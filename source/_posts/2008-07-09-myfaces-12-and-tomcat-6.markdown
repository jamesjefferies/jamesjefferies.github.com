---
layout: post
title: !binary |-
  bXlmYWNlcyAxLjIgYW5kIHRvbWNhdCA2
wordpress_id: 31
wordpress_url: !binary |-
  aHR0cDovL2phbWVzYW5kY2xhcmUubmV0L2xpZmUvP3A9MzE=
date: 2008-07-09 15:39:13.000000000 +00:00
---
Well, after much head scratching, it appears that myfaces 1.2 (.3 specifically) doesn't play ball with tomcat 6.0.14. A class cast error occurs when setting values determined by a select box.

Not only is this a bit rubbish, but it's cost me virtually a day of pain to work out what the problem was, and back out some changes.

Consequently I've gone back to myfaces 1.1.5 - painful, but true, as I'm not sure I'd be able to get the nod to upgrade the tomcats to 6.0.16 - which does seem to work.
