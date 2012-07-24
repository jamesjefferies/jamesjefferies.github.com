---
layout: post
title: !binary |-
  Q3JlYXRpbmcgbXlzcWwgdXNlcnM=
wordpress_id: 70
wordpress_url: !binary |-
  aHR0cDovL2Jsb2dzLnRlY2hub3Bob2JpYS5pbnQvamplZmZlcmllcy8/cD03
  MA==
date: 2009-02-25 14:12:07.000000000 +00:00
---
I used to know Ingres RDBMS pretty well and then got well in to Oracle, in fact, I've got 7 years of Oracle experience probably. Unfortunately, each day that goes by, I forget how to do the ninja stuff I used to be able to do..

Instead now, I'm using HSQLDB for in memory speedy development and then today have been getting local mysql up and running. Of course, it's easy to get the db fired up on ubuntu, where I have the block is creating a simple user who can log on to the flippin' thing. All you mysql veterans out there will be stroking your beard wondering what all the fuss is about. So, to remind my self, here's some pimple simple stuff...
<pre> grant all on DATABASENAME.* to 'NEWUSERNAME'@'localhost' identified by 'NEWPASSWORD';</pre>
Yeah, yeah, you could, should do a lot more with this, but for what I want, it just works...
