---
comments: true
date: 2011-03-09 13:36:24
layout: post
slug: using-constants-in-spring-configuration
title: Using constants in spring configuration
wordpress_id: 380
tags:
- java
- linkedin
- spring
---

Whilst doing some re-work on a loan calculator, I wanted to move the configuration of the various loan rates in to the spring XML configuration. Setting up the various loan rates for the amount borrowed is relatively straightforward, but I wanted to use constants (defined only once in the app) in the map rather than straight strings. Easy you may say.. and indeed, it is if you use the 'util' schema.

Add the util schema to your bean configuration xml

``` xml

    <beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xmlns:util="http://www.springframework.org/schema/util"
    xsi:schemaLocation="
    http://www.springframework.org/schema/beans
    http://www.springframework.org/schema/beans/spring-beans-3.0.xsd
    http://www.springframework.org/schema/util
    http://www.springframework.org/schema/util/spring-util-3.0.xsd">
``` 

and then you can just reference your constants as follows:``

``` xml 
    <util:constant static-field="com.foo.bar.RATE_2000_2950" />
```    
