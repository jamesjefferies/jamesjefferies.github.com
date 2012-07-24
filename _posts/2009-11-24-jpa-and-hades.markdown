---
layout: post
title: !binary |-
  SlBBIGFuZCBIYWRlcw==
wordpress_id: 258
wordpress_url: !binary |-
  aHR0cDovL3d3dy5qYW1lc2FuZGNsYXJlLm5ldC8/cD0yNTg=
date: 2009-11-24 23:21:43.000000000 +00:00
---
JPA (Java Persistence API) is the standard implementation for persistence in the Java world. Although most people would probably use Hibernate (which is JPA compliant) the JPA spec gives a standard way forward for the various persistence vendors to produce compliant platforms which they can then extend with their own bells and whistles.

Having used JPA a few times now, I've found it to be well thought out and useful. However, although JPA 2.0 is around the corner there are still some improvments which could be made. Hades is an open source library which is built on top of JPA and makes producing the Data Access (DAO) layer super easy. Using convention over configuration means that simply by writing an interface with the simple queries you require is all that is required for Hades to factory produce the actual services you will need.

So, for example, by declaring public User findByUsername(String username);  in your service interface, Hades will automatically generate a corresponding query returning a type safe User. This works for lists as well (which solves the pain of having generic lists returned which are not type safe)

It uses a genericDAO service which is the JPA entity manager on steroids.

Proper named queries can be added to the interface and once again, Hades will implement the query for you.

All in all, definitely worth a look.
