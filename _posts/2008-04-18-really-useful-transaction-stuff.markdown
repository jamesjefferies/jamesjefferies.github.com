---
layout: post
title: !binary |-
  UmVhbGx5IHVzZWZ1bCB0cmFuc2FjdGlvbiBzdHVmZg==
wordpress_id: 16
wordpress_url: !binary |-
  aHR0cDovL2phbWVzYW5kY2xhcmUubmV0L2xpZmUvP3A9MTY=
date: 2008-04-18 14:38:42.000000000 +00:00
---
For this to work, you MUST set up the data source in the spring section rather than hibernate, otherwise the transaction manager doesn't create the session.. and goodness me, the DAOs are so much tidier, no phase listener crap either!

http://www.javalobby.org/articles/thread-safe/index.jsp
