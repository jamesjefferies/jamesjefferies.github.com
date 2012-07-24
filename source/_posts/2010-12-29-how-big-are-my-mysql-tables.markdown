---
comments: true
date: 2010-12-29 13:41:15
layout: post
slug: how-big-are-my-mysql-tables
title: How big are my MySQL tables?
wordpress_id: 384
tags:
- linkedin
- mysql
---

You may ask yourself this question - here is a little query from [MySQL performance blog](http://www.mysqlperformanceblog.com/) which may well help:

``` sql    
SELECT count(*) TABLES,
TABLE_NAME,
concat(round(sum(table_rows)/1000000,2),'M') rows,
concat(round(sum(data_length)/(1024*1024*1024),2),'G') DATA,
concat(round(sum(index_length)/(1024*1024*1024),2),'G') idx,
concat(round(sum(data_length+index_length)/(1024*1024*1024),2),'G') total_size,
round(sum(index_length)/sum(data_length),2) idxfrac
FROM information_schema.TABLES
group by TABLE_NAME
order by total_size desc;
```
