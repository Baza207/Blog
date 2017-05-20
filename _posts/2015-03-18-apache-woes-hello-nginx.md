---
layout: post
title: Apache Woes, Hello Nginx!
author: James Barrow
date: 2015-03-18
tags:
- nginx
- apache
- wordpress
- web servers
- web
- servers
- php
- php-fastcgi
image: nginx-logo.png
---

A couple of weeks ago I started getting emails from Jetpack[^1] telling me that my Wordpress blog was down. I was too busy at the time, but I came back to look into it around a week later. I was amazed to see that what the issue was that MySQL wasn’t running on my server. It took a while to work out what was wrong, but the long and short of it is I ran out of memory.

Now my server isn’t the most powerful one out there. It’s a 2GB Linode VPS[^2] but that should be more than powerful enough to run a simple Wordpress site. A deeper look into it showed me that Apache was using 1.99GB/2.0GB! So there’s the culprit.

READMORE

Apache is what I’ve used since the beginning, since I first got a VPS about 3 years ago. But now it’s stabbed me in the back using up all of my memory. So I scrapped it. 😛 Goodbye Apache, hello Nginx.

Nginx is a lightweight web server, and I could probably write a whole post of it in itself (actually, that’s sort of what this has become). After installing, setting it up and then removing Apache,  I went from my web server using up 1.99GB to using around 6-8MB. Now that, that is a massive improvement. Right, so lets get things running again. I setup PHP-FastCGI so my Wordpress site can work and I left it alone.

20 minutes later and Jetpack emails me saying that my blog is down again. Back to square 1. 😟 What’s going on now? Apparently PHP-FastCGI is doing the same thing that Apache was, though it’s capping itself to ~240MB. However it’s still getting to that cap and not releasing anything to be able to keep going. I did a bit of research and tried optimising (like I did with Apache before moving to Nginx) but nothing seems to work. 20 minutes after every time I restarted PHP-FastCGI, my Wordpress site would go down, pretty much on the dot.

So, I feel we’ve found the issue. Wordpress. For whatever reason it’s just being a fat memory hog. And after being so happy in optimising my memory usage when swapping to Nginx, I’m not going to let my blog do the same thing.

I ended up moving my whole blog to a static site (which I’ve written about here [Static Site Generators](/2015/static-site-generators/)) and that sorted out my issues. I am now using between 180MB and 220MB for standard usage. Which makes me extremely happy compared to to the over 1.99GB previously.

Setting up Nginx was simple, you install it was `sudo apt-get install nginx` and then you and then start it with `sudo service nginx start`. And hey presto, you're pretty much up and running. Linode has a load of really nice tutorials on it, though I'll mainly link this one, which details the basics (I'm sure you can find more specific ones for your own distributions with a simple search) <a href="https://www.linode.com/docs/websites/nginx/websites-with-nginx-on-debian-7-wheezy" target="_blank">Websites with Nginx on Debian 7 (Wheezy)</a>.

Unlike Apache, Nginx does require you to restart the web server every time you change something in either the main config file or one of your sites individual config files, but that takes less than a second using `sudo service nginx restart`, so it's not really an issue, just something to note.

One final note about PHP-FastCGI. If you have anything that requires PHP (for me, once I'd removed Wordpress it was just a token parsing script for APNs) then you will need to install and configure FastCGI. It is a pain in the arse, as there are so many conflicting sources out there on how to get it to work, all slightly different from each other. I can write another post, if people want it, about configuring a Nginx site to send PHP to FastCGI if people request it, but for now I will offer up the link that saved my hide and finally got it all working. <a href="http://wildlyinaccurate.com/solving-502-bad-gateway-with-nginx-php-fpm/" target="_blank">Solving "502 Bad Gateway" with nginx & php-fpm</a>.

In conclusion, Nginx is my new best friend when it comes to web servers. It's easy to setup, it's not impossible to understand the config file (unlike Apache where I always got lost instantly) and it takes up little to no memory when running a set of simple sites[^3]. If you're looking into getting a VPS and are wondering if you go for this widely talk about server Apache, I'd say wait, do you _need_ it? If the answer is anything but "they're paying me to use it", then you should use Nginx.

[^1]: Jetpack is a tool built into Wordpress that allows access to a range of tools, one of which being a status tool that emails the site's admin if it detects the site being down.
[^2]: If you feel like using Linode, which I highly recommend as a VPS provider, then check them out here with my referral link: <a href="https://www.linode.com/?r=398f3b1ce56e745028c920f81e56d1cbb13f57bf" target="_blank">Linode</a>.
[^3]: In my case, I'm running 4-5 low traffic sites, and some JSON feeds for some of my iOS apps to access.