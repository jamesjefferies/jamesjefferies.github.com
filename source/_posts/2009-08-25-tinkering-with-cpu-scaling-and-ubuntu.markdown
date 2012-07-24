---
layout: post
title: !binary |-
  VGlua2VyaW5nIHdpdGggQ1BVIHNjYWxpbmcgYW5kIFVidW50dQ==
wordpress_id: 241
wordpress_url: !binary |-
  aHR0cDovL3d3dy5qYW1lc2FuZGNsYXJlLm5ldC8/cD0yNDE=
date: 2009-08-25 17:06:55.000000000 +00:00
---
I have a little gnome applet running which tells me how fast my CPUs are running. Annoyingly, they seem to be lazing about at 2.0Ghz, saving energy and all that, speeding up (allegedly) when required.

This seemed like a bit of cop out to me, I want them running at 2.3Ghz, their max speed, when I'm compiling and running apps! I'm all for saving energy, but I want the control.

Well, now I have it thanks to a bit of reconfiguring..

sudo dpkg-reconfigure gnome-applets

Running this allows the CPU speed applet to change the settings (with root permission). So, I have changed it from On Demand to Performance. Hurrah!

More on the configuration you can achieve can be found in this interesting article. Click here! (sorry, couldn't resist!)
