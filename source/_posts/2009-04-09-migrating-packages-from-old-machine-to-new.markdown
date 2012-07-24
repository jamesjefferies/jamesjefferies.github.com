---
comments: false
date: 2009-04-09 11:41:31
layout: post
slug: migrating-packages-from-old-machine-to-new
title: Migrating packages from old machine to new
wordpress_id: 150
---

Before switching off your old ubuntu machine for good, run

    
    dpkg --get-selections > Packages.lst


which will output all the stuff you've installed using the package manager to a flat file (Packages.lst). Copy this file to your new machine.

    
    dpkg --set-selections < Packages.lst


will then set all those packages ready for install on your new machine.

Martin reckons run this first as a dry-run

    
    sudo apt-get -s dselect-upgrade


and then when you are feeling brave

    
    sudo apt-get dselect-upgrade


will install them for you...hopefully!

oh and watch out for things you *don't* want to install on the new machine, like gfx drivers. You can remove them from Packages.lst
