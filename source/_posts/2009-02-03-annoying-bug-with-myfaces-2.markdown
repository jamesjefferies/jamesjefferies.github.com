---
comments: false
date: 2009-02-03 09:42:52
layout: post
slug: annoying-bug-with-myfaces-2
title: Annoying Bug with MyFaces
wordpress_id: 129
tags:
- MyFaces Java Stupid Error
---

So I reckon I've spent over an hour wrestling with this chuffer....

Simple search button on a page using Tomahawk Data Table to render the output. Page would render first time out, but then using the search button resulted in the following error

   
``` java 
    java.lang.NoSuchMethodError: org.apache.myfaces.component.html.ext.HtmlDataTable.refresh(Ljavax/faces/context/FacesContext;)
``` 


Looks like there might be a problem rendering the data table doesn't it. Well, I thought I'd made a chimpolata mistake somewhere down the line... and I had, but nothing to do with the table....

The last thing the search method did was return a string to tell MyFaces where to navigate to next. Like a complete chump, at some point I'd removed the config from the faces navigation xml to tell it which page that string referred to.

Consequently, rather than saying something like

    
    Navigation failure you numpty, couldn't find "list-applicants"


it came up with the other error... Thanks MyFaces, you're really helpful







