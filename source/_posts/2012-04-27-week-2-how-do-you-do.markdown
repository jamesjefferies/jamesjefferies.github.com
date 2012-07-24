---
layout: post
title: !binary |-
  V2VlayAyIC0gaG93IGRvIHlvdSBkbw==
wordpress_id: 463
wordpress_url: !binary |-
  aHR0cDovL2phbWVzamVmZmVyaWVzLmNvbS8/cD00NjM=
date: 2012-04-27 17:18:59.000000000 +00:00
---
This week has all been about pairs of trousers. It has rained a lot and usually when you are equidistant from where you are going and where you want to go, the heavens open and you get absolutely soaked. I've been through three pairs of trousers and counting.

<img src="http://happenstanceproject.com/assets/wp-content/uploads/2012/04/rain-620x620.jpg" alt="rain" title="rain" width="620" height="620" class="alignnone size-large wp-image-383" />

So trousers.. and marketing/branding innovation labs, meeting with yet more interesting people, fixing the internet and eating flapjack.

To distract us from the weather and all these other things we've had the excitement of two receipt printers which we are bringing to life. The illustrious <a title="James Adam twitter" href="http://twitter.com/lazyatom">James Adam</a> has written a fantastic <a title="Hell Printer Article" href="http://gofreerange.com/hello-printer">article</a> about how to build internet enabled receipt printers. My advice would be to go away and read that, when you're done, come back here!

So we have been guinea pigs, taking delivery of two printers complete with special <a title="Arduino" href="http://www.arduino.cc/">arduino</a> kits, leads and other <a title="Gubbins" href="http://uncyclopedia.wikia.com/wiki/Gubbins">gubbins</a>. Of course, all we needed to do was plug them in (following the instructions) and BOOM! The little printers would burst in to life....

<img src="http://happenstanceproject.com/assets/wp-content/uploads/2012/04/heathcliff12-463x620.jpg" alt="" width="463" height="620" class="alignnone size-large wp-image-378" />

... except they did not :(

The little light flashed to say that it was talking to the internet, but the internet didn't want to speak back. This was a blow, was it the printer, was it the lead, was it the network, was it the circuitry, was it the 'sketch' (the arduino program)? So we put on our best Worzel Gummidge problem solving heads and got to work. We broke in to the server room and tried a direct connection (rather than through all the office switches and routers), fired up skype and waved the laptop in the direction of the kit whilst the illustrious one watched from afar. No joy.

We knew that one of the other tenants in the building used a different internet connection, so we took one of the printers up there and plugged it in. It burst into life and the backlog of messages we'd sent it arrived in a semi-orderly fashion, hurrah! We knew the printer, leads and circuitry worked, but why didn't it work on the other network? 

The next day the magic serial-USB debugging lead arrived and it was time to download the Arduino app and work out what on earth was happening. Once hooked up, the little bundle of electronic joy started telling us debug messages from the sketch.. which was nice, but it still didn't work. Time for some coding I thought. 

I don't think you can actually see what code is being run on the device as it is compiled in to assembler, so all I could do was add some further debugging information and upload it. I had some theories about the network too, what would happen if I put in the explicit IP address? Tweaked the URL it was using? Nothing, still didn't work. At this point I thought we may was well upload the <a href="https://github.com/freerange/printer/blob/master/printer.ino" title="Sketch">original sketch</a> with the relevant bits tweeted...

AND IT ONLY WENT AND WORKED!

Heathcliff lives...

<img src="http://happenstanceproject.com/assets/wp-content/uploads/2012/04/heathcliff31-620x620.jpg" alt="Heathcliff Lives" width="620" height="620" class="alignnone size-large wp-image-362" />

and after lunch, we got Cathy working too!

Next week we'll send them off to Wuthering Heights and see what happens..
