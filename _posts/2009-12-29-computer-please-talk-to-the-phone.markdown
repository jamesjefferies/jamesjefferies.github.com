---
layout: post
title: !binary |-
  Q29tcHV0ZXIg4oCTIHBsZWFzZSB0YWxrIHRvIHRoZSBwaG9uZeKApg==
wordpress_id: 274
wordpress_url: !binary |-
  aHR0cDovL3d3dy5qYW1lc2FuZGNsYXJlLm5ldC8/cD0yNzQ=
date: 2009-12-29 11:19:41.000000000 +00:00
---
I have in my hand a piece of paper, well, actually it is an htc hero android phone, but let's not let that get in the way of an opening sentence..

Karmic Koala, Ubuntu 9.10 doesn't take kindly when you ask it to pick up an htc hero via USB. The android developers guide gives you hints for Hardy ubuntu, but nothing more recent. Assuming you've followed all the other steps outlined in the <a href="http://developer.android.com/guide/developing/device.html">guide</a>, you get stuck with this output when you run
<pre>adb devices</pre>
output is:
<pre>List of devices attached</pre>
<pre>????????????    no permissions</pre>
Fortunately, <a href="http://truthseekernz.blogspot.com/2009/11/ubuntu-910-and-adt-094-tangle.html">someone else</a> has done the hard work sorting out the authentication. This is what you need to do:
<pre><span><span class="Apple-style-span" style="font-family: Helvetica,Arial,sans-serif;">sudo vi /etc/udev/rules.d/51-android.rules </span></span></pre>
and add the following (for an HTC phone - the code changes for other devices)
<pre>SUBSYSTEMS=="usb", ATTRS{idVendor}=="0bb4", ATTRS{idProduct}=="0c01", MODE="0666"</pre>
<pre>SUBSYSTEMS=="usb", ATTRS{idVendor}=="0bb4", ATTRS{idProduct}=="0c02", MODE="0666"</pre>
Sort out permissions for that file
<pre>sudo chmod a+r /etc/udev/rules.d/51-android.rules</pre>
Then restarted the android debugging thingy (adb should be on the path after installing the Android SDK)
<pre>adb kill-server</pre>
<pre>sudo adb start-server</pre>
Now when you run
<pre>adb devices</pre>
you should get something like this:
<pre>List of devices attached
HT9C2L901094    device</pre>
