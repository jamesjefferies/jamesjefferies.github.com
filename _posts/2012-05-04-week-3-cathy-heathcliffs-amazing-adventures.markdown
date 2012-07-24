---
layout: post
title: !binary |-
  V2VlayAzIC0gQ2F0aHkgJmFtcDsgSGVhdGhjbGlmZidzIGFtYXppbmcgYWR2
  ZW50dXJlcw==
wordpress_id: 466
wordpress_url: !binary |-
  aHR0cDovL2phbWVzamVmZmVyaWVzLmNvbS8/cD00NjY=
date: 2012-05-04 17:18:34.000000000 +00:00
---
This week has given us a real opportunity to do something interesting with Cathy &amp; Heathcliff, we spent two of our three days out of the Site office to get our heads down.

The first challenge was to allow 6th Formers to send messages to Cathy &amp; Heathcliff. At first we thought of hooking them up directly to twitter accounts, but as Leila had a <a title="Twilio" href="http://twilio.com">Twilio</a> account, it meant that we could do something clever with SMS Text messages. With a bit of PHP magic on an intermediary server (timescales demanded a quick turnaround!) we managed to get the SMS messages sent to the two printers. Hooray!

The next step was to bypass the button on the Arduino device which you had to push each time a message arrived. We edited the C code and uploaded the new code to the devices so that instead of waiting for the button to be pushed, the green light flashed and it printed without intervention. Hooray x 2!

Finally, we wanted to get the messages sent to Cathy and Heathcliff's twitter accounts - @CathyPrinter @HeathcliffPrinter - initially we looked a using the PHP OAuth libraries to authenticate and send the message to twitter, but as neither of us are particularly adept at PHP, we decided on a different solution. Using <a href="http://ifttt.com">If This Then That</a> and some server side magic, we send an email from the server, via their gmail accounts to If This Then That, which then passes them on to their twitter accounts.. Hooray x 3!

You can see us setting them up on our <a title="Happenstance Sheffield" href="http://happenstancesheffield.tumblr.com">tumblr site</a>.
