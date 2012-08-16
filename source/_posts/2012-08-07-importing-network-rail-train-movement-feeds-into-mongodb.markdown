---
layout: post
title: "Importing Network Rail Train Movement feeds into MongoDB"
date: 2012-08-07 14:33
comments: true
categories:
- Railways
- Ruby
- Techie
- MongoDB
tags:
- Network Rail Datafeeds
- Open Data
- railways
- MongoDB

---
## Network Rail datafeeds?
Ah yes, please my previous [blog](http://jamesjefferies.com/2012/07/04/getting-started-with-network-rails-datafeeds/) post for further info, apologies for the lack of updates on here, I've been away, sent round the loop line.


## Why MongoDB?

[MongoDB](http://www.mongodb.org/) is a scalable, high-performance, open source, NoSQL database. I thought it would make a good fit for the train movement feeds as it's storage is oriented towards JSON-style documents. It's JSON-style because it actually uses [binary-encoded serialisation](http://bsonspec.org/) behind the scenes.

There is a nice little interactive tutorial on the MongoDB home page to get you in to the swing of things.

## Getting Mongo installed on OS X
I use [Homebrew](http://mxcl.github.com/homebrew/) for installing packaged stuff on to my Mac, if you use it, then you can easily install it with 

```
brew install mongodb
```

## What do you need for Ruby Mongo Magic?
There is a standard Mongo driver available, which you can install using gem
```
gem install mongo
```
but it is also worth installing the C compiled extension to speed up any BSON serialisation
``` 
gem install bson_ext
```

More info can be found on the [official pages](http://www.mongodb.org/display/DOCS/Ruby+Language+Center)

## Code example? 

Here you go, proper version in the [github repository](https://github.com/jamesjefferies/national-rail-datafeeds-ruby-examples)

{% gist 3285558 %}

## Examples of querying Mongo
There are lots of good examples and resources for using Mongo, but just a couple of examples related to the schema I've used in the example. You can fire up the interactive Mongo console and try the following (once you have some data!)

To retrieve all Departure events

```
db.td.find({ "body.event_type" : "DEPARTURE" })
```

To retrieve 10 (using limit) Train Movement (type 3) messages

```
db.td.find({ "header.msg_type" : "0003" }).limit(10)
```





