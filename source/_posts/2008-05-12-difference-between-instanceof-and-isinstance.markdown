---
comments: false
date: 2008-05-12 10:52:28
layout: post
slug: difference-between-instanceof-and-isinstance
title: Difference between instanceof and isInstance
wordpress_id: 26
---

f  you use instanceof or isInstance it will succeed if the class can be 'upcast', so if it inherits from what you're comparing it to..

classA instanceof classB

is true if classA is of a type inherited from classB

classA.getClass().isInstance(ClassB.class))

isInstance allows you to do it dynamically though
