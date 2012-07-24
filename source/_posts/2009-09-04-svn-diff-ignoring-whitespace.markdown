---
comments: false
date: 2009-09-04 17:05:02
layout: post
slug: svn-diff-ignoring-whitespace
title: svn diff ignoring whitespace
wordpress_id: 239
---

svn diff is nice but not very configurable... fear not!

``` sh
svn diff --diff-cmd diff -x -uw /path/to/file
```

will save the day. this tells svn diff to use diff with the -uw flags. Brill...

now to get it working with my favourite diff, sdiff!
