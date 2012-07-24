---
layout: post
title: !binary |-
  RmxpY2tyIGFuZCB0aGUgbWlzc2luZyBpbWFnZXM=
wordpress_id: 370
wordpress_url: !binary |-
  aHR0cDovL2phbWVzamVmZmVyaWVzLmNvbS8/cD0zNzA=
date: 2011-08-18 16:10:08.000000000 +00:00
---
A client got in touch with a weird problem, when logging in to flickr, some images wouldn't download, the placeholders would be there with the classic little red cross indicating a problem.
<h3>Idea 1 - funny URLs</h3>
Thinking that something must be going wrong with the content delivery for those pictures, the farm was down or whatever, I asked him to send through the direct URL, plus to try accessing it himself. Well, usually it didn't work, but sometimes, if he right clicked and asked the browser to download the image it did. Curious.
<h3>Idea 2 - browsers</h3>
Ok, well, maybe it's just the browser messing up with its security levels. Nope, still the same on Safari, Chrome &amp; Firefox.
<h3>Idea 3 - DNS</h3>
Maybe the DNS is being bodged up for those server farms. Try google DNS - no joy. Try flushing Windows DNS cache - no joy.
<h3>Idea 4 - Firefox's exception list</h3>
This is where I found out about <a title="Flickr test page" href="http://www.flickr.com/help/test">Flickr's test page </a> which is useful for trouble shooting this stuff. Apparently all the global column didn't load on a clean firefox install. So we added farm1 to firefox's image exception list. Boom, they all came back.. bizarre.
<h3>Idea 5 - Conflict with security software</h3>
The machine was XP SP 3 with AVG internet security installed. After a further prod around, Ad-aware was on there, as was McAfee. So, here's an idea, boot in to safe mode with networking and see if that works... Hmm, nope.
<h3>Idea 6 - Must be unrelated to the computer, belkin router anyone?</h3>
Surely the ISP wouldn't be messing about here... but what about the router. A belkin apparently, which is when I found a <a title="flickr forum thread" href="http://www.flickr.com/help/forum/72157627085259789/">flickr forum thread</a> of people with the same problem. Ah, belkin routers - this is starting to make sense. Believe it or not, switching off the router firewall (whilst maintaining a software firewall on the PC) meant that the images downloaded without a problem. Argh! It was the router all along. It seemed so obscure.
<h3>In a nutshell</h3>
If you are having problems with flickr (or other image intensive sites) and you have a belkin router with the firewall switched on. SWITCH it off and see if it fixes it. If it does - bingo!
