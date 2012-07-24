---
comments: false
date: 2009-05-01 10:22:15
layout: post
slug: deploying-applications-to-tomcat-running-under
title: Deploying applications to tomcat running under /
wordpress_id: 227
---

Standard practice with tomcat is that the application is deployed under a directory which is derived from the name of the war file archive which is deployed.

i.e. foo.war will be deployed to the foo directory and will be accessed with the URL http://application-server-url/foo

All well and good, but what if you want to access it as http://app-server-url/   ?

a number of approaches were tried, none of which worked 100%, they part worked or ended up with the application being deployed twice. Pain, pain, pain.

Trying to use docbase in the server.xml, i.e.

`<Context path="" docBase="foo" debug="1"/>`

will result in the application being deployed to / and /foo - not good, we only want it deployed once.

So, take a step back. Only one application can be deployed under / and for tomcat, this defaults to one called ROOT.war, so rather than creating and deploying foo.war, call it ROOT.war and it will deploy to /, once and everyone is happy.
