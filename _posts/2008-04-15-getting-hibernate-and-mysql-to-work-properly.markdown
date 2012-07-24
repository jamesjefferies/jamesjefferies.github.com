---
layout: post
title: !binary |-
  R2V0dGluZyBoaWJlcm5hdGUgYW5kIG15c3FsIHRvIHdvcmsgcHJvcGVybHk=
wordpress_id: 13
wordpress_url: !binary |-
  aHR0cDovL2phbWVzYW5kY2xhcmUubmV0L2xpZmUvP3A9MTM=
date: 2008-04-15 17:55:44.000000000 +00:00
---
When you have a problem with hibernate and mysql, namely mysql dropping the connection before hibernate does, then you need to configure the c3p0 connection pooling functionality. There are two main things which need setting, plus one which actually switches it on, helpfully badly documented!

&lt;property name="c3p0.idle_test_period"&gt;5&lt;/property&gt;
&lt;property name="c3p0.timeout"&gt;100&lt;/property&gt;
&lt;property name="c3p0.max_size"&gt;100&lt;/property&gt;

The max size property actually switches connection pooling on and in this case sets it to a maximum of 100 connections in the pool. Then the other two come in to play.

Idle test period is how many seconds between hibernate testing the unused connections in the pool to make sure they're ok. You want this to be set less than mysql's timeout.

timeout is how long an open connection will stay open before it times out.

So, as long as idle test period is less than the mysql timeout, you should be ok. But don't forget the max_size otherwise it isn't switched on at all!

You'll also need to add c3p0 as a maven dependency and include it in your package.

http://www.codefin.net/2007/05/hibernate-and-mysql-connection-timeouts.html

http://www.hibernate.org/214.html

http://www.mchange.com/projects/c3p0/index.html#hibernate-specific
