---
layout: post
title: !binary |-
  V2h5IGhhcyBteSBKU0YgYnV0dG9uIHN0b3BwZWQgd29ya2luZy4u
wordpress_id: 388
wordpress_url: !binary |-
  aHR0cDovL2phbWVzamVmZmVyaWVzLmNvbS8/cD0zODg=
date: 2010-06-08 13:44:01.000000000 +00:00
---
I've asked this a number of times in the past, but I think I've  finally found the answer!

Often with JSF you may have a command  button wrapped in a div or subview rendered only in certain  circumstances.
<pre>&lt;f:subview id="show-the-button" rendered="#{managedBean.shouldButtonBeRendered}"&gt;
    &lt;h:commandButton action="#{managedBean.doSomething}" value="Do Something" /&gt;
&lt;/f:subview&gt;</pre>
Ok, you might have some extra mark up in there, id etc, but this is  just to keep things simple for this example.

Now, for the button  to be rendered, the value of  managedBean.shouldButtonBeRendered should  be true when the page is being rendered, then the button appears.

However,  if between the page loading and the button being clicked, the value of  managedBean.shouldButtonBeRendered changes, then the button action is  ignored. Many hours of headaches would have been saved if I'd realised this sooner!

So, if you have a button which stops working under certain circumstances, check any rendering on the component or parent components!

More info can be found on the <a href="http://forums.sun.com/thread.jspa?threadID=5410200">sun forums</a> and on <a href="http://balusc.blogspot.com/2010/06/benefits-and-pitfalls-of-viewscoped.html">BalusC's</a> useful site
