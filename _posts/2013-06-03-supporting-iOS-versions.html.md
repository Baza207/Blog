---
title: Supporting iOS Versions
date: 2013-06-03
tags:
- Apple
- iOS
- Objective-C
- WWDC
---

Lately there's been a lot of talk with backwards compatibility, both in my work and in the press due to the new gen consoles we've seen. At work most people and clients go for iOS 5 being the minimum iOS version to support these days. This seems natural with the speed people seem to be moving over to the latest versions of operating systems due to them being delivered over the air, and in he case of iOS, being free. However in my own personal projects I have always tried to support the oldest version I can, that being iOS 4.3 (as of writing this post). Though lately, working on new versions of some of my apps I've gone for iOS 5 as a minimum.

Apple releases a new version of iOS pretty much annually. This means once a year I get a bunch of new features to play with and hope that none of the updates don't break any of my apps (which thankfully hasn't happened yet, touch wood). When I look at previous updates for iOS from a developers point of view the last major things were added in 4.3. Since then we've got some amazingly useful new features but they've very much been improvements on the previous method of doing things (I'm sure I might be called out on this but infant see anything that changed what I do that is "new"). I think the biggest thing I noticed over the last few years was in iOS 6, when the core methods of how UI rotation is handled was changed. And that was still an enhancement again of a previous feature.

<!-- READMORE -->

At the time I was working on a video recording app and it really messed with me. Where before I had 1 method that was called when the device and UI was rotated, now I had 3 or 4 and had to check the orientation myself every time. This doesn't sound like a bit thing, but it threw me off and from a lot of the questions online at the time I wasn't the only one.

But anyway, I digress. You support older versions to allow people who have older phones that can't run the latest version of iOS to run you app still. Plain and simple. However, Apple have got very good at making their new versions of iOS run on as many previous devices as possible. Take the iPhone 3GS for example. This is a phone that in June this year is 4 years old, ancient in smart phone terms, shipped with iOS 3 (still actually called the "iPhone OS" at that point, pre iPad), this phone runs the latest version of iOS 6.1.3! That's crazy when you think about how different it is in specs to the iPhone 5 and even that is 7 months old now.

So why should you support all the way back to iOS 4? Especially as we have WWDC just around the corner where we know we're hearing about the new iOS and OS X versions thanks to Tim Cook at D11. Well I think it comes down to personal choice and the app you're making. If you want to make an app that requires NewsStand, iCloud syncing, AirPlay mirroring or PassBook the obviously you need to be minimum of iOS 5 or 6 respectively. Or if you don't want to have to support 2 ways of presenting view controllers modally, then go for iOS 5. But if you don't have any of these limitations or cares, then go or it! Just, for the love if god test it on all supported versions. That's the hard bit these days as Xcode no longer has simulator support for iOS 4. But always test you apps, please!
