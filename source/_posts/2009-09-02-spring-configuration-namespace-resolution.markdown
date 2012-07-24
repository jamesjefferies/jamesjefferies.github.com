---
comments: false
date: 2009-09-02 17:07:31
layout: post
slug: spring-configuration-namespace-resolution
title: Spring configuration namespace resolution
wordpress_id: 243
---

try saying "Spring configuration namespace resolution" with a mouthful of tea.

Anyway, from Spring 2.5, one can use the new namespace resolution functionality in your spring configuration. We've used this for example (by the way, http bits have lost a slash - stops them getting wordpress'd), here:



Which allows you to use the namespace amq in your spring configuration, i.e.

 

spring knows that amq maps to the active mq schema, and as we provide a url in the location section, it knows where it can get it from.

The only downside to this is when apache.org goes down, as it did last week. Spring tries to look up the schema, can't and consequently fails to start. This is catastrophic.

I've been trying to find out how to work around this, ideally I'd like Spring to get the xsd from the classpath (where I've put it) rather than trying to download it from the internet. Just in case apache.org disappears up it's own firewall.. again.

The change is simple, if you know how. Chuck the .xsd schema file in src/main/resources and update the config as follows, change in red - hurrah!


