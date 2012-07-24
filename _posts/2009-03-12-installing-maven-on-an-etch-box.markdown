---
layout: post
title: !binary |-
  SW5zdGFsbGluZyBtYXZlbiBvbiBhbiBldGNoIGJveA==
wordpress_id: 92
wordpress_url: !binary |-
  aHR0cDovL2Jsb2dzLnRlY2hub3Bob2JpYS5pbnQvamplZmZlcmllcy8/cD05
  Mg==
date: 2009-03-12 11:53:22.000000000 +00:00
---
Ok, noddy stuff this really, but it's good reference for me, thanks to wilbatron. Lenny has maven packaged, but etch doesn't, so a manual install is required!

oh, make sure java and bzip2 are installed and set up

download maven binary, unarchive it, move to /usr/local do some links
<pre>wget http://www.mirrorservice.org/sites/ftp.apache.org/maven/binaries/apache-maven-2.0.9-bin.tar.bz2
tar xjvf apache-maven-2.0.9-bin.tar.bz2
mv apache-maven-2.0.9 /usr/local/
ln -s /usr/local/apache-maven-2.0.9/ /usr/local/maven
ln -s /usr/local/maven/bin/mvn /usr/local/bin/</pre>
I went a bit off piste after that and added the following to /etc/mvnrc rather than chuck them in the mvn shell script

JAVA_HOME=/whatever/this/is
M2_HOME=/wherever/you/put/it
MAVEN_OPTS="-Xms256m -Xmx512m"
