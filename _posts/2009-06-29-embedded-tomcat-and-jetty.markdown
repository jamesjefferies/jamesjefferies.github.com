---
layout: post
title: !binary |-
  RW1iZWRkZWQgdG9tY2F0IGFuZCBqZXR0eQ==
wordpress_id: 236
wordpress_url: !binary |-
  aHR0cDovL3d3dy5qYW1lc2FuZGNsYXJlLm5ldC8/cD0yMzY=
date: 2009-06-29 17:04:15.000000000 +00:00
---
With maven, running web apps with embedded tomcat & jetty is brill... as long as you have a straightforward configuration, not requiring lots of extra dependencies. The maven jetty plugin is super configurable though and can be tweaked as required.

To get the jetty plugin working though, you need to add the following to your settings.xml

<pluginGroups>
<pluginGroup>org.mortbay.jetty</pluginGroup>
</pluginGroups>

Once you've done that, it should pick up fine with mvn jetty:run for jetty or mvn tomcat:run for tomcat
