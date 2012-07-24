---
comments: true
date: 2010-06-08 13:44:01
layout: post
slug: why-has-my-jsf-button-stopped-working
title: Why has my JSF button stopped working..
wordpress_id: 388
tags:
- java
- jsf
---

I've asked this a number of times in the past, but I think I've  finally found the answer!

Often with JSF you may have a command  button wrapped in a div or subview rendered only in certain  circumstances.

    
    <f:subview id="show-the-button" rendered="#{managedBean.shouldButtonBeRendered}">
        <h:commandButton action="#{managedBean.doSomething}" value="Do Something" />
    </f:subview>


Ok, you might have some extra mark up in there, id etc, but this is  just to keep things simple for this example.

Now, for the button  to be rendered, the value of  managedBean.shouldButtonBeRendered should  be true when the page is being rendered, then the button appears.

However,  if between the page loading and the button being clicked, the value of  managedBean.shouldButtonBeRendered changes, then the button action is  ignored. Many hours of headaches would have been saved if I'd realised this sooner!

So, if you have a button which stops working under certain circumstances, check any rendering on the component or parent components!

More info can be found on the [sun forums](http://forums.sun.com/thread.jspa?threadID=5410200) and on [BalusC's](http://balusc.blogspot.com/2010/06/benefits-and-pitfalls-of-viewscoped.html) useful site
