---
comments: false
date: 2008-04-18 14:38:42
layout: post
slug: really-useful-transaction-stuff
title: Really useful transaction stuff
wordpress_id: 16
---

For this to work, you MUST set up the data source in the spring section rather than hibernate, otherwise the transaction manager doesn't create the session.. and goodness me, the DAOs are so much tidier, no phase listener crap either!

http://www.javalobby.org/articles/thread-safe/index.jsp
