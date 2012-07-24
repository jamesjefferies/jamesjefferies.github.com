---
layout: post
title: !binary |-
  R2V0dGluZyBTdW4gamRrNiB1cCBhbmQgcnVubmluZyBvbiBEZWJpYW4gZXRj
wordpress_id: 58
wordpress_url: !binary |-
  aHR0cDovL2Jsb2dzLnRlY2hub3Bob2JpYS5pbnQvamplZmZlcmllcy8/cD01
  OA==
date: 2009-02-18 12:31:00.000000000 +00:00
---
ok, so we'll be going for proper open jdk at some point (Java 7 preferably) but to get us up and running with Java 6 update 7...

add the following to /etc/apt/sources.list
<pre>deb http://ftp.us.debian.org/debian/ etch main contrib non-free
deb http://www.backports.org/debian etch-backports main non-free</pre>
and run
<pre>sudo apt-get update</pre>
before running
<pre>sudo apt-get install sun-java6-jdk</pre>
now, I had a problem with the default java install (not sure how to tinker with /etc/alternatives yet) so I uninstalled
<pre> sudo apt-get remove sablevm</pre>
and
<pre> sudo apt-get remove free-java-sdk</pre>
once I work out /etc/alternatives beyond them just being symbolic links, then that'll be not required I guess
