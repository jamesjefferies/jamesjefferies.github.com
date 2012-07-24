---
comments: true
date: 2010-12-14 16:40:04
layout: post
slug: liquibase-and-the-maven-plugin
title: Liquibase and the Maven Plugin
wordpress_id: 324
categories:
- java
tags:
- java
- linkedin
---

I'm having a look at the [Liquibase](http://liquibase.org/home) product at the mo, mainly to help automate the database migrations for one of our clients. Currently the process is a bit hairy and manual. It's easy to make mistakes and you have to be on the ball, plus rollbacks are awkard and generally it's a mess.

Liquibase is a Database Change Management system - as they say "You never develop code without version control, why do you develop your database without it?" - and I agree.

However, in classic Open Source fashion, the documentation leaves something to be desired. So when I found myself trusting the documentation and getting the error:

``` sh    
    The driver has not been specified either as a parameter or in a properties file
```

when it was specified in both properties and as a parameter I should have realised that it was the documentation which was wrong, not me. I'm far too trusting....

So, when you set up the maven plugin in and they recommend doing this:

``` xml 
<plugin>
	<groupid>org.liquibase</groupid>
        <artifactid>liquibase-plugin</artifactid>
        <version>1.6.1.0</version>
        <executions>
        	<execution>
                	<phase>process-resources</phase>
                  	<configuration>
                    		<propertyfile>src/main/resources/liquibase.properties</propertyfile>
                  	</configuration>
                  	<goals>
                    		<goal>update</goal>
                  	</goals>
               	</execution>
        </executions>
</plugin>
```    

you just ignore them as the configuration is only set for that particular phase - whereas you want the configuration for all phases.. so you should set it up like this instead, makes a lot of sense really.

``` xml 
            <plugin>
                <groupid>org.liquibase</groupid>
                <artifactid>liquibase-plugin</artifactid>
                <version>1.9.3.0</version>
                <configuration>
                    <propertyfile>src/main/resources/liquibase.properties</propertyfile>
                    <changelogfile>src/main/resources/db/changelog-master.xml</changelogfile>
                    <driver>com.mysql.jdbc.Driver</driver>
                    <url>${db-connection-url}</url>
                    <username>${db-connection-username}</username>
                    <password>${db-connection-password}</password>
                </configuration>
                <executions>
                    <execution>
                        <phase>process-resources</phase>
                        <goals>
                            <goal>update</goal>
                        </goals>
                    </execution>
                </executions>
            </plugin>
``` 

hurrah.
