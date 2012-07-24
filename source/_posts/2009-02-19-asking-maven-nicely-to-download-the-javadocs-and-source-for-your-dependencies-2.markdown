---
comments: false
date: 2009-02-19 16:40:08
layout: post
slug: asking-maven-nicely-to-download-the-javadocs-and-source-for-your-dependencies-2
title: Asking Maven nicely to download the javadocs and source for your dependencies
wordpress_id: 62
categories:
- java
tags:
- java
- maven
---

Just about every day I find something else useful out about Maven. Today's little nugget of joy is asking it to download the javadocs (i.e. standard api documentation) and the source of the libraries you're using in the project.

Because we use nexus, these nice bits of info will be stored centrally for all to use.

To get source and javadocs simply run

    
    mvn eclipse:eclipse -DdownloadSources=true  -DdownloadJavadocs=true


and go and have a cup of tea or a biscuit or both.

You can also run this to get the sources

    
    mvn -DdownloadSources=true dependency:sources
