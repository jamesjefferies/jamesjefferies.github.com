---
comments: false
date: 2009-06-29 17:04:15
layout: post
slug: embedded-tomcat-and-jetty
title: Embedded tomcat and jetty
wordpress_id: 236
---

With maven, running web apps with embedded tomcat & jetty is brill... as long as you have a straightforward configuration, not requiring lots of extra dependencies. The maven jetty plugin is super configurable though and can be tweaked as required.

To get the jetty plugin working though, you need to add the following to your settings.xml


org.mortbay.jetty


Once you've done that, it should pick up fine with mvn jetty:run for jetty or mvn tomcat:run for tomcat
