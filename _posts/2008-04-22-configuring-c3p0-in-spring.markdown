---
layout: post
title: !binary |-
  Q29uZmlndXJpbmcgYzNwMCBpbiBzcHJpbmc=
wordpress_id: 18
wordpress_url: !binary |-
  aHR0cDovL2phbWVzYW5kY2xhcmUubmV0L2xpZmUvP3A9MTg=
date: 2008-04-22 15:24:37.000000000 +00:00
---
Tricky, the username and password have to be in the properties bundle as follows:

&lt;bean id="dataSource" class="com.mchange.v2.c3p0.ComboPooledDataSource" destroy-method="close"&gt;
&lt;property name="driverClass"&gt;&lt;value&gt;com.mysql.jdbc.Driver&lt;/value&gt;&lt;/property&gt;
&lt;property name="jdbcUrl"&gt;&lt;value&gt;${db-connection-url}&lt;/value&gt;&lt;/property&gt;
&lt;property name="properties"&gt;
&lt;props&gt;
&lt;prop key="user"&gt;${db-connection-username}&lt;/prop&gt;
&lt;prop key="password"&gt;${db-connection-password}&lt;/prop&gt;
&lt;prop key="c3p0.timeout"&gt;25200&lt;/prop&gt;
&lt;prop key="c3p0.idle_test_period"&gt;14400&lt;/prop&gt;
&lt;prop key="c3p0.max_size"&gt;50&lt;/prop&gt;
&lt;/props&gt;
&lt;/property&gt;

&lt;/bean&gt;
