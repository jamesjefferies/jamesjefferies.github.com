---
comments: false
date: 2009-04-07 11:48:37
layout: post
slug: uml-diagrams-in-javadocs
title: UML diagrams in javadocs
wordpress_id: 143
categories:
- java
tags:
- java
---

Ok, so after all that excitement about javadocs, now we can really push the boat out by getting a maven plugin to also auto create UML diagrams. "Diagrams" I hear you ask, yes diagrams. Useful for people like me who like pictures.

So, this requires two steps. The first is to install graphviz which the plug in uses to create the pictures. A simple process on a linux box with apt-get.

The second is adding the following configuration to the pom...

    
    	<plugin>
            <artifactId>maven-javadoc-plugin</artifactId>
            <configuration>
              <source>1.6</source>
              <aggregate>true</aggregate>
              <doclet>gr.spinellis.umlgraph.doclet.UmlGraphDoc</doclet>
              <docletArtifact>
                <groupId>gr.spinellis</groupId>
                <artifactId>UmlGraph</artifactId>
                <version>4.6</version>
              </docletArtifact>
              <additionalparam>
                -inferrel -inferdep -quiet -hide java.*
                -collpackages java.util.* -qualify
                -postfixpackage -nodefontsize 9
                -nodefontpackagesize 7
              </additionalparam>
            </configuration>
          </plugin>


now, when you build the maven site you get nice UML diagrams in your javadocs
