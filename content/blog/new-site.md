+++
title = 'New Site!'
date = 2023-12-07T13:43:32+01:00
draft = false
tags = ['web', 'dev', 'hugo', 'performance']
+++

So, tldr, I changed this site.

The old site was basically a [Jekyll](https://jekyllrb.com/) site using the [Minima theme](https://github.com/jekyll/minima) which works great. The thing is that recently I came across [this blog post](https://endtimes.dev/why-your-website-should-be-under-14kb-in-size/) by Nathaniel where he disserts about how websites should be under 14kb in size and... I realized he was completely right!

I always disliked how websites nowadays are absolutely huge even for simple websites like, for example, [Google's homepage](https://google.com/), which have barely a couple of elements and almost no content, downloads several MBs of data. This is the result of heavy use of Javascript files, web telemetry and analytics, weird fonts and some more crap, which works great with high speed connections, which are widely available, but not always! So I decided that my website should be as simple as possible.

Right now, the homepage of this website should download around 4.4 KBs of data to your device, while the old version of my website would have downloaded around 35.6 KBs. This should translate on most visits to my website being able to download almost every page of my website in one TCP packet each, which should increase the performance.

Another advantage of reducing network usage is to reduce the carbon footprint of webpages, which in this case is insignificant since my website does not have that big amount of network traffic, but still, is pretty nice.

## How to

So, in order to do this I started playing around with [Hugo](https://gohugo.io/), which is a tool to build static webpages in a similar fashion as Jekyll. I tried looking at [themes.gohugo.io](https://themes.gohugo.io/) for minimal themes, but all of them had some heavy Javascript or CSS frameworks so... I decided to create my [own theme](https://github.com/manglaneso/mango)! 

This theme has no Javascript, barely 160 lines of CSS and makes the website look with a cool 90s retro look! And also does the job okay, so if you feel like you could use it, install instructions are in the README :).

