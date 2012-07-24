---
layout: post
title: !binary |-
  Y2xhc3MgZXF1YWxz
wordpress_id: 27
wordpress_url: !binary |-
  aHR0cDovL2phbWVzYW5kY2xhcmUubmV0L2xpZmUvP3A9Mjc=
date: 2008-05-12 13:41:23.000000000 +00:00
---
ok, so if you don't want to do the instanceof (which allows subclasses to pass) you simply want to use .equals.. as so:

classA.getClass().equals(classB.class)) {
