---
layout: post
title: !binary |-
  VXNpbmcgRE1MIGZvciBhbiB1cGRhdGUgd2l0aCBoaWJlcm5hdGUvSlBB
wordpress_id: 80
wordpress_url: !binary |-
  aHR0cDovL2Jsb2dzLnRlY2hub3Bob2JpYS5pbnQvamplZmZlcmllcy8/cD04
  MA==
date: 2009-03-03 09:05:25.000000000 +00:00
---
Got caught out with a gotcha last night which I 'solved' this morning. I hate leaving work with an annoying problem, but I knew I was too tired to get it clear in my head.  So, I was doing a direct update to an object in the database using
<pre>Query query = entityManager.createQuery("Update Foo f set f.value = :value where f.key = :key");
query.executeUpdate();</pre>
Which works, the database gets updated. However by doing the update directly the hibernate persistence context is bypassed so although the db is sorted, hibernate is blissfully ignorant of what you've done. Yes, what YOU have done!

So, one way to get around this is to ask hibernate to refresh what it knows about the object using the entity manager (by the way, the entity manager is JPA's equivalent of the hibernate session manager).
<pre>entityManager.refresh(theFoo);</pre>
Or.. I guess you could retrieve the Foo object, update it and then save it and you wouldn't have got in this pickle in the first place...
