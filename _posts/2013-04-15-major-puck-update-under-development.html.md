---
layout: post
title: Major Puck update under development
author: James Barrow
date: 2013-04-15
tags:
- apps
- coming-soon
- hockey
- ice-hockey
- ios
- ishockey
- pig-on-a-hill
- puck
image: puck-2-logo.png
---

We're nearing the end of the Elitserian season and the first season for Puck. It's been a great time and I've learnt a lot, especially server stuff. So what do we do now? Well the obvious thing is, make it all even better! So I'm currently working on a major update to Puck which includes big UI and backend updates.

I have been planning to add more Hockey Leagues into the app for a while now and doing so would have meant a crowded experience with the current UI. So I decided to get rid of the tab bar and use a sidebar, similar to the current Facebook and Wunderlist apps use. This allows more space to add features and leagues for the user to choose while having the added bonus of freeing up the screen where the tab bar used to be. Here's a sneak peek of how it's looking at the moment. Please remember this is a work in progress and it currently has no updated graphics.

<!-- READMORE -->

<img src="/images/puck/Puck-New-UI-3.png" width="230" height="346"/>

I'm also refining the backend to handle multiple leagues because at the moment it goes a little crazy when the internet connection is dodgy. It's currently at one of those stages where I fix one problem and break everything else that was working before the fix. What I want to be able to do is set it up so that I can handle, theoretically, an unlimited number of leagues. So when I add a new league on my server, I don't have to update the app though Apple. This means of course instead of waiting a couple of weeks for Puck to go through the review process with each new league I add, it can be pretty much instantly.

Next up is re-adding the live scores into a sidebar on the other side which also supports multiple leagues and then make some more detailed views for matches and other aspects. There is a fair bit to do and I want to (as I do with all my apps) test it into the ground before I upload the update to the App Store. I'm also planning an update of my server code to try to make it as fast as possible, so I suppose I should get back to work.
