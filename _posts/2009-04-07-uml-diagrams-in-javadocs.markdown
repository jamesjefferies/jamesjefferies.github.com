---
layout: post
title: !binary |-
  VU1MIGRpYWdyYW1zIGluIGphdmFkb2Nz
wordpress_id: 143
wordpress_url: !binary |-
  aHR0cDovL2Jsb2dzLnRlY2hub3Bob2JpYS5pbnQvamplZmZlcmllcy8/cD0x
  MDU=
date: 2009-04-07 11:48:37.000000000 +00:00
---
Ok, so after all that excitement about javadocs, now we can really push the boat out by getting a maven plugin to also auto create UML diagrams. "Diagrams" I hear you ask, yes diagrams. Useful for people like me who like pictures.

So, this requires two steps. The first is to install graphviz which the plug in uses to create the pictures. A simple process on a linux box with apt-get.

The second is adding the following configuration to the pom...
<pre>	&lt;plugin&gt;
        &lt;artifactId&gt;maven-javadoc-plugin&lt;/artifactId&gt;
        &lt;configuration&gt;
          &lt;source&gt;1.6&lt;/source&gt;
          &lt;aggregate&gt;true&lt;/aggregate&gt;
          &lt;doclet&gt;gr.spinellis.umlgraph.doclet.UmlGraphDoc&lt;/doclet&gt;
          &lt;docletArtifact&gt;
            &lt;groupId&gt;gr.spinellis&lt;/groupId&gt;
            &lt;artifactId&gt;UmlGraph&lt;/artifactId&gt;
            &lt;version&gt;4.6&lt;/version&gt;
          &lt;/docletArtifact&gt;
          &lt;additionalparam&gt;
            -inferrel -inferdep -quiet -hide java.*
            -collpackages java.util.* -qualify
            -postfixpackage -nodefontsize 9
            -nodefontpackagesize 7
          &lt;/additionalparam&gt;
        &lt;/configuration&gt;
      &lt;/plugin&gt;</pre>
now, when you build the maven site you get nice UML diagrams in your javadocs
