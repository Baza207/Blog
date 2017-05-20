---
layout: post
title: Static Site Generators
author: James Barrow
date: 2015-03-19
tags:
- static site
- middleman
- blog
- ruby
- nginx
- wordpress
- disqus
image: middleman-logo.png
---

**PRE-POST NOTE:** The origins of this post really starts in another post. I was having issues with Apache and my Wordpress setup, and those issues made me move to Nginx and then to using a static site generator. To read more of those details that got me to this point, read here: [Apache Woes, Hello Nginx!](/2015/apache-woes-hello-nginx/)

I have been using Wordpress since I started my site, I think it must have been back in 2010-2011, and it’s done all I’ve wanted it to do, and more. But it’s always felt too much than I needed. I’ve tried to dive into making my own themes a couple of times, but swiftly given up, just because the amount of _stuff_ there was, it overwhelmed me. So after the problems I was having with my server (see pre-post note), I decided to move to a static site.

What is a static site? Static site generators are programs that take templates and content you make and render the content into separate, compiled files. This means, unlike a dynamic site, the content is already created and ready to serve to the requesting web browser, unlike a dynamic site, like Wordpress, that renders the content and creates the web page (in Wordpress’ case using PHP) when and every time it is requested (though obviously facing systems can and are used, but still).

READMORE

This instantly gives me several benefits when using a static site, the most prominent in my eyes is that we get an enormous speed boost. I have never used my blog in a big way, I’ve never managed to keep up a good posting schedule, and it’s always been just me posting. So all of the _mass_ features that Wordpress has, multiple users, massive plugin expandability with a few clicks, I’ve never needed.

It was mentioned to me by a friend[^1] that he used a static site generator for his blog. He uses [Middleman](https://middlemanapp.com), but there were others such as [Jekyll](http://jekyllrb.com) and then from there I also found [Octopress](http://octopress.org) (which is built on top of Jekyll).

For your site, you can choose which you feel is best, but after a bit of searching around, reading comments and looking into the separate docs, I decided to go with Middleman. It was mainly for 3 reasons;
1. It was in Ruby, which I haven’t really used before[^2], so bring on something new!
2. I liked the site, the documentation seemed simple to understand and to the point and there wasn’t an excess to _stuff_ that I didn’t need to bog it down,
3. My friend Matt used it. I think it’s important to use things that have been recommended to you by people who’s judgement you trust (and as a side point, who can help you if it isn’t working or you break something 😉).

So I started setting up my middleman-blog site, and after a while of tinkering, adding this, moving that, (pestering Matt when it something didn’t work,) I have my new blog up and running. It was taking me a while to get used to using Ruby and then Haml as my templating markup language, but I was learning, and getting there. And the main point, it was fun and simple. Nothing ever happened that made me throw my arms up and walk away from my computer.

Of course, there were a few issues I had (like my code syntax css file refusing to generate on build, I had to save the `.css` file manually myself) etc, but overall, things were going well.

### Exporting Blog Posts from Wordpress

With my new Middleman blog setup, now I needed content. Well I had that, but it was all in Wordpress, wrapped up in the MySQL database. Luckily I am not the first to make the switch and [Mike Ball](https://github.com/mdb) has made a great little Ruby Gem called [wp2middleman](https://github.com/mdb/wp2middleman) that takes the `.xml` file you can export from Wordpress and turns it into markdown files[^3]. After that, it’s just a matter or sorting the post files into the organisational system you’ve chosen for you blog, and off you go.

**Note:** There are obviously some things you need to keep an eye out for. For example, Wordpress does love to add certain `<p>` and `<div>` tags along with ids and classes. Noramally this happens when you’ve told your posts content to formatter in a certain way (entered, justified, etc). Also, there’s the `<!--more-->` line where you want to break you post summary on the main page. Though these should be easily fixed with something like SublimeText’s (or whatever editor you’re using) find and replace feature, it’s something to look out for.

### Disqus Comments

Comments were one of the last things to move over, mainly because I was expecting them to be a painful experience to move over, but I was quite wrong there. Now I don’t get a lot of comments on my blog, but I have a few and I didn’t want to start from scratch. So I looked around a bit for what other people use. I wasn’t feeling like using something such as Facebook or Google+, those commenting systems always seem a bit cluttered for my tastes (and constantly trying to drag you back to the sites respectively).

I then found a very basic, but obviously powerful system called [Poole](http://pooleapp.com) which at first seemed exactly what I wanted, but after a deeper looked into it was a great but very basic system. I wasn’t looking for something I had to build up from scratch, at least, not at this point in time. I just wanted to have something I could dump at the bottom of my posts, import my old Wordpress comments to and carry on with my life.

[Disqus](https://disqus.com) was the answer to this. It’s a simple commenting system, closer to that of Facebook or Google+ than Poole, but it doesn’t feel as _loud_ on the page. Also, it has the ability (via a [Wordpress plugin](https://wordpress.org/plugins/disqus-comment-system/)) to export comments from your Wordpress blog. All boxes ticked, and after that, it was a simple few lines to implement.

`Gemfile`

```ruby
gem "middleman-disqus"
```

`config.rb`

```ruby
# Disqus Comments
activate :disqus do |d|
  d.shortname = 'short_name'
end
```

And then in your article layout file, `article.ham` for me.

```haml
= disqus
= disqus_count
```

And you’re done. There are a few extra things to do in Disqus, but you can find them in the [admin panel](https://disqus.com/admin/create/) on the Disqus site.

### Wrap-up

Overall I’m currently in love with static sites. They’re so fast, and now I’ve got my foot in the door and feel I understand the basics, I can really see some amazing places I can go with it. That along with the fact my blog is now amazingly fast compared to how it was when running via Wordpress, I can’t wait to base some more sites off of it.

I am not condemning Wordpress, or dynamic sites in general. In some cases (and there’s a lot of them) it’s exactly what’s needed. But for me and for this, Middleman and a static site works a charm. I just have to think of some other ways to use it now.

[^1]: My good friend Matt is normally the guy who helps me fix the issues I get myself into when it comes to my server. I only wish I can repay his help when it comes to iOS development as much as he helps me with Server stuff. Check out his blog here: <https://mattprice.me>
[^2]: Up until now, when I’ve stayed away from iOS, Obj-C and Swift, it’s been to do things in Python, but it’s always nice to have a change.
[^3]: it also seems to convert some other items like custom menu items etc, if you you’ve added that type of thing to your Wordpress blog, but they’re not hard to filter out.