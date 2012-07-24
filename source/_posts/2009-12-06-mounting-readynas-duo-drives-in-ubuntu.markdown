---
layout: post
title: !binary |-
  TW91bnRpbmcgUmVhZHlOQVMgRHVvIGRyaXZlcyBmcm9tIFVidW50dQ==
wordpress_id: 260
wordpress_url: !binary |-
  aHR0cDovL3d3dy5qYW1lc2FuZGNsYXJlLm5ldC8/cD0yNjA=
date: 2009-12-06 00:20:35.000000000 +00:00
---
Choosing a NAS solution where you can't mount the storage media outside of the NAS is asking for trouble. I was worried I'd made the wrong choice when I found that mounting the ReadyNAS do ext3 drives is not trivial, mainly because they use a 16kb block size with their SPARC cpus.

A bit of routing around found various solutions, but the one which worked for me was as follows.
<ol>
	<li>Fire up ubuntu vm (running on OS X for me and in my case 9.10 Karmic)</li>
	<li>install lvm2 with a apt-get install lvm2</li>
	<li>Download ext2fuse 0.5 (from <a href="http://linux.softpedia.com/progDownload/ext2fuse-Download-29820.html">here</a> for example)</li>
	<li>run vgscan to locate drives</li>
	<li>vgchange -ay c to allow access to drive</li>
	<li>mkdir /mnt/lvm</li>
	<li>ext2fuse /dev/c/c /mnt/lvm (where ext2fuse will have been downloaded)</li>
	<li>drive can now be accessed on /mnt/lvm</li>
</ol>
Hurrah!
