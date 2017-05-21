---
layout: post
title: PP2 March/April Update
author: James Barrow
date: 2013-04-17
tags:
- Pixel Pals
- iOS
---

Pixel Pals 2 is making progress, slowly but surely. I've finished the basic backend now and have been tweaking it as I add the other content, new functions and generally play with the game. I've recreated the basic UI and started importing features, such as the mini games (the coolest part of the current version in my opinion). It's made me realise how bad my current code is in v1.x. It's not wrong but it's just formatted and written in such a novice way, which isn't hard to understand as I'd only been making iOS Apps for a couple of months, self-taught when I wrote it and had only been programming in Obj-C for the same amount of time. It's actually really nice to see how far I've come and how much better and efficient I am now. For example I believe the size of the Find and Seek mini game class is now a 3rd smaller after optimising it.

<!-- READMORE -->

I had a long think about UI when working on it last week. "Should I change the UI?" was the question I kept asking myself, and I finally came to the conclusion, "If it ain't broke, don't fix it". I still really like the button bars I originally created and they can still hold all the buttons I need to put on them. However the thing I wanted to improve is customisation ability of the entire UI. The current version is just a load of images, so each colour, style, and resolution has to have it's own image. In an app that supports iPhone, iPad and the retina screen on both device types this makes the app get large very quickly. So I had the idea of being able to draw the graphics in-app with something called Core Graphics. Basically this is like using Illustrator and vectors instead of Photoshop and bitmaps. Below is a screen shot of my proof of concept, which I made to prove to myself it can be done.

<img alt="PP CoreGraphics Proof" src="/assets/pixel-pals/PP-CoreGraphics-Proof.png" width="286" height="464"/>

The colours are a bit off (thank you rubbish TV being used as a monitor), there is no gradient shading and it's amazingly basic but it works! The benefits of this is, as I said, I don't need images for each resolution and colour so the app will be a lot smaller in size, but also theoretically the UI can be any colour the user wants. Full marks for customisation! I am still to add a colour pallet to allow the user to change the colour of the UI, but it's on the list, long list, of things to do.

Between adding the navigation at the beginning of last week and adding the mini games this week I rewrote my sprite and animation classes. They are now make more sense for use in PP2 but also allow a lot more expansion in the future. It still needs a few more tweaks, but I'm going to leave that until I have a few more creature graphics done to be able to decide how I'm going to format my sprite sheets. Though that's another post, and you might even see some mock ups of the new creatures.

Next step is to finalise the mini games (i.e. finish adding Bounce) and add the creature creation screens. I'm going to be using a custom view animation I made for scroll views here. I've already used it for the creature information view and plan to use it a lot more because it looks so cool! Until I get the app finished a bit more I don't want to make any videos of it so here's a video of this scrolling on my YouTube channel. It's simplistic, but you get the idea. <a href="http://youtu.be/2nxQCaKhPmw" target="_blank">LHECarousel</a>
