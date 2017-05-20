---
layout: post
title: Little Hedgehog Server
author: James Barrow
date: 2013-06-07
tags:
- coming-soon
- github
- lhs
- little-hedgehog-server
- open-source
- pig-on-a-hill
- puck
- py
- python
- server
- twisted
image: lh-logo.png
---

When I stared work on Puck (my iOS app for results, scores and information on Elitserien Ice Hockey, <a title="Puck iTunes Link" href="https://itunes.apple.com/gb/app/ios/id571254467" target="_blank">check it out on iTunes here!</a> and the reason I got my lovely <a title="Linode Link" href="https://www.linode.com/?r=398f3b1ce56e745028c920f81e56d1cbb13f57bf" target="_blank">Linode VPS</a>) I made a backend to be able to compile all of the data into JSON files and then read them into the app. I started looking into several languages for this, PHP and Ruby both being strong contenders, but as it is with most things, you normally go for something that your friends and colleagues are using. This is for the most part because you know you have people to ask for help when things go wrong or you don't understand a feature, but probably also because you end up hearing more about it.

The language in this case was Python and after going through the tutorials on <a title="Codecademy Link" href="http://www.codecademy.com" target="_blank">Codecademy</a> in a day I started making my backend. This continued to be my main and only real source of use of Python for a long time. Even though it did span out into a lot of topics, because Puck now has push notifications and so the backend has notification and database support now, all done with Python, apart from one page of PHP for dealing with device tokens.

About a month ago I decided I wanted to start looking into making myself a multiplayer server. I've been picking a few similar topics lately in an attempt to increase my knowledge in different areas and start creating the building blocks to make my own game engine/framework, or at least a group of frameworks that I can use in future games I develop.

<!-- READMORE -->

So here was a really good project to hone my Python skills on as it would need to include things like sockets and constantly running server programs. So as always I did an initial Google search and found some very useful tutorials such as one on the <a title="Ray Wenderlich Link" href="http://www.raywenderlich.com/3932/how-to-create-a-socket-based-iphone-app-and-server" target="_blank">Ray Wenderlich</a> site which used the Twisted framework for dealing with sockets and clients. This seemed a nice way of doing it, so I started having a play around.

I got the basic system up and running pretty quickly and then stopped. I could see this running away with its self quite quickly and I wanted to try to make myself a plan. The first goal was to make a basic chat server. This, in my opinion, is needed in any multiplayer server but it will create a good base to work out how to implement other areas. The main idea for the project from the start was to make it modular. This idea started when I was looking into how to authenticate clients. The way I was doing it was simply storing users information in a database, which was fine for testing. However to make this as adaptable as possible for the future it was going to need to handle authentication from lots of different services, such as Facebook, Twitter, Tumbler, Game Center and so on and so forth as well as custom databases. So I came up with the following plan.

<div style="text-align: center;">LHS Base Code</div>
<div style="text-align: center;">|</div>
<div style="text-align: center;">Authentication Module</div>
<div style="text-align: center;">/|\</div>
<div style="text-align: center;">Facebook    Twitter    Tumbler    Game Center    Database    Etc...</div>

This basic plan means that if and when a new way of authentication arrives and needs to be added, you can simply link it to the authentication module and not have to worry about how it deals with each client. The authentication module will always talk to the client in the same way, and in this way it should even make major version updates easier to handle.

There may even be an argument for putting another "module handler" module between the LHS Base code and the other modules (in this case the authentication module), which would allow easy addition of modules for other functions such as voice chat or game data handling to be added with the same level of ease as adding a new authentication type to the authentication module.

The project is still in the early stages, but due to a friend really wanting to get their hands on the code and play around with it, I've uploaded it to GitHub and made it open source. It's something I can see having a lot of potential and really want to get going from now on. Oh and it's called Little Hedgehog Server. Why? I don't really know but it makes me smile and that's enough for me.

If you'd like to contribute towards LHS you can find it on <a title="LHServer GitHub Link" href="https://github.com/Baza207/LHServer" target="_blank">GitHub HERE!</a> Please feel free to massage me about any function or future function you have a question about.
