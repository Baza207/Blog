---
layout: post
title: WatchKit and watchOS 1 Apps
author: James Barrow
date: 2015-08-10
tags:
- watchOS
- WatchKit
- Apple Watch
published: true
image: watchkit-logo.png
---

So over the last few weeks I’ve been on a bit of holiday. Some time away from work is always nice, some time to relax, and yet, I continue coding. 😛

However, I finally got myself an Apple Watch, as I managed to get my hands on one when I was over in the UK (I wanted to see what the colours really looked like) and they also came out in Sweden. So obviously I’ve been trying to make watch apps for my apps, namely Puck and Dog Bins. I thought it might be useful to post some of my findings from playing around with WatchKit in watchOS 1.

READMORE

### Only send what you need
You want to limit the amount of data you are handling in your watch extension, either from the main app or from the internet. You don’t want to be sending an array or objects (probably dictionaries) full of key-values that the watch will never need or use.

What I did in these cases was, with my custom objects create a `simple() -> [String: AnyObject]` function. This would return a dictionary with just the basic key-values I wanted. You could even go further on that to have a `simple(keys: [String]) -> [String: AnyObject]` function. This would allow you to specify the keys you wanted from the custom object. Then you’d simply loop though the passed in keys and return the key-values in a dictionary.

This is a good practice at the moment, as both the extension and main app are running on the same device. However, when we get watchOS 2 later this year, the watch extension will be running on the watch and so this becomes even more important.

### Do NOT use openParentApplication(_:reply:) for network operations
This is exactly how I started using `openParentApplication(_:reply:)` but I soon realised this was adding extra steps that were causing issues. `openParentApplication(_:reply:)` is a synchronous call. This means that by the end of the function, you have to call the `reply()` callback, and if you don’t the the OS will complain at you. So if you kicked off an asynchronous task (which they should pretty much always be) you would get to the end of `openParentApplication(_:reply:)` and probably call `reply()` before you ever get any data back from your request.

This was the source of many issues I was having. I knew why it was doing it, but I couldn’t find a way around it. I even started playing with `dispatch_semaphore` etc before I realised, this thing that should be simple, I was making very complicated.

**Note:** Ok, so sometimes you do need to hand off network request to the main app, but my point is, do it very sparingly. 

Watch extension -> Internet -> watch extension  
is always going to be better than  
Watch extension -> main app -> internet -> main app -> watch extension.

### Run network request in the Watch extension
Why not? You can even think of your watch extension as being a completely different app, in fact, you *should* think of it that way. It can still share the same code with you main iOS app with Frameworks obviously. And this is actually what they were introduced to do with iOS 8 and extensions (today, action, share, keyboard, etc). But again, this is another point that will become more obvious when you start to think about watchOS 2, as then your watch extension will be running on the watch itself. Give it it’s independence, let it explore the world on it’s own.

In fact, I managed to make the Puck 3 watch extension run completely independently from the main app if it had to. The only limitation is watch OS 1, but when watch OS 2 comes out and the extension is run on the watch, the phone could probably be off and it’d still work (on wifi only of course 😉).

### So when should I use openParentApplication(_:reply:)?
In watch OS 1, very little, though there will be some instances when you need it. Getting a users location, getting locally saved data or transferring a locally saved image/file are probably the only reasons in watch OS 1 you’d need to use it. (watchOS 2 is a different matter, but we’ve got a whole framework to help us out there. Thank you Watch Connectivity.)

### Share as much data as possible
What I’m referring to here is shared containers. In Puck 3 I am using Core Data in the main iOS app, however the watch extension just uses the basic raw JSON from my server. I even use the same code in my framework called by both apps. However the main iOS app calls 2 functions, the watch extension just calls 1.

What I’ve done is made a function called `updateData(complete:)` which will get the JSON from my server, saves it to the shared container and also returns it in the `complete()` callback. This is what the watch extension uses.

The second called `updateDataForCoreData(complete:)` will first call `updateData(complete:)`,  but then it will parse the data it has received into Core Data. This, as you might have guessed is what the main iOS app uses.

Apart from reusing code and not having duplicates, this allows me to make sure that the data saved into the shared container is always up to date. It doesn’t matter it the request was made from the watch extension or main iOS app, `updateData(complete:)` is always called, and so the JSON response is always saved to the shared container.

I even went a little further, going along with what I previously said about “only send what you need”. I only save certain sections to the shared container, as that is all that the watch extension needs. For example fixtures are not shown in the watch app, so there’s no point to save the raw JSON for 360+ games if I’m already saving them to Core Data for the only thing using them.

### The error `The UIApplicationDelegate in the iPhone App never called reply() in -[UIApplicationDelegate application:handleWatchKitExtensionRequest:reply:]` doesn’t always mean what it says.
I noticed there was a few times that I would call `reply()` in `openParentApplication(_:reply:)`, but I would still get this error. It seems that this is the *generic* error that we get given for watch extensions, and sadly, it’s all the feedback we get.

An example is that you can only return certain native classes in the `reply()` dictionary, NSData, NSString, NSNumber, NSDate, NSArray and NSDictionary. So if you reply with another object, or custom object, it will fail.

The error is not correct, but `reply()` never gets called, not because you didn’t call it, but because the iOS can’t parse the dictionary to send, and so crashes, so the watch extension complains it never receives a response.

### Test on a physical device
Now this is probably the most annoying though hopefully the most obvious point. Anyone who has been making iOS apps for a while knows that however nice the simulator can be, it also does perform very differently at times to actual hardware. This is even more the case with watch apps on watchOS 1.

Seeing as all we got with watchOS 1 was basically a second screen for the iPhone simulator (hell it’s even in the same menu are AirPlay to an AppleTV) there are some things that just aren’t the same. I found a few times that stating certain processes in my watch extension when the main app was never open on the physical device gave some stage results, something that you can’t reproduce with the simulator. There’s even features you just can’t test properly, like had off, at all in the simulator.

### Conclusion
So those are just some of the things I’ve run into while making watch apps in the last week or so. There are parts of this post of course that will become redundant when watchOS 2 comes out later this year. But there are also some ideas that can be used with the new APIs we’re getting, even if we don’t use `openParentApplication(_:reply:)` anymore.