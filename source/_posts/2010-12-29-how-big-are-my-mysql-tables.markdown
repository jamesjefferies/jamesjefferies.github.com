---
layout: post
title: !binary |-
  SG93IGJpZyBhcmUgbXkgTXlTUUwgdGFibGVzPw==
wordpress_id: 384
wordpress_url: !binary |-
  aHR0cDovL2phbWVzamVmZmVyaWVzLmNvbS8/cD0zODQ=
date: 2010-12-29 13:41:15.000000000 +00:00
---
You may ask yourself this question - here is a little query from <a href="http://www.mysqlperformanceblog.com/">MySQL performance blog</a> which may well help:
<pre>SELECT count(*) TABLES,
TABLE_NAME,
concat(round(sum(table_rows)/1000000,2),'M') rows,
concat(round(sum(data_length)/(1024*1024*1024),2),'G') DATA,
concat(round(sum(index_length)/(1024*1024*1024),2),'G') idx,
concat(round(sum(data_length+index_length)/(1024*1024*1024),2),'G') total_size,
round(sum(index_length)/sum(data_length),2) idxfrac
FROM information_schema.TABLES
group by TABLE_NAME
order by total_size desc;</pre>
