---
comments: false
date: 2008-04-15 17:55:44
layout: post
slug: getting-hibernate-and-mysql-to-work-properly
title: Getting hibernate and mysql to work properly
wordpress_id: 13
---

When you have a problem with hibernate and mysql, namely mysql dropping the connection before hibernate does, then you need to configure the c3p0 connection pooling functionality. There are two main things which need setting, plus one which actually switches it on, helpfully badly documented!

``` xml
<property name="c3p0.idle_test_period">5</property>
<property name="c3p0.timeout">100</property>
<property name="c3p0.max_size">100</property>
``` 

The max size property actually switches connection pooling on and in this case sets it to a maximum of 100 connections in the pool. Then the other two come in to play.

idle_test_period is how many seconds between hibernate testing the unused connections in the pool to make sure they are still alive. You want this to be set to less than mysql's timeout.

timeout is how long an open connection will stay open before it times out.

So, as long as the idle_test_period is less than the mysql timeout, you should be ok. But don't forget the max_size, otherwise it isn't switched on at all!

You'll also need to add c3p0 as a maven dependency and include it in your package.

[codefin](http://www.codefin.net/2007/05/hibernate-and-mysql-connection-timeouts.html)
[hibernate docs](http://www.hibernate.org/214.html)
[c3p0](http://www.mchange.com/projects/c3p0/index.html#hibernate-specific)
