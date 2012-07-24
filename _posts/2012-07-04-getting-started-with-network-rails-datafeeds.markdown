---
layout: post
title: !binary |-
  R2V0dGluZyBzdGFydGVkIHdpdGggTmV0d29yayBSYWlsJ3MgZGF0YWZlZWRz
wordpress_id: 509
wordpress_url: !binary |-
  aHR0cDovL2phbWVzamVmZmVyaWVzLmNvbS8/cD01MDk=
date: 2012-07-04 22:46:41.000000000 +00:00
---
I've had a few railway project ideas knocking around for ages now, but have had a couple of blockers which have meant they have not progressed. Mainly lack of time and lack of data! I'm therefore clearing the decks for July and August to spend some decent time working on these ideas, which also co-incides with Network Rail giving access to a new platform providing live data feeds. You may have heard about <a title="Techweek europe story" href="http://www.techweekeurope.co.uk/news/network-rail-open-data-feeds-83128">the launch</a>, I believe the platform was developed in conjunction with <a href="http://rockshore.net/">Rockshore</a>, well, it's what this <a title="Rockshore tweet" href="https://twitter.com/rockshoreltd/status/218323058493108224">tweet</a> says anyway.
<h2>Where do you start?</h2>
If you are interested in using the datafeeds yourself, you can read all about it on <a href="http://www.networkrail.co.uk/data-feeds/">Network Rail's site</a> which also has a link to download the developer's guide in PDF format.

First, you need to <a href="https://datafeeds.networkrail.co.uk/ntrod/login">create an account</a> - I believe there are limited numbers of accounts going at the moment, so the sooner you do that, the better.

There are two types of feeds available, pub/sub using the stomp protocol for real-ish time data &amp; downloads of huge files from Amazon S3 for timetables etc.

Once your account is active, you can subscribe to any of the pub/sub datafeeds you like and away you go.
<h2>Receiving Messages</h2>
I decided that I was going to try accessing the pub/sub datafeeds using Ruby (not my usual language) and put my experimental code on to my git hub account. Feel free to <a title="git hub" href="https://github.com/jamesjefferies/national-rail-datafeeds-ruby-examples">have a look and check it out</a>, I'll be using it for my initial experiments, so it should get updated beyond this basic example!

I've also included a sample, no error checking, very straightforward listener below. If you wish to try and run it, then you will of course need Ruby and Ruby gems installed, plus the stomp ruby gem.

Then, you just need to ensure your username and password are set as the relevant environment variables and away you go.

All being well, you should slowly receive updates from the topic you have selected. The example below uses Train positioning data for the East Midlands (TD_MC_EM_SIG_AREA) and assumes that you have subscribed to that feed using the <a href="https://datafeeds.networkrail.co.uk/ntrod/myFeeds">network rail control panel</a>

The updates you receive from this program are not formatted at all, it's just sending the message straight to string. Of course, this is just helping you know you're set up correctly. So you would get something like:

[code]

&lt;Stomp::Message headers={&quot;message-id&quot;=&gt;&quot;ID:blahblah&quot;, &quot;destination&quot;=&gt;&quot;/topic/TD_MC_EM_SIG_AREA&quot;, &quot;timestamp&quot;=&gt;&quot;1341436026840&quot;, &quot;expires&quot;=&gt;&quot;1341436326840&quot;, &quot;persistent&quot;=&gt;&quot;true&quot;, &quot;priority&quot;=&gt;&quot;4&quot;} body='[{&quot;CA_MSG&quot;:{&quot;to&quot;:&quot;1234&quot;,&quot;time&quot;:&quot;1341435963000&quot;,&quot;area_id&quot;:&quot;WH&quot;,&quot;msg_type&quot;:&quot;CA&quot;,&quot;from&quot;:&quot;5678&quot;,&quot;descr&quot;:&quot;1Z99&quot;}}]' command='MESSAGE' &gt;

[/code]

Ultimately of course, you'd process the JSON from the body and do something with it.
<h2>Example Ruby Listener</h2>
[ruby]
require 'rubygems'
require 'stomp'

begin
  # Credentials set here as environment variables
  @user = ENV[&quot;DATAFEEDS_USER&quot;];
  @password = ENV[&quot;DATAFEEDS_PASSWORD&quot;]
  @host = &quot;datafeeds.networkrail.co.uk&quot;
  @port = 61618

  # Example destination add yours here
  @destination = &quot;/topic/TD_MC_EM_SIG_AREA&quot;

  puts &quot;Connecting to datafeeds as #{@user} using stomp protocol stomp://#{@host}:#{@port}\n&quot;
  @connection = Stomp::Connection.open @user, @password, @host, @port, true
  @connection.subscribe @destination

  while true
    @msg = @connection.receive
    puts @msg
  end
  @connection.disconnect
rescue
end
[/ruby]
