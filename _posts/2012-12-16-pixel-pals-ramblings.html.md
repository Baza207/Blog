---
layout: post
title: Pixel Pals Ramblings
date: 2012-12-16
tags:
- apps
- coming-soon
- ios
- pig-on-a-hill
- pixel-pals
- v2-0
image: pixel-pals-logo.png
---

**PRE-POST NOTE:** The following will be a rambling of my thoughts and plans for the new version of Pixel Pals. I have been having some problems of late trying to workout certain features of the new version because I can't get them out of my head. This is an attempt to do that. Not all the things I talk about in this post will make it to the final release, likewise some things I say will not be in the app, may still be. Confused? Well have fun reading the rest of this and seeing a, sometimes scary, glimpse into my thoughts.

### General Idea

The general idea for Pixel Pals v2.0 is to fix the fundamental problems with the current version and so make it in a "nicer" way. The original version was made over 9 months while I was learning how to code. So it's a complete mess! It's structured wrong (if can call it structured at all) and nearly impossible to add new features to. So the plan for v2.0 is to fix these main to points.

<!-- READMORE -->

### Navigation and Style

I still really like the general navigation in the app, however I think it can be streamlined a little bit more. I really like the idea of gestures but how I would implement them, I'm not entirely sure. Possibly gestures are more for interacting with your creature than navigating around the app itself. The base of the views themselves though will have to be redone. I want the user to have way more control of the style of the app, to allow the user to personalise it to themselves. The main decision here is to have the cases in the app as graphics (PNG files) or to make the app draw them itself. The first option is easiest but will mean the app will be bigger and give less options to the user. The second option is my preferred one, it'll make the app smaller and allow way more customisation from the user. However it is a lot harder to code. I need to look more into Quartz and CoreAnimation for this.

### Game Modes

The biggest complaint with the game at the moment is that peoples creatures die too fast. I was trying to make it like the original but I still think I might have made it a little too needy. So for v2.0 there are going to be two modes, Casual and Classic. Classic is going to be pretty much the same as the current easy mode, so you creature will get hungry and unhappy over time and if left too hungry or unhappy, it will die. The casual mode will be, I think the mode most people will choose. your creature will not die from neglect it will just start refusing to do things until it is fed or played with again. The big bit for this is to not corner myself with the following:

- When the creature is unhappy, it will not eat but only want to be played with,
- When the creature is hungry it will not want to be played with but only fed.

As might be obvious, there is a flaw with just these two rules. If you leave you creature for a long period of time and it is really hungry and really unhappy, it would not allow you to do anything. It would be doomed to eternity of hungry sadness, and thats just not nice. So the trick will be to always allow one to take precedence over the other. Other aspects to this might be, if the creature gets it, it wont want to eat or play until it's healed. I wonder if digital pets can get bored as well...? As the casual mode wont be able to die, the age scores will not be uploaded to Game Center in this case, so I was thinking (just this second) of adding something like XP that could be used instead. How this is earned and how this is uploaded to the leader boards I currently don't know, but it's something to think about.

### Death

Death is a tricky one. On classic mode it's fine, I've already done that with v1.x, when the creature is neglected for a long period of time, it dies. However in casual mode there isn't the possibility of death so how long should it live for? Should it die at all? Should the player get the option to retire there creature when they want to start a new one? Is this when XP scores are uploaded to the leader boards? I would like to point out here that I do mean retire, NOT put down. Little bit overly morbid thoughts there. This has to be treated tactfully and another thing that will need a bit more thinking.

### Creatures and Animations

So there will be the 3 current creatures (Rex the Dino, Pete the Penguin and Ben the Bunny) in v2.0 but there will also be an extra 6! I'm planning to spilt these up into 3 categories of 2, Sci-Fi (Robot and Alien), Fantasy (Fairy and Gnome) and Animals (Hedgehog and ?Something...). As I said before I want to make the game easy to add on things as possible, so the amount of creatures my increase with future, future versions.

I also wanted to add a bit here about how much work goes into making these creatures because I don't really think people realise how much work it really is. So ignoring the designing phase of it all there will be 9 creatures, each creature has 4 evolution stages so thats basically 36 creatures. Each creature currently has a few animations, walk, eat, happy, sad, jump. These animations are between 2-4 frames so I have to create a minimum of 72, max 144 separate images for all of the creatures. I'm also looking to add some more emotions and so animations to make everything just that little bit more immersive. I'm currently thinking of some different jump animations (surprise, etc), boredom, dancing, and possibly some idle animations. So thats a minimum of another 4 animations cycles, so were looking at up to a minimum of 144 images or maximum of 288!

It all looks so awesome when its done though. 😄

### Mini-Games

There are 2 mini-games in the current version and 'Doink' has been "Coming Soon!" for ever, so Doink will be part of v2.0 as well as 3 extra mini-games. However, I have no idea what these will be at the moment though. I'm going to have to look through some of my old notebooks and see if I came up with any good ideas that I've forgotten about. If anybody has any suggestions, please let me know in the comments or email me at: <a title="james@pigonahill.com" href="mailto:james@pigonahill.com">james@pigonahill.com</a>

### In-App Purchases

I didn't know if I really wanted to write or even think about this right now but I thought I really should. I am thinking of adding in-app purchases into Pixel Pals v2.0. I am currently working out how exactly it's going to be in there but let me clear a few basic things up. In-app purchases will never help a player get further than another player in the game. I have always hated this way of doing it as it is just unfair. Also you will not be stopped through the life cycle of the game unless you pay for a certain item. I understand why people put this into there games but I hate it. It is the main reason I have stopped playing so many games because I didn't want to pay and so the game got boring, because I couldn't do anything more! The way I am looking to implement it is buying new styles to customise you creatures case, extra creature packs and extra games/game packs. I was also thinking of making some sort of credit system so that if you use the app a lot you can use you earned credit to purchase things or if your lazy you can by coins/credit to get those items quicker. Just a thought.

### Final Thoughts

So a very long post there but I hope it clears up some questions people have been having though this has hardly scratched the surface. I haven't talked about 'Little Hedgehog Engine', creature interaction and reaction, day night cycles, backend rebuild, the arena or the sound and music! That might have to be talked about as I make it and update you all on whats going on.

If anybody has any questions please comment down below or email me at: <james@pigonahill.com>. The only thing I can not answer is when Pixel Pals v2.0 will be ready. It is still very early day in development and I have lots to do (as you might have gathered). It is just me working here on this and I have other work (that pays the bills) to do as well. So please be patient with me and I will try and keep you updated with progress reports, and when I have an idea of how long it will be until the end, I'll let you all know. 😄

So good night, I'm off to code some more until the wee hours of the morning.
