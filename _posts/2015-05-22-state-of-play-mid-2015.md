---
layout: post
title: State of Play, Mid 2015
author: James Barrow
date: 2015-05-22
tags:
- pixel pals
- colour cubes
- dog bins
- puck
- update
image: poah-logo.png
---

So I’ve been quiet for a little while about my own apps. I keep getting back to them every now and again, but the main thing is that simply, I just haven’t had the time. Let’s face it, none of my apps are "big" apps. They don't make me any money that I could live off of, maybe enough for my developer licence and a beer.

Though that doesn't matter to me. I don't make my apps to make loads of money (however that wouldn't be something I'd be against 😉). I make my apps to satisfy needed I have that I can't find some other existing app to fill that need, and mainly, I make my apps to learn new things. Going though my current apps on the store:

- Pixel Pals was made for my dissertation at University.
- Colour Cubes was made in about a week after seeing a very basic version of a similar game on my mates BlackBerry, and I wanted to see if I could remake it myself.
- Dog Bins was made when my step-mum suggested it would be a good idea for the app, and I took it as a change to learn how to make an app with cloud feature, so I made it using <a href="http://parse.com" target="_blank">Parse</a> for the backend.
- Puck was made because when I moved to Sweden, I got into Ice Hockey, and I wasn't amazingly impressed by the apps available at the time, so I made my own. It also gave me the chance to learn Python and setup my server, along with push notifications and all that fun stuff.

<!-- READMORE -->

Every app I've made, I've learnt something new on, and that's sort of a conscious decision. So even if the app doesn't make any money, I know I've learned something, something that will helpfully help one day when I make that app that might do well. You never know. I've made quite a few little apps when I've been learning new tech (UIDocument, CoreData, CoreLocation, Beacons, Sockets, etc) that will never see the light of day, but have been fundamental in things that have happened after them.

But that's getting away from wanted I want to say here. I'm going to quickly run though each of my apps in the app store with a quick description of where they are and what I see happening with them in the future. I'm not going to say when anything will be done, because honestly, I have no idea when I'll find the time do do any of what I want to do, but hopefully, one day. 😄

If you want to jump to any particular app that you're interested in, I've added some quick links below. Otherwise, just read away.

- [Pixel Pals](#pixel-pals)
- [Colour Cubes](#colour-cubes)
- [Dog Bins](#dog-bins)
- [Puck](#puck)

##Pixel Pals
Pixel Pals is still the app that sells, consistently. Not a lot, but there's always at least 1/2 sales a week, which always makes me happy. Especially as it's an app that hasn't gotten a proper update since the end of Match 2012[^1]. I have loads of plans for PP, the issue is time, though mainly logic.

The logic for the original game was, how can I say this... poor. It was my first ever app, and it was a crazy app for my first one. Kid's make your first apps simple. DO NOT try and make something like Pixel Pals. I learnt a lot, and in quite a small space of time, but with any code that's more than 8 months older, or more, it makes me want to cry when I look at how I did some things. So one of the fundamental features in a 2.0 version is to re-do the underlying logic.

The original version had issues with this, you could change the time zone and your creature would die, you could put your creature to sleep, close the app, and he would just sleep indefinitely, some weird sleeping beauty scenario and so on. There were some funny ones, that were planned, but sort of worked, for example if you feed your pet continuously (as there was no logic for your pet to tell you it was full, it'd just keep eating and eating) the next time it would goto the loo, it would... go to the **loo**. A screen full of poo.

However annoying or funny these were, the base issue was the fact the app can be closed. This is not an issue the original physical toys ever had. They'd always be on, always be ticking though the game loop, no worries. But an iOS app, users can close it, it can be closed by the operating system, lots of things could happen that disrupt this, so I started going about solving this... then I got in a muddle and haven't touched it in about a year and a half.

One day I will get my head around it, one day I will not be thinking about a million other things to be able to get my head around it, and one day, I'll probably get a few of my friends to double check my logic, just to make sure I've not completely messed it up. But for now it stays on the list of apps I _really_ want to update, but just need to find the time and motivation to do so.

Any feature I've previously talked about for PP 2.0 are still completely on the table. More pets, more mini games, etc, just maybe with a few tweaks after 2+ years thinking about it in the back of my mind.

##Colour Cubes
Colour Cubes was always a fun little thing I did to test myself, that ended up becoming something I released. If you look at it now, it looks like pants. Though, the logic is pretty solid. I've been thinking lately about seeing if I can clean it up, revamp the whole design to something much cleaner, and maybe add a few features.

I had, a little while ago, an idea of how to make CC multiplayer, something I'm still interesting at coming back to. I've have a good few pages in a notebook from a year or so back that lays out how it could be done, logic wise, in some detail. Again, this being quite an old project now, its really needs a re-write (probably in Swift as well) but I feel it has the possibility of having something done to it at some point.

There is another thing with CC, because it's based on what is basically a square of squares, it's made me very interested to see if I could make it work on the Apple Watch. Obviously the higher levels of difficulty wouldn't work as the hit boxes for each cube would be too small, but maybe. Either way I think I'm going to wait on that particular point until, at least, after WWDC 2015. Let's see what more we get, as developers, for the Apple Watch this year, then we'll see.

##Dog Bins
Dog Bins was my first foray into working with a cloud based backend system. I learned a lot that I now take for granted from it, async processes probably being a big one. However, after the last big update, it fell prey to my lack of time. There's enhancements I want to make to it, fixes that are needed and other things that could be improved... but time.

Dog Bins out of all my apps falls into it's own category of being a free app. It has ads in it yes, and in app purchase to remove those ads, however, they make nothing. It has a decent user base, and the community has nearly logged 300 dog bins, which is awesome. However in the last year it has had 200 installs, though iAds have made $0.70 and in app purchases came to $0.71. That's after Apple takes there stuff but before any tax. In short terms, it's nothing, and sadly that's something that bumps it down the list of priorities.

##Puck
Puck was the app where I learned how to code in Python on a server (along with setting up and maintaining that server, to a degree) and dealing with push notifications. I was my test case when Swift came out last year at WWDC 2014 to dive into Apple's new programming language. And that was also what made it instantly clear, that Swift was not ready when it was released to remake a whole app in it. Now however with Swift 1.2, I feel like it is and so I've gone back to what I started on with re-writing Puck in Swift all those months ago.

However, because of the nature of how much Swift has changed, and with how much I've learned since then on how you should do things in Swift compared to Obj-C, it needs to be pretty much scrapped and started again.

Puck has the extra component of being a 2 sided application, as it also has the backend that needs constant updating and maintenance as well. With the latest version of Puck, I've started looking into redoing my backend for the 3rd time, as, like with 2.0 last year, I've started going though the app and wanting to add this or that, and realised my backend data isn't optimised to do those tasks. This of course makes the process longer, but I hope, in the long run makes the whole application and service that much better.

Again, Puck is another perfect candidate for an Apple Watch application, more so than Colour Cubes, as what we have in WatchKit is more than enough for what I need for Puck, but without that new main app backing it up, it has to wait.

I do feel Puck is the app that I expect an update being released for soonest, and I do now have the summer break before the new season begins to get this done in. But we will have to see. Like in all of my apps, I have lots ideas I want to add or improve on existing features, it's just finding the time to do so.

##So to sum up...
Time, time, time... I think that pretty much sums it up. I've got lot of ideas, and even though 4 apps doesn't sound a lot, when there's just one of you, 4 apps becomes a lot to go though. You can say that I've kind of shot myself in the foot by leaving some of them for a while, and so making the workload more, but sadly that's just the way it is.

As always, if I have any more updates as time goes on, I will try and post them here, but I hope this answers any questions, even though it might not answer them in the way you wanted.

[^1]: I don't count the update in October 2013, as it was really just a fix for an issue that arose with iOS 7.