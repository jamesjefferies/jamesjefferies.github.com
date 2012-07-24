---
layout: post
title: !binary |-
  c3ZuIGRpZmYgaWdub3Jpbmcgd2hpdGVzcGFjZQ==
wordpress_id: 239
wordpress_url: !binary |-
  aHR0cDovL3d3dy5qYW1lc2FuZGNsYXJlLm5ldC8/cD0yMzk=
date: 2009-09-04 17:05:02.000000000 +00:00
---
svn diff is nice but not very configurable... fear not!

svn diff --diff-cmd diff -x -uw /path/to/file

will save the day. this tells svn diff to use diff with the -uw flags. Brill...

now to get it working with my favourite diff, sdiff!
