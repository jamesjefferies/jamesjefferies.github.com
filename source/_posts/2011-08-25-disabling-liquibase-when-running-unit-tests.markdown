---
comments: true
date: 2011-08-25 09:33:44
layout: post
slug: disabling-liquibase-when-running-unit-tests
title: Disabling liquibase when running unit tests
wordpress_id: 374
categories:
- java
tags:
- junit
- linkedin
- liquibase
---

If you're running Liquibase, configured by Spring (or whatever) and you don't want it to run it's checks when running unit tests, you can disable it from running by setting a system property.

Whilst running a single unit test class many times, you might want to add a system set property call before any of the tests are run. Hence:

``` java    
@BeforeClass
public static void switchOffLiquibase() {
	System.setProperty(Liquibase.SHOULD_RUN_SYSTEM_PROPERTY, "false");
}
```
