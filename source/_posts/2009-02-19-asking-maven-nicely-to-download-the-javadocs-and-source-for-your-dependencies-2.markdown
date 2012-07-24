---
layout: post
title: !binary |-
  QXNraW5nIE1hdmVuIG5pY2VseSB0byBkb3dubG9hZCB0aGUgamF2YWRvY3Mg
  YW5kIHNvdXJjZSBmb3IgeW91ciBkZXBlbmRlbmNpZXM=
wordpress_id: 62
wordpress_url: !binary |-
  aHR0cDovL2Jsb2dzLnRlY2hub3Bob2JpYS5pbnQvamplZmZlcmllcy8/cD02
  Mg==
date: 2009-02-19 16:40:08.000000000 +00:00
---
Just about every day I find something else useful out about Maven. Today's little nugget of joy is asking it to download the javadocs (i.e. standard api documentation) and the source of the libraries you're using in the project.

Because we use nexus, these nice bits of info will be stored centrally for all to use.

To get source and javadocs simply run
<pre>mvn eclipse:eclipse -DdownloadSources=true  -DdownloadJavadocs=true</pre>
and go and have a cup of tea or a biscuit or both.

You can also run this to get the sources
<pre>mvn -DdownloadSources=true dependency:sources</pre>
