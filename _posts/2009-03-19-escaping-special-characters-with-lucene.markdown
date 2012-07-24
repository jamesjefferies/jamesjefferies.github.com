---
layout: post
title: !binary |-
  RXNjYXBpbmcgc3BlY2lhbCBjaGFyYWN0ZXJzIHdpdGggbHVjZW5l
wordpress_id: 138
wordpress_url: !binary |-
  aHR0cDovL2Jsb2dzLnRlY2hub3Bob2JpYS5pbnQvamplZmZlcmllcy8/cD0x
  MDA=
date: 2009-03-19 12:10:57.000000000 +00:00
---
If you're using Lucene queries then there are some special characters which do magic things. Of course you might not want any wild card / range magic going on and you'd rather the searcher could look up ] without everything blowing up.

Well, you can escape those special characters simply by passing the query through the escape method of the QueryParser.. like so
<pre>searchTerm = QueryParser.escape(searchTerm);</pre>
of course this will nobble any asterixes or similar in there, so if you do want any wildcard stuff going on, add after the escaping.
