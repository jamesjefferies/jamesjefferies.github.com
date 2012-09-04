---
layout: post
title: "Poor old java"
date: 2012-09-04 12:11
comments: true
categories:
- Techie
- java
 
---
There seems to be a lot of noise at the moment about the latest security vulnerabilities in Java, especially Java 7. I'd go as far as to say that some of the articles are [scare stories](http://www.pcadvisor.co.uk/news/security/3379150/time-give-java-boot/). Is this what we need, to give Java the boot?

## TL;DR

All computers connected to things have security vulnerabilities of various forms.

Desktop Java installed computers where not required is an unnecessary security risk and should be uninstalled, just as Adobe Flash, Adobe Reader, Silverlight etc. Windows 8 and Mac OS X don't bundle Java runtimes via default anymore. This is a good thing. Oracle should be far quicker out of the blocks fixing security vulnerabilitles.

Giving Java the boot full stop is an over the top reaction. However, giving Java the boot on the desktop when it's not required is a wise move.

## History

Java as a platform has a reputation for being secure, reliable and frequently patched. Being able to run Java server side on Sun software provided the building blocks for many web businesses at the end of the last millenium and in to this one. 

It also has many branches in to other parts of the internet ecosystem. As well as running server side, the other two main areas are mobile Java, J2ME, for example and desktop Java, either via browser plugin Applets or as runnable GUI applications using a desktop JVM (virtual machine).

Over the last few years, mobile Java has basically been nobbled by the rise of smartphones and their respective application frameworks and stacks, Android, iOS, Windows whatever it's called, BlackBerry and the rest. 

However, the legacy of desktop Java has continued by some applications still requiring a JVM installed on the local PC and some people still writing or using Java applets. Althoguh Sun and now Oracle have continued to try and encourage desktop development with their JavaFX initative, they've not got very far.

### Applets

The idea behind applets was that you visited a site via a web browser, which could always deliver the latest version of the application code to your browser, either to run in a plug-in or using the JVM installed on your machine. They were useful for some niche applications, you sometimes see them now replacing flash file uploaders for example, but the User Experience was often a bit shonky.

### Desktop Applications

Write Once, run anywhere was the mantra behind Java Desktop applications, an attractive proposition. One set of code would run on Windows, Linux, Unix variants & Macs. Many Java development environments have been written in Java and are used today. CrashPlan is an example cross platform application which requires desktop Java to work.

## Legacy

Unfortunately, a lot of the Java runtimes (and Flash installs, adobe reader installs etc), installed in days of yore on people's machines will have security vulnerabilities, either because they are out of date or because of recent new exploits. 

It was interesting to see Apple's response to recent JVM exploits, although they may have been slow in responding, they, in effect, switched off people's Java installations, providing a prompt if it was required. In one OS X update (assuming it was installed!) Macs became better protected from Java exploits. 

## Summary

If you don't use Java on your machine - uninstall it, it's not worth having a potential vulnerability. Same with Flash or Adobe reader - if you don't use them, uninstall them. 

If you do need it installed on your machine, there is some great advice [here](http://www.macworld.co.uk/macsoftware/news/?newsid=3378690&pagtype=allchandate)

Of course, keep things up to date that you do use, Operating systems, browsers etc

Java server side is a different story. If you do use the Java Virtual Machine, whether it is for Java apps, Clojure, Scala or whatever. Keep your eyes on the Oracle security bulletins, update when you can and be aware of any vulnerabilities in the latest version. 


