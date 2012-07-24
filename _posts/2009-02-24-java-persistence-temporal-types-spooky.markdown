---
layout: post
title: !binary |-
  SmF2YSBwZXJzaXN0ZW5jZSAtIHRlbXBvcmFsIHR5cGVzIC0gc3Bvb2t5
wordpress_id: 68
wordpress_url: !binary |-
  aHR0cDovL2Jsb2dzLnRlY2hub3Bob2JpYS5pbnQvamplZmZlcmllcy8/cD02
  OA==
date: 2009-02-24 10:55:26.000000000 +00:00
---
Should be easy this, but I made an assumption (probably on a Friday afternoon) and it's just returned to bite my petite derriere...
<pre>javax.persistence.TemporalType</pre>
is an enum which can have three values
<pre>DATE</pre>
<pre>TIME</pre>
<pre>TIMESTAMP</pre>
the differences being that with Date, you just get the date, no time factor at all.

Time, you just get the time, no date factor at all.

Timestamp, you get date and time, which is probably what you want when you want a timestamp (durr). Don't be misled in to thinking that a TemporalType.Date will include the time, because it won't!

I don't know why, but TemporalTypes make me think of Rentaghost... odd

http://www.hibernate.org/hib_docs/ejb3-api/javax/persistence/TemporalType.html
