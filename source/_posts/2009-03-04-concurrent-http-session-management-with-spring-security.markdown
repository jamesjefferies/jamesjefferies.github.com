---
comments: true
date: 2009-03-04 12:06:26
layout: post
slug: concurrent-http-session-management-with-spring-security
title: Concurrent HTTP session management with Spring Security
wordpress_id: 82
categories:
- java
tags:
- java
- security
- spring
---

Spring Security (formerly Acegi) is a useful framework for adding security to webapps. Directories, pages and the like can all be controlled with various user roles and methods can be annotated too, ensuring a belt and braces approach.

The setting to switch it on in the configuration is just this (within the other security config):

``` xml    
	<security:concurrent-session-control max-sessions="1" expired-url="/already-logged-in.faces"/>
```

and as you can see, you can set a url for spring to redirect to if you already have a session somewhere else. The gotcha though seems to be that unless you configure  a listener, it may not know when the session has expired (i.e. if you don't log out).

so, in the good old web.xml, add this little puppy to listen out for expired sessions...
``` xml  
<listener>
	<listener-class>org.springframework.security.ui.session.HttpSessionEventPublisher</listener-class>
</listener>
```

hopefully, job is a good 'un
