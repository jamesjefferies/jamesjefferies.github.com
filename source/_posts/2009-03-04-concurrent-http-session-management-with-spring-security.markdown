---
layout: post
title: !binary |-
  Q29uY3VycmVudCBIVFRQIHNlc3Npb24gbWFuYWdlbWVudCB3aXRoIFNwcmlu
  ZyBTZWN1cml0eQ==
wordpress_id: 82
wordpress_url: !binary |-
  aHR0cDovL2Jsb2dzLnRlY2hub3Bob2JpYS5pbnQvamplZmZlcmllcy8/cD04
  Mg==
date: 2009-03-04 12:06:26.000000000 +00:00
---
Spring Security (formerly Acegi) is a useful framework for adding security to webapps. Directories, pages and the like can all be controlled with various user roles and methods can be annotated too, ensuring a belt and braces approach.

The setting to switch it on in the configuration is just this (within the other security config):
<pre>      &lt;security:concurrent-session-control max-sessions="1" expired-url="/already-logged-in.faces"/&gt;</pre>
and as you can see, you can set a url for spring to redirect to if you already have a session somewhere else. The gotcha though seems to be that unless you configure  a listener, it may not know when the session has expired (i.e. if you don't log out).

so, in the good old web.xml, add this little puppy to listen out for expired sessions...
<pre>  &lt;listener&gt;
	  &lt;listener-class&gt;org.springframework.security.ui.session.HttpSessionEventPublisher&lt;/listener-class&gt;
  &lt;/listener&gt;</pre>
hopefully, job is a good 'un
