---
comments: false
date: 2009-03-03 09:05:25
layout: post
slug: using-dml-for-an-update-with-hibernatejpa
title: Using DML for an update with hibernate/JPA
wordpress_id: 80
tags:
- java
---

Got caught out with a gotcha last night which I 'solved' this morning. I hate leaving work with an annoying problem, but I knew I was too tired to get it clear in my head.  So, I was doing a direct update to an object in the database using

    
    Query query = entityManager.createQuery("Update Foo f set f.value = :value where f.key = :key");
    query.executeUpdate();


Which works, the database gets updated. However by doing the update directly the hibernate persistence context is bypassed so although the db is sorted, hibernate is blissfully ignorant of what you've done. Yes, what YOU have done!

So, one way to get around this is to ask hibernate to refresh what it knows about the object using the entity manager (by the way, the entity manager is JPA's equivalent of the hibernate session manager).

    
    entityManager.refresh(theFoo);


Or.. I guess you could retrieve the Foo object, update it and then save it and you wouldn't have got in this pickle in the first place...
