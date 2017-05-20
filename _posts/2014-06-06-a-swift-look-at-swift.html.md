---
layout: post
title: A swift look at Swift
author: James Barrow
date: 2014-06-06
tags:
- apple
- ios
- mac-os-x
- osx
- swift
- tutorial
- wwdc
image: swift-logo.jpg
---

On Monday of this week Apple introduced the world to Swift. The new programming language to, _eventually_, replace Objective-C. There's a lot of major improvements that Swift brings and I will never be able to go through everything, but I'm going to try to go though the "main" points or just as much, the points that excite me the most. If there's anything that I've missed that you won't to hear about, post it in the comments and I'll try to look into it.

Swift has made me very excited. It's the most excited I've got about coding since I first started learning Obj-C. It's a language that seems to make an awful lot of sense when you look though it. It is a language that in its simplest form can be very easy to learn. However it can be harder for beginners to coding when you get to some of the more advanced topics, a lot sooner than, say, Obj-C would.

With that in mind, the majority of what I'm going to write about will assume that you have some previous coding knowledge, mainly in Obj-C. If you're a complete beginner, some guides for you will be coming out by someone (I might try some myself) when Swift comes out properly later this year.

READMORE

I said Swift will _eventually_ replace Objective-C. This is **not** something that is going to happen overnight. Far from it. Apple has even said in their WWDC sessions that they are not expecting Swift to be an instant replacement to Obj-C, nor should it be thought of in that way. So you don't have to worry about re-writing all of your Obj-C apps, they'll continue to work just as they always have. What Apple has done those is given us as developers the tools to easily use Swift and Obj-C classes and frameworks seamlessly together, with little or no hassle.

So what do you need to know when your writing stuff in Swift? Well first of all Apple has spent a lot of time and effort being able to switch between Obj-C and Swift amazingly easily. So much so that when you're working in a Swift file and you lookup a class or element from Obj-C if converts the header into Swift so you don't have to translate it yourself in your head. Obviously it works the opposite way as well and is a great tool to be able to sink yourself into the new language instantly with very little constraints.

This is not to say you can convert you code from Obj-C, this is just to say you can see what your declarations would look like in Swift, allowing you to lookup method calls or variables just like you would if you were looking them up in an Obj-C header file. If you want to look into this particular feature in more detail, check out session 407 - Swift Interoperability in Depth in the WWDC 2014 videos.

As everyone is a 4 day old Swift programmer I am bound to make a few mistakes here and there, so please forgive me if you spot any of these. I will make edits as I go if they are required.

I've split this post up into a series of post as after writing about my first point, I've already filled up 1 posts worth already. Below I have listed the areas I'll go into and I will add links to the relevant posts as and when I write them.

- [The Basics](/2014/swift-the-basics/)
- [Optionals and nil](/2014/swift-optionals-and-nil/)
- Functions and Closures
- Extensions
- Enumerations
- Generics

It's the little bits that make the difference

For any of the sessions from WWDC 2014 find them at: <a herf="https://developer.apple.com/videos/wwdc/2014/" target="_blank">developer.apple.com/videos/wwdc/2014/</a>

Also check out the excellent book that Apple released that goes though the Swift language in a lot of detail: <a herf="https://itunes.apple.com/se/book/swift-programming-language/id881256329?l=en&amp;mt=11 target="_blank">Swift Programming Language</a>
