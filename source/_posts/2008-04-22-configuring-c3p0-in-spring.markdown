---
comments: false
date: 2008-04-22 15:24:37
layout: post
slug: configuring-c3p0-in-spring
title: Configuring c3p0 in spring
wordpress_id: 18
---

Tricky, the username and password have to be in the properties bundle as follows:

<bean id="dataSource" class="com.mchange.v2.c3p0.ComboPooledDataSource" destroy-method="close">
<property name="driverClass"><value>com.mysql.jdbc.Driver</value></property>
<property name="jdbcUrl"><value>${db-connection-url}</value></property>
<property name="properties">
<props>
<prop key="user">${db-connection-username}</prop>
<prop key="password">${db-connection-password}</prop>
<prop key="c3p0.timeout">25200</prop>
<prop key="c3p0.idle_test_period">14400</prop>
<prop key="c3p0.max_size">50</prop>
</props>
</property>

</bean>
