---
layout: post
title: !binary |-
  UnVubmluZyBFY2xpcHNlIHVuZGVyIHRoZSBVbml0eSBpbnRlcmZhY2U=
wordpress_id: 393
wordpress_url: !binary |-
  aHR0cDovL2phbWVzamVmZmVyaWVzLmNvbS8/cD0zOTM=
date: 2011-09-09 09:00:36.000000000 +00:00
---
Unity eh? Love it or hate it the version in Ubuntu 11.04 seems not quite complete. Also other applications sometimes will not play nicely.

Eclipse is one of them, your menu items can go walk about. I found this <a href="http://blog.matto1990.com/2011/04/using-eclipse-under-ubuntu-11-04-natty/">blog post</a> which has a helpful hint. Unsetting UBUNTU_MENUPROXY for the application does the trick
<pre class="brush: java;">#!/bin/bash
unset UBUNTU_MENUPROXY
path/to/eclipse/here</pre>
&nbsp;
