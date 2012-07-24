---
comments: false
date: 2008-11-14 13:58:47
layout: post
slug: so-i-broke-the-package-installer-2
title: So I broke the package installer
wordpress_id: 127
---

Tinkering around with vmware server install meant that I couldn't do any apt-get stuff. It kept on trying to remove the half installed debian package, failing when running the scripts.

useful commands
``` sh
dpkg --list
```

gives a list of the packages installed, the ii first bit, is installed stuff, I think the half installed one was hI or something similar, it stood out anyway!

the pre/post scripts were causing a problem. I found them here:
``` sh
/var/lib/dpkg/info
```
and so I nobbled the four of them:

``` sh
-rwxr-xr-x 1 root root  6772 2008-11-13 10:36 vmware-server.prerm
-rwxr-xr-x 1 root root 30474 2008-11-13 10:36 vmware-server.preinst
-rwxr-xr-x 1 root root  1510 2008-11-13 10:36 vmware-server.postrm
-rwxr-xr-x 1 root root 48652 2008-11-13 10:36 vmware-server.postinst
```
and ran this

``` sh
sudo dpkg --purge  vmware-server
```
hooray!
