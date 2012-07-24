---
layout: post
title: !binary |-
  QWRkaW5nIGEgbGluayBpbiBqYXZhc2NyaXB0
wordpress_id: 22
wordpress_url: !binary |-
  aHR0cDovL2phbWVzYW5kY2xhcmUubmV0L2xpZmUvP3A9MjI=
date: 2008-05-01 12:26:27.000000000 +00:00
---
thank you Jamie!

(but then I found this too with prototype)

$('container').update('&lt;a href="#" id="myclickid"&gt;text for link&lt;/a&gt;');

which will update a container called div and pop in the following stuff

&lt;div id="container"&gt;&lt;/div&gt;

should become

&lt;div id="container"&gt;&lt;a href="#" id="myclickid"&gt;text for link&lt;/a&gt;&lt;/div&gt;

function addLink() {
<pre>  var closeP = document.createElement("p");
closeP.appendChild(document.createTextNode("Alternatively, ");

var closeLink = document.createElement("a");
closeLink.href = "#";
closeLink.onclick = function() { window.close(); };
closeLink.appendChild(document.createTextNode("Close window"));
closeP.appendChild(closeLink);

var parentEl = document.getElementById("container");
// this should be the ID of the element this link should be appended to
parentEl.appendChild(closeP);
}

if (window.addEventListener) { window.addEventListener("load", addLink, false); }
else if (window.attachEvent) { window.attachEvent("onload", addLink); }</pre>
<p class="subpostmeta"></p>
<!-- You can start editing here. -->
