---
layout: post
title: "Troubleshooting WordPress connectivity issue - could not connect to host"
date: 2012-09-05 14:57
comments: true
categories: 
- Techie
- WordPress
- Problem Solving
tags: 
- WordPress
- Techie
- Problem Solving
- Could Not Connect To Host

---
## The problem
After migrating a WordPress site, auto update and plugin install wouldn't work. The former errored with ```could not connect to host``` which seemed very odd.

### First attempts
WordPress allows you to download the file manually or autoupdate if configured correctly. Clicking on the manual download link and the file downloaded fine to the local machine. So first, I thought I'd try and download the file from the command line on the new server.

```
wget http://wordpress.org/wordpress-3.4.1.zip
```

Zip, it all downloaded fine.

### Extra help
There is a good trouble shooting/dev plugin for WordPress called [Core Control](http://wordpress.org/extend/plugins/core-control/). By installing this and enabling the HTTP control, you can test the various transports WordPress uses for downloads. Curl, PHP File open, PHP Fsockopen etc.

Testing all three default transports, starting with cURL came up with the same message, ```could not connect to host```

### Head Scratching time

So WordPress was telling the truth. Now, as WordPress was running as the ```www-data``` user, what happens if I tried the wget from the command line for that user?

```
wget http://wordpress.org/wordpress-3.4.1.zip
Permission denied!
```

Ah-ha, so it was nothing to do with WordPress, the ```www-data``` user couldn't download anything.

### Problem solved!

Firewalls, I started thinking firewalls and lo and behold, [BytemarkUK block outgoing http traffic](https://projects.bytemark.co.uk/projects/24/wiki/Firewall) for the www-data user by default! This makes sense for when sites get compromised, but it also stops some of the core functionality for updates etc working.

Enabling http traffic for the www-data user will make things worse if the site is compromised, but also makes it a lot easier to keep the site up to date, reducing the chances of a WordPress exploit.

The following removes the firewall rule

```
rm /etc/symbiosis/firewall/outgoing.d/50-www-data
```


