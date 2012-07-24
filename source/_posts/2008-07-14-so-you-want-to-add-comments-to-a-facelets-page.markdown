---
comments: false
date: 2008-07-14 14:15:55
layout: post
slug: so-you-want-to-add-comments-to-a-facelets-page
title: So you want to add comments to a facelets page?
wordpress_id: 32
---

Simple, use the remove tag. This gets stripped out very early on and will not be rendered.

<ui:remove>
This is a comment basically, will get stripped out when facelets sorts out the templates...
</ui:remove>
