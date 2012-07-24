---
comments: true
date: 2009-12-29 11:19:41
layout: post
slug: computer-please-talk-to-the-phone
title: Computer – please talk to the phone…
wordpress_id: 274
categories:
- java
- Techie
tags:
- linkedin
---

I have in my hand a piece of paper, well, actually it is an htc hero android phone, but let's not let that get in the way of an opening sentence..

Karmic Koala, Ubuntu 9.10 doesn't take kindly when you ask it to pick up an htc hero via USB. The android developers guide gives you hints for Hardy ubuntu, but nothing more recent. Assuming you've followed all the other steps outlined in the [guide](http://developer.android.com/guide/developing/device.html), you get stuck with this output when you run

``` sh    
    adb devices
```

output is:

``` sh 
    List of devices attached
    ????????????    no permissions
```

Fortunately, [someone else](http://truthseekernz.blogspot.com/2009/11/ubuntu-910-and-adt-094-tangle.html) has done the hard work sorting out the authentication. This is what you need to do:

``` html   
<span><span style="font-family: Helvetica,Arial,sans-serif;" class="Apple-style-span">sudo vi /etc/udev/rules.d/51-android.rules </span></span>
```

and add the following (for an HTC phone - the code changes for other devices)

``` sh    
    SUBSYSTEMS=="usb", ATTRS{idVendor}=="0bb4", ATTRS{idProduct}=="0c01", MODE="0666"
    SUBSYSTEMS=="usb", ATTRS{idVendor}=="0bb4", ATTRS{idProduct}=="0c02", MODE="0666"
```

Sort out permissions for that file

``` sh    
    sudo chmod a+r /etc/udev/rules.d/51-android.rules
```

Then restarted the android debugging thingy (adb should be on the path after installing the Android SDK)

``` sh 
    adb kill-server
    sudo adb start-server
```

Now when you run

``` sh    
    adb devices
```

you should get something like this:

``` sh  
    List of devices attached
    HT9C2L901094    device
```
