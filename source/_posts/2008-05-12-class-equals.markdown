---
comments: false
date: 2008-05-12 13:41:23
layout: post
slug: class-equals
title: class equals
wordpress_id: 27
---

ok, so if you don't want to do the instanceof (which allows subclasses to pass) you simply want to use .equals.. as so:
``` java
classA.getClass().equals(classB.class)) 
```
