---
layout: post
title: !binary |-
  RGlmZmVyZW5jZSBiZXR3ZWVuIGluc3RhbmNlb2YgYW5kIGlzSW5zdGFuY2U=
wordpress_id: 26
wordpress_url: !binary |-
  aHR0cDovL2phbWVzYW5kY2xhcmUubmV0L2xpZmUvP3A9MjY=
date: 2008-05-12 10:52:28.000000000 +00:00
---
f  you use instanceof or isInstance it will succeed if the class can be 'upcast', so if it inherits from what you're comparing it to..

classA instanceof classB

is true if classA is of a type inherited from classB

classA.getClass().isInstance(ClassB.class))

isInstance allows you to do it dynamically though
