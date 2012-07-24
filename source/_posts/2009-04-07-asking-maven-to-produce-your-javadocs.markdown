---
layout: post
title: !binary |-
  QXNraW5nIE1hdmVuIHRvIHByb2R1Y2UgeW91ciBqYXZhZG9jcw==
wordpress_id: 140
wordpress_url: !binary |-
  aHR0cDovL2Jsb2dzLnRlY2hub3Bob2JpYS5pbnQvamplZmZlcmllcy8/cD0x
  MDI=
date: 2009-04-07 09:33:11.000000000 +00:00
---
Javadocs are the java platforms standard way of producing code documentation, comments about what the class is for, which methods are provided and all that kind of stuff. It feels a bit old school now, but they are really useful if kept up to date.

As we are building our project using maven, we can ask maven to build a 'site' for our project. This pulls in various bits of information about the project, including dependencies on other libraries (and their licencing models) and all kinds of interesting stuff.

One of the maven plugins generates the javadocs for your project and it's very straightforward to set up, just add this to the reporting section of your pom file (for maven) and when you do a mvn site it automatically builds your javadocs.
<pre>&lt;plugin&gt;
&lt;groupId&gt;org.apache.maven.plugins&lt;/groupId&gt;
&lt;artifactId&gt;maven-javadoc-plugin&lt;/artifactId&gt;
&lt;/plugin&gt;</pre>
