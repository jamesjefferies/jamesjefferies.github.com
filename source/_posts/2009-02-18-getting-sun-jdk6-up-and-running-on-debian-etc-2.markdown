---
comments: false
date: 2009-02-18 12:31:00
layout: post
slug: getting-sun-jdk6-up-and-running-on-debian-etc-2
title: Getting Sun jdk6 up and running on Debian etc
wordpress_id: 58
tags:
- java debian sun
---

ok, so we'll be going for proper open jdk at some point (Java 7 preferably) but to get us up and running with Java 6 update 7...

add the following to /etc/apt/sources.list

    
    deb http://ftp.us.debian.org/debian/ etch main contrib non-free
    deb http://www.backports.org/debian etch-backports main non-free


and run

    
    sudo apt-get update


before running

    
    sudo apt-get install sun-java6-jdk


now, I had a problem with the default java install (not sure how to tinker with /etc/alternatives yet) so I uninstalled

    
     sudo apt-get remove sablevm


and

    
     sudo apt-get remove free-java-sdk


once I work out /etc/alternatives beyond them just being symbolic links, then that'll be not required I guess
