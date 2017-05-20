---
layout: post
title: Game Engines and Polycode
author: James Barrow
date: 2013-05-31
tags:
- c
- cpp
- coming-soon
- frameworks
- game-engines
- lua
- lua
- polycode
image: polycode-logo.png
---

Over the last however number of months, a friend of mine has been learning and playing around with OpenGL. Ever so often I will receive a .app file with new functionality each time. It started with a red and a blue cube hovering over a green plane with no lighting, shadows or anything, to basic lighting, dynamic lighting with an old Lara Croft model loaded in (I mean what would you use?), basic textures and so on. The latest version I've seen, via screen shots, included full textures on the Lara model, the buildings in the background, road, paths and everything else. Of course, as with everything in programming it was still a work in progress (and I may have over hyped that a bit) but the distance he's come from those 2 cubes hovering over a flat plane was amazing! I might have got a little jealous, but I know I just don't have time to be learning something so core like OpenGL from the ground up at the moment. What with work and my own projects, my brain would just explode. So I wen't looking around for a nice game engine to use and play with.

The first things you find of course are the big boys such as <a title="Unity3D" href="http://unity3d.com" target="_blank">Unity3D</a> and the <a title="Unreal Engine" href="http://www.unrealengine.com/en/udk/" target="_blank">Unreal Engine (UDK)</a> which are very popular and nice engines, but they just felt a little much. I've been getting into the indie game industry a lot more lately (which I'll go into in another post if I haven't already) and a lot of people seem to make there own engines. It's again something that I've wanted to do for a long time though I know, right now, I just don't have the knowledge to do it on my own and of course theres the time thing again as I mentioned before. So I kept looking around and the more I looked I found lots of different things.

<!-- READMORE -->

C++ is always the language that I have had in my mind as THE language to write games in if you're serious about it. I know this is far from the truth (Minecraft is written in Java for example) though when you read posts and see people asking questions on sites like <a title="Stack Overflow" href="http://stackoverflow.com" target="_blank">Stack Overflow</a> and <a title="Game Dev" href="http://gamedev.stackexchange.com" target="_blank">Game Dev</a> it always seems to come back to C++. I seem to be going through a phase where I'm learning a new programming language every 2-3 months, so I thought it was about time I started on a new one. I have played around with C++ before when I looked into <a title="Box2D" href="http://box2d.org" target="_blank">Box2D</a>, a 2D physics engine that I found through Cocos2D last year. I then stared looking into Lua, as it seemed to be a nice, concise language that came up, when talking about C++ and game dev, and which seems to be used a lot for game AI, which I've always been interested to play around with.

Finally I found this post on Stack Overflow:
<a title="Stack Overflow Question" href="http://stackoverflow.com/questions/5053134/what-is-a-good-game-engine-that-uses-lua" target="_blank">http://stackoverflow.com/questions/5053134/what-is-a-good-game-engine-that-uses-lua</a>
This had a lot of links on it and I looked quickly through a few until I clicked on <a title="Polycode" href="http://polycode.org" target="_blank">Polycode</a>. Now this made me sit up in my chair. I read though all of their site (which is rare for me, I normally just skim) and then moved onto the <a title="Polycode GitHub" href="https://github.com/ivansafrin/Polycode" target="_blank">GitHub</a> site.

Polycode, I've found out, is a project that has been developed over the last 6 years or so by Ivan Safrin. From what I've read on forums and the Polycode site he uses it for work and his own personal projects and that is how it grew initially. These days it gets daily pull requests on GitHub and is under constant improvement by Ivan and the community.

The initial thing I liked with it was the range of things it is able to do! Just to name a few; you can build 2D and/or 3D games, it has "1 click publishing" for Windows, Mac and Linux, 2D and 3D particles systems, OpenAL for sound (3D sound which I love and can't wait to play with), 2D and 3D physics, networking, input handling (including gamepad/joystick), font rendering, sprite sheets for 2D animating, mesh and skeletons for 3D animating... the list just keeps going!

Now there's a lot there but the cross platform support, instant win in my books. If you're making a game or any program, you have to be able to let everyone who wants to play or use it the ability to. I know from being a Mac user, the amount of games I've seen, got really excited about and then realised they are only for windows really sucks, so, I love this feature. Then you can write everything in C++ using Polycode as a library or in Lua using the IDE that is included in the git repository (the IDE includes a debugger which I hear is quite rare for Lua as well).

So I'm sold! Do I have to pay anything? Nope, it's all open source and you just have to close the git. Away I went, reading through the build file to get everything up and running, and bleah! Let us say I ran into a few problems. There's a few things that the instructions skirt over and being a little bit of a novice using the terminal got me a little muddled. However with the help of a terminal whizz friend I managed to get it all built, including the IDE and was up until around 3.30AM playing with the sample projects. I'm going to write another blog post for instructions on how I got Polycode to build and run properly soon, but during the of building me and my friend did a little more research into why this was such a pain to build.

Polycode is currently on version 0.8.2 which means it's pre-release. Quoting Ivan on the Polycode forums <a title="Polycode forum quote" href="http://polycode.org/forum/viewtopic.php?p=1443&amp;sid=4398b1c413c573c616335194b1d2a496#p1443" target="_blank">"There is a reason why there hasn't been a public binary release yet: there are still a lot of bugs." (click to see the full post)</a>. He goes on to say that by releasing binaries means that that would be the version that some people would see first and base their first impressions off of, so he's decided to wait. After reading that, I completely understand. In his eyes, this project is not ready for "release". Yes it's available to the public, but that's just as much to make it that much better for the time when it does become ready for release and that 1.0 status.

I'm sure I will be posting more about Polycode in the future as it grows with more features and onto more platforms (in the pipeline are a 3D modelling editor for the IDE, iOS and Android support and beyond) and I just can't wait to see what I and others can do with it and what it becomes. As soon as the initial build problems are fixed I can see this becoming an even greater framework than it already is, and it's already seems pretty damn good. So thank you Ivan and everyone who has contributed to Polycode so far and please keep up the good work!

The Polycode site can be found at: <a title="Polycode Site" href="http://polycode.org" target="_blank">polycode.org</a> and can be downloaded form the GitHub site here: <a title="Polycode GitHub" href="https://github.com/ivansafrin/Polycode" target="_blank">github.com/ivansafrin/Polycode</a>
