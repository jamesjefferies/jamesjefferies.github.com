---
comments: true
date: 2012-07-04 22:46:41
layout: post
slug: getting-started-with-network-rails-datafeeds
title: Getting started with Network Rail's datafeeds
wordpress_id: 509
categories:
- Railways
- Ruby
- Techie
tags:
- Network Rail Datafeeds
- Open Data
- railways
---

I've had a few railway project ideas knocking around for ages now, but have had a couple of blockers which have meant they have not progressed. Mainly lack of time and lack of data! I'm therefore clearing the decks for July and August to spend some decent time working on these ideas, which also co-incides with Network Rail giving access to a new platform providing live data feeds. You may have heard about [the launch](http://www.techweekeurope.co.uk/news/network-rail-open-data-feeds-83128), I believe the platform was developed in conjunction with [Rockshore](http://rockshore.net/), well, it's what this [tweet](https://twitter.com/rockshoreltd/status/218323058493108224) says anyway.


## Where do you start?


If you are interested in using the datafeeds yourself, you can read all about it on [Network Rail's site](http://www.networkrail.co.uk/data-feeds/) which also has a link to download the developer's guide in PDF format.

First, you need to [create an account](https://datafeeds.networkrail.co.uk/ntrod/login) - I believe there are limited numbers of accounts going at the moment, so the sooner you do that, the better.

There are two types of feeds available, pub/sub using the stomp protocol for real-ish time data & downloads of huge files from Amazon S3 for timetables etc.

Once your account is active, you can subscribe to any of the pub/sub datafeeds you like and away you go.


## Receiving Messages


I decided that I was going to try accessing the pub/sub datafeeds using Ruby (not my usual language) and put my experimental code on to my git hub account. Feel free to [have a look and check it out](https://github.com/jamesjefferies/national-rail-datafeeds-ruby-examples), I'll be using it for my initial experiments, so it should get updated beyond this basic example!

I've also included a sample, no error checking, very straightforward listener below. If you wish to try and run it, then you will of course need Ruby and Ruby gems installed, plus the stomp ruby gem.

Then, you just need to ensure your username and password are set as the relevant environment variables and away you go.

All being well, you should slowly receive updates from the topic you have selected. The example below uses Train positioning data for the East Midlands (TD_MC_EM_SIG_AREA) and assumes that you have subscribed to that feed using the [network rail control panel](https://datafeeds.networkrail.co.uk/ntrod/myFeeds)

The updates you receive from this program are not formatted at all, it's just sending the message straight to string. Of course, this is just helping you know you're set up correctly. So you would get something like:


``` ruby
<Stomp::Message headers={"message-id"=>"ID:blahblah", "destination"=>"/topic/TD_MC_EM_SIG_AREA", "timestamp"=>"1341436026840", "expires"=>"1341436326840", "persistent"=>"true", "priority"=>"4"} body='[{"CA_MSG":{"to":"1234","time":"1341435963000","area_id":"WH","msg_type":"CA","from":"5678","descr":"1Z99"}}]' command='MESSAGE' >
```


Ultimately of course, you'd process the JSON from the body and do something with it.


## Example Ruby Listener


``` ruby
require 'rubygems'
require 'stomp'

begin
  # Credentials set here as environment variables
  @user = ENV["DATAFEEDS_USER"];
  @password = ENV["DATAFEEDS_PASSWORD"]
  @host = "datafeeds.networkrail.co.uk"
  @port = 61618

  # Example destination add yours here
  @destination = "/topic/TD_MC_EM_SIG_AREA"

  puts "Connecting to datafeeds as #{@user} using stomp protocol stomp://#{@host}:#{@port}\n"
  @connection = Stomp::Connection.open @user, @password, @host, @port, true
  @connection.subscribe @destination

  while true
    @msg = @connection.receive
    puts @msg
  end
  @connection.disconnect
rescue
end
```
