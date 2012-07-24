---
comments: true
date: 2011-09-09 09:00:36
layout: post
slug: running-eclipse-under-the-unity-interface
title: Running Eclipse under the Unity interface
wordpress_id: 393
categories:
- java
- Techie
tags:
- eclipse
- java
- linkedin
- ubuntu
- unity
---

Unity eh? Love it or hate it the version in Ubuntu 11.04 seems not quite complete. Also other applications sometimes will not play nicely.

Eclipse is one of them, your menu items can go walk about. I found this [blog post](http://blog.matto1990.com/2011/04/using-eclipse-under-ubuntu-11-04-natty/) which has a helpful hint. Unsetting UBUNTU_MENUPROXY for the application does the trick

    
    #!/bin/bash
    unset UBUNTU_MENUPROXY
    path/to/eclipse/here



