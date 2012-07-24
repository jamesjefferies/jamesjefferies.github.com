---
layout: post
title: !binary |-
  SGliZXJuYXRlIFNlYXJjaCwgTHVjZW5lIGFuZCBHcmVlbndpY2ggTWVhbiBU
  aW1l
wordpress_id: 225
wordpress_url: !binary |-
  aHR0cDovL3d3dy5qYW1lc2FuZGNsYXJlLm5ldC8/cD0yMjU=
date: 2009-04-22 10:20:05.000000000 +00:00
---
Aww, what a gotcha this morning. Felt stoopid when I realised what was going on.

There are a number of ways to use dates with Lucene and specifically with Hibernate Search, which is what I'm using at the moment for providing a wrapper around Lucene. I wanted to search for a certain date range on a field.. which has been set to midnight. You can probably guess what's coming here. Now we're in British Summer Time our clocks are forward, but of course, the date is stored by Lucene as GMT, consequently, without a bit of cleverness, something saved at 12:01 AM on the 2nd April BST, is actually 11:01 PM on the 1st April GMT.

Throw in a date range search looking for stuff from the 2nd April onwards and things start going a bit wonky!

By the way, here is how it now woorks, still may not be the best way to do it, but it's working for now.

<code> @Field(index = Index.UN_TOKENIZED)
@DateBridge(resolution = Resolution.HOUR)
@Temporal(TemporalType.DATE)
private Date startDate;</code>
