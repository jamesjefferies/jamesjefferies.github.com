---
comments: true
date: 2010-12-29 11:08:40
layout: post
slug: getting-spring-and-liquibase-to-play-nicely
title: Getting Spring and Liquibase to play nicely
wordpress_id: 339
categories:
- java
- Techie
tags:
- java
- linkedin
- spring
---

Liquibase comes with out of the box Spring integration, although there are few configuration options if you take this route. Straight after your web application is deployed, the Spring container will start - as it starts, it runs the Liquibase database migrations before the application is fully instantiated.

Getting it working with v2.0.0 proved problematic, the way you get it working is to add the following to your Spring context (note clazz should be class, but is messes up the markup!)

``` xml    
    	<bean id="liquibase" clazz="liquibase.integration.spring.SpringLiquibase">
    		<property ref="dataSource" name="dataSource"></property>
    		<property name="changeLog" value="classpath:db/changelog-master.xml"></property>
    
    		<property name="contexts" value="test, production"></property>
    	</bean>	
```    

which is all well and good, except the SpringLiquibase class crashes on instantiation - it's expecting a map named 'parameters' to exist. Unfortunately, when you try and inject the map in to the class, that fails too as the Map can't be set externally... looking at the code, you can see where it's going wrong - fortunately, it has been fixed in the latest overnight snapshot build, so instead of using v2.0.0 I'm now using V2.0.1.SNAPSHOT

I could have created my own implementation of SpringLiquibase - in fact this would have been my next step, but for now I'll stick with the updated snapshot.
