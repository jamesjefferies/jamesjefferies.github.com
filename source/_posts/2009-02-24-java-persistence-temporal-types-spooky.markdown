---
comments: false
date: 2009-02-24 10:55:26
layout: post
slug: java-persistence-temporal-types-spooky
title: Java persistence - temporal types - spooky
wordpress_id: 68
---

Should be easy this, but I made an assumption (probably on a Friday afternoon) and it's just returned to bite my petite derriere...

    
    javax.persistence.TemporalType


is an enum which can have three values

    
    DATE



    
    TIME



    
    TIMESTAMP


the differences being that with Date, you just get the date, no time factor at all.

Time, you just get the time, no date factor at all.

Timestamp, you get date and time, which is probably what you want when you want a timestamp (durr). Don't be misled in to thinking that a TemporalType.Date will include the time, because it won't!

I don't know why, but TemporalTypes make me think of Rentaghost... odd

http://www.hibernate.org/hib_docs/ejb3-api/javax/persistence/TemporalType.html
