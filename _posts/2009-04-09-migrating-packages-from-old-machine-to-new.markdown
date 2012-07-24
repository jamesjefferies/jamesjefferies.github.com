---
layout: post
title: !binary |-
  TWlncmF0aW5nIHBhY2thZ2VzIGZyb20gb2xkIG1hY2hpbmUgdG8gbmV3
wordpress_id: 150
wordpress_url: !binary |-
  aHR0cDovL2Jsb2dzLnRlY2hub3Bob2JpYS5pbnQvamplZmZlcmllcy8/cD0x
  MTQ=
date: 2009-04-09 11:41:31.000000000 +00:00
---
Before switching off your old ubuntu machine for good, run
<pre>dpkg --get-selections &gt; Packages.lst</pre>
which will output all the stuff you've installed using the package manager to a flat file (Packages.lst). Copy this file to your new machine.
<pre>dpkg --set-selections &lt; Packages.lst</pre>
will then set all those packages ready for install on your new machine.

Martin reckons run this first as a dry-run
<pre>sudo apt-get -s dselect-upgrade</pre>
and then when you are feeling brave
<pre>sudo apt-get dselect-upgrade</pre>
will install them for you...hopefully!

oh and watch out for things you *don't* want to install on the new machine, like gfx drivers. You can remove them from Packages.lst
