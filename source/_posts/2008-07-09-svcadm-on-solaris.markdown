---
layout: post
title: !binary |-
  c3ZjYWRtIG9uIHNvbGFyaXM=
wordpress_id: 30
wordpress_url: !binary |-
  aHR0cDovL2phbWVzYW5kY2xhcmUubmV0L2xpZmUvP3A9MzA=
date: 2008-07-09 11:06:10.000000000 +00:00
---
svcadm is the service admin command line thing on solaris

e.g. svcadm enable tomcat will switch on the tomcat managed service

if a service doesn't start

svcs - all services

svcs -x  services with exceptions (in maintenance mode)

svcs -x -v as above, more verbose

svcadm clear tomcat - clears any exceptions
