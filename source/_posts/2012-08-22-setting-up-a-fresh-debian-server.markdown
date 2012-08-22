---
layout: post
title: "Setting up a Fresh Debian Server"
date: 2012-08-22 14:41
comments: true
published: true
categories: 
- Techie
---

## Accessing the server

Once set up, you will have the IP address, in the form 123.456.789.012 and the root password. This means you will be able to log on to the server using ssh (secure shell), i.e. 

```
ssh root@123.456.789.012
```

You will get a message along the lines of

```
The authenticity of host '123.456.789.012(123.456.789.012)' can't be established. RSA key fingerprint is blah blah bla
Are you sure you want to continue connecting (yes/no)?
```

to which you will reply

```
yes
```

and you will then get

```
Warning: Permanently added '123.456.789.012' (RSA) to the list of known hosts.
root@123.456.789.012's password: 
```
which is when you can enter your password. Hopefully then you'll be logged on to the server.

```
blah blah blah snip…
servername:~# 
```

### First things first

Root access is the super user for your server. You really don't want to have people being able to log on to your server as root. What you really need is to have user accounts which people can use to log on, and if/when required, they can get super user privileges to do whatever they need to do.

What we are going to do is to stop root being able to secure shell straight in to the server, create a new user account to use for our admin (with upgradable privileges) and run ssh on a different port to deter basic attacks.

### Change root's password!

So you have a default root password - CHANGE IT to a new one! From a root prompt, use ```passwd``` to change the password

### Adding a new user

```
adduser james
```

Will create a new user, called James - you can add in extra details as you go like full name etc.

Now we want to allow james a bit of privilege, not by default though, but by using the sudo command.

#### Aside - setting default editor to be vi

By default, for all users, you may want to use vi as your editor (ok, you may not, but I do!) so add the following to ```/etc/profile```

```
EDITOR=vi
export EDITOR
```

### Giving the new user sudo privileges

You may need to install sudo if it isn't already installed on your server. It's a simple case of
```
apt-get install sudo
```

Then, the application ```visudo``` is your friend. You edit the config file using visudo and then sudo does the rest. When you open the file, you'll see a section with:

```
# User privilege specification
root    ALL=(ALL) ALL
admin ALL = (ALL) ALL
james ALL = (ALL) ALL
```
By adding my own entry, it allows me to upgrade my user to super user privileges for all actions. You can limit the commands which users can run if you like using this, but if you are going to be the super user, you probably want to leave it as all.

## Sorting out access

Let's stop people attempting to log on to the server as [root via ssh](http://www.howtogeek.com/howto/linux/security-tip-disable-root-ssh-login-on-linux/) and also to run ssh on a different port than the default. There is a lot of good advice [here](http://www.foogazi.com/2006/11/29/modify-ssh-to-maximize-security/)

### Amend port

The default port is 22, change this to something else, which isn't being used by anything else

```
# What ports, IPs and protocols we listen for
Port 60
```

### Stop root login

Now stop people logging in as root
```
PermitRootLogin no
```

### Some other bits

Give maximum number of log in attempts to be 3, only allow james to login.

```
MaxAuthTries 3
AllowUsers james 
```

### Restart sshd

As root (or sudo)
```
/etc/init.d/ssh restart
```

Now try logging in remotely from a different shell (i.e. keep the one you've just restarted sshd on open in case you have any problems!)

```
ssh -p60 james@123.456.789.0123
```

obviously set the p to be the port you set earlier.

### Stop chancers getting in

It's also a good idea to stop people attempting to log on to your server using common passwords, usernames etc. A good way to do this is to install the [fail2ban](http://en.wikipedia.org/wiki/Fail2ban) which goes some way to banning people trying to brute force their way in to your server.

```
apt-get install fail2ban
```

Default settings are pretty good here.

## Firewall configuration

UFW or Uncomplicated Firewall is a good first port of call for securing your shiny new server. You can install it as root with

```
apt-get install ufw
```

Now, unlike fail2ban, ufw is installed switched off. You need to configure a few things before getting it up and running and providing that extra security. By default ALL ports are shut, so make sure you've opened up the ones you need before switching the firewall on!

For example, if you've set up your ssh to run on port 60, then you need to run

```
ufw allow 60
```

If you're going to be running apache on port 80 (the usual)

```
ufw allow 80
```

Here are a few [notes](http://www.mmncs.com/2011/07/this-guide-shows-howto-install-and-setup-uncomplicatedfirewall-ufw-on-linux-ubuntu-10-04-and-11-04-and-other-debian-distributions/)

Don't forget to run ```ufw enable``` when you are ready! ```ufw status``` tells you what is set up.





























