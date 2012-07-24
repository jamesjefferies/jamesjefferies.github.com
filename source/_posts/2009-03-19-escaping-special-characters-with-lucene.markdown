---
comments: false
date: 2009-03-19 12:10:57
layout: post
slug: escaping-special-characters-with-lucene
title: Escaping special characters with lucene
wordpress_id: 138
tags:
- java
---

If you're using Lucene queries then there are some special characters which do magic things. Of course you might not want any wild card / range magic going on and you'd rather the searcher could look up ] without everything blowing up.

Well, you can escape those special characters simply by passing the query through the escape method of the QueryParser.. like so

    
    searchTerm = QueryParser.escape(searchTerm);


of course this will nobble any asterixes or similar in there, so if you do want any wildcard stuff going on, add after the escaping.
