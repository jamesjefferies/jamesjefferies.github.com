---
comments: true
date: 2010-10-14 10:17:33
layout: post
slug: maven-gets-an-update-3-0
title: Maven gets an update - 3.0
wordpress_id: 318
categories:
- java
tags:
- linkedin
---

Maven is the build & dependency management tool we use for all our java projects. Used correctly it's ace, but it can also prove to be a headache when you head off the beaten track.

Maven 3.0 has just been released which contains a lot of new goodies, plus, alleged backwards compatibility!

The pom file, which is the main file which describes the structure of the project, it'd dependencies and plugins *is* backwards compatible, but there is stricter validation. So when I ran one of our project configuration files through the new version, it came up with a number of missing versions and scopes in the wrong place. Easy to fix and the config still works with version 2 or 3. Bigger and more complicated project structures may have more problems.

The two things I think are most interesting are:



	
  * When an error occurs, rather than just spitting out an error message, a link is included to a wiki page, what a great idea! For example:



    
    [ERROR] For more information about the errors and possible solutions, please read the following articles:
    [ERROR] [Help 1] <a href="http://cwiki.apache.org/confluence/display/MAVEN/NoGoalSpecifiedException">http://cwiki.apache.org/confluence/display/MAVEN/NoGoalSpecifiedException</a>





	
  * The maven shell has been updated, the shell is a high performance console add on, giving you syntax highlighting and context sensitive help. At the mo you can download and [install it from github ](http://github.com/sonatype/mvnsh)


I'll be taking it out for a spin with some of our projects to see if there any issues, before we maybe have a look at some of our other projects.
