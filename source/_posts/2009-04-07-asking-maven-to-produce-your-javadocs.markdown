---
comments: false
date: 2009-04-07 09:33:11
layout: post
slug: asking-maven-to-produce-your-javadocs
title: Asking Maven to produce your javadocs
wordpress_id: 140
---

Javadocs are the java platforms standard way of producing code documentation, comments about what the class is for, which methods are provided and all that kind of stuff. It feels a bit old school now, but they are really useful if kept up to date.

As we are building our project using maven, we can ask maven to build a 'site' for our project. This pulls in various bits of information about the project, including dependencies on other libraries (and their licencing models) and all kinds of interesting stuff.

One of the maven plugins generates the javadocs for your project and it's very straightforward to set up, just add this to the reporting section of your pom file (for maven) and when you do a mvn site it automatically builds your javadocs.

    
    <plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-javadoc-plugin</artifactId>
    </plugin>
