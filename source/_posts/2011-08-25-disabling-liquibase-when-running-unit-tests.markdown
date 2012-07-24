---
layout: post
title: !binary |-
  RGlzYWJsaW5nIGxpcXVpYmFzZSB3aGVuIHJ1bm5pbmcgdW5pdCB0ZXN0cw==
wordpress_id: 374
wordpress_url: !binary |-
  aHR0cDovL2phbWVzamVmZmVyaWVzLmNvbS8/cD0zNzQ=
date: 2011-08-25 09:33:44.000000000 +00:00
---
If you're running Liquibase, configured by Spring (or whatever) and you don't want it to run it's checks when running unit tests, you can disable it from running by setting a system property.

Whilst running a single unit test class many times, you might want to add a system set property call before any of the tests are run. Hence:
<pre class="brush: java;"> @BeforeClass
    public static void switchOffLiquibase() {
        System.setProperty(Liquibase.SHOULD_RUN_SYSTEM_PROPERTY, "false");
    }</pre>
