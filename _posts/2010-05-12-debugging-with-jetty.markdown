---
layout: post
title: !binary |-
  RGVidWdnaW5nIHdpdGggSmV0dHk=
wordpress_id: 390
wordpress_url: !binary |-
  aHR0cDovL2phbWVzamVmZmVyaWVzLmNvbS8/cD0zOTA=
date: 2010-05-12 13:45:24.000000000 +00:00
---
Having used jetty a fair bit recently, one thing I couldn't get working was remote debugging connections from Eclipse. The magic combination of parameters for Jetty 6.1.24 and Java 1.6 is as follows, if you're using maven.
<pre>export MAVEN_OPTS="$MAVEN_OPTS -Xdebug -agentlib:jdwp=transport=dt_socket,server=y,address=8000,suspend=n" ; mvn jetty:run</pre>
