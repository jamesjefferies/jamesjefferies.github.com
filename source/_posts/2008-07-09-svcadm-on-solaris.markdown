---
comments: false
date: 2008-07-09 11:06:10
layout: post
slug: svcadm-on-solaris
title: svcadm on solaris
wordpress_id: 30
---

svcadm is the service admin command line thing on solaris

e.g. svcadm enable tomcat will switch on the tomcat managed service

if a service doesn't start

svcs - all services

svcs -x  services with exceptions (in maintenance mode)

svcs -x -v as above, more verbose

svcadm clear tomcat - clears any exceptions
