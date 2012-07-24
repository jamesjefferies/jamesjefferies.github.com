---
comments: true
date: 2009-12-06 00:20:35
layout: post
slug: mounting-readynas-duo-drives-in-ubuntu
title: Mounting ReadyNAS Duo drives from Ubuntu
wordpress_id: 260
categories:
- Techie
tags:
- linkedin
---

Choosing a NAS solution where you can't mount the storage media outside of the NAS is asking for trouble. I was worried I'd made the wrong choice when I found that mounting the ReadyNAS do ext3 drives is not trivial, mainly because they use a 16kb block size with their SPARC cpus.

A bit of routing around found various solutions, but the one which worked for me was as follows.



	
  1. Fire up ubuntu vm (running on OS X for me and in my case 9.10 Karmic)

	
  2. install lvm2 with a apt-get install lvm2

	
  3. Download ext2fuse 0.5 (from [here](http://linux.softpedia.com/progDownload/ext2fuse-Download-29820.html) for example)

	
  4. run vgscan to locate drives

	
  5. vgchange -ay c to allow access to drive

	
  6. mkdir /mnt/lvm

	
  7. ext2fuse /dev/c/c /mnt/lvm (where ext2fuse will have been downloaded)

	
  8. drive can now be accessed on /mnt/lvm


Hurrah!
