---
comments: false
date: 2008-05-06 10:26:59
layout: post
slug: ensuring-faces-spits-out-the-error-messages-when-developing
title: Ensuring faces spits out the error messages when developing
wordpress_id: 24
---

in the form view:

<h:messages></h:messages>

and in web.xml - switch facelets development on...

<context-param>
<param-name>facelets.DEVELOPMENT</param-name>
<param-value>true</param-value>
</context-param>
