---
layout: post
title: "Moving from WordPress to Octopress"
date: 2012-08-01 12:43
comments: true
categories: Techie
---
## What is Octopress?

[Octopress](http://octopress.org) is a blogging engine designed to be run from the command line, it uses Markdown for formatting content and doesn't have any built in GUI editing facilities.

It is worth looking at though because it generates static HTML files, so you don't need a database, you don't need PHP you just need to serve straight forward files.

The integration with github pages is very nice, so you can actually use github to host your blog or website leaving them to worry about server admin etc!

## Why did I switch?

At the moment, my virtual server was only hosting my blog and nothing else. At the moment, I don't need it for anything else, so being able to move to github pages for free was one draw, saving me £X a month. When I need a server again, I'll set one up.

I having nothing against WordPress per se, but it wasn't very hackable by me, a non-PHP developer. Now with Octopress, it seems a lot more straight forward. Plus I no longer have a MySQL or PHP install to maintain.

It *feels* like the Octopress templates are more designer friendly. I'll let you know if that is the case!

My site now has very straightforward version control, powered by git.

## How does it work?

You check out the [source](https://github.com/imathis/octopress) (from github of course). The html generating engine is written in ruby, so you need to have that installed. Once set up and configured, you can push your content using git to wherever you want to deploy it.

When you deploy, octopress turns your markdown and HTML templates in to straight forward HTML pages ready to be served.

It uses Disqus by default for comments, but if you have a WordPress account, you can set that up with Disqus before migration. Works a treat.

## Exiting WordPress

At first I tried the ruby WordPress migrating script. Basically it was not very good and I think I wasted a fair bit of time on it. Better is the Python [exitwp.py](https://github.com/thomasf/exitwp) script which is.. brilliant!

## Downsides

* There is a much smaller plugin selection available
* You generally re-generate the whole site when you want to publish something new (there are ways around that though, to selectively generate new content).
* If you had a blog with a lot of posts, then it might take some time to generate.
* Small amount of off-the-shelf themes

## Upsides

* The standard plugins you might want are available, twitter, github, google analytics.
* Github pages integration is very straightforward
* Simple caching can be set up if required, but no more W3 Total Cache Super Plugin things
* No WordPress security loopholes and patches
* No PHP or MySQL loopholes or patches
* Fast
* Relatively lightweight page sizes
* Nice default, responsive design

## Theme

I'm using a slightly customised default theme at the moment, but hopefully will have a bespoke one up and running soon.

## Summary

Now I'm migrated, I'm liking it so far, let me know what you think..
