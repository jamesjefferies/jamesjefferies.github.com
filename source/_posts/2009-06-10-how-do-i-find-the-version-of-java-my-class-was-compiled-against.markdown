---
comments: false
date: 2009-06-10 17:03:20
layout: post
slug: how-do-i-find-the-version-of-java-my-class-was-compiled-against
title: How do I find the version of java my class was compiled against?
wordpress_id: 233
---

Is a very good question and something I couldn't quite remember from the mists of time. However, there is a utility to help...

javap -verbose Classname

where Classname is your class, will give you loads of information, including major and minor java version numbers. Handy huh?
