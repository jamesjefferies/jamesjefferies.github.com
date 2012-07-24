---
comments: false
date: 2008-07-09 15:39:13
layout: post
slug: myfaces-12-and-tomcat-6
title: myfaces 1.2 and tomcat 6
wordpress_id: 31
---

Well, after much head scratching, it appears that myfaces 1.2 (.3 specifically) doesn't play ball with tomcat 6.0.14. A class cast error occurs when setting values determined by a select box.

Not only is this a bit rubbish, but it's cost me virtually a day of pain to work out what the problem was, and back out some changes.

Consequently I've gone back to myfaces 1.1.5 - painful, but true, as I'm not sure I'd be able to get the nod to upgrade the tomcats to 6.0.16 - which does seem to work.
