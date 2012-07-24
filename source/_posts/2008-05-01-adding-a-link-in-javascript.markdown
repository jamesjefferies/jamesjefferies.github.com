---
comments: false
date: 2008-05-01 12:26:27
layout: post
slug: adding-a-link-in-javascript
title: Adding a link in javascript
wordpress_id: 22
categories:
- Oracle
---

thank you Jamie!

(but then I found this too with prototype)

$('container').update('<a href="#" id="myclickid">text for link</a>');

which will update a container called div and pop in the following stuff

<div id="container"></div>

should become

<div id="container"><a href="#" id="myclickid">text for link</a></div>

function addLink() {

    
      var closeP = document.createElement("p");
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
    else if (window.attachEvent) { window.attachEvent("onload", addLink); }






