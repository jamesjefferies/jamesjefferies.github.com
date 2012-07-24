---
comments: true
date: 2012-07-18 16:43:39
layout: post
slug: downloading-the-network-rail-schedules
title: Downloading the Network Rail Schedules
wordpress_id: 528
categories:
- Railways
- Techie
tags:
- Network Rail Datafeeds
- Open Data
- railways
---

As well as the live feeds which you can subscribe to for the Network Rail data, you can also download the Schedule feed which is delivered by Amazon S3. The Schedule feed is an extract of train schedules from the Integration Train Planning System.

When you have your Network Rail account you can subscribe, either to all the data, or to the Train Operators you are interested in. However, at the time of writing, the only feed which works is the one for ALL the data, the Train Operator specific downloads throw an unhelpful error


> HTTP Status 401 - User not subscribed to CIF_HL_FULL_DAILY


Which is a bit rubbish really. So my advice is, at this point to subscribe to ALL the data rather than just for one TOC. You can then access the feeds and download the zip file with either:

[https://datafeeds.networkrail.co.uk/ntrod/CifFileAuthenticate?type=CIF_ALL_FULL_DAILY&day=toc-full](https://datafeeds.networkrail.co.uk/ntrod/CifFileAuthenticate?type=CIF_ALL_FULL_DAILY&day=toc-full)

for the full feed or, say

[https://datafeeds.networkrail.co.uk/ntrod/CifFileAuthenticate?type=CIF_ALL_UPDATE_DAILY&day=toc-mon](https://datafeeds.networkrail.co.uk/ntrod/CifFileAuthenticate?type=CIF_ALL_UPDATE_DAILY&day=toc-mon)

for Monday's update.

Note that you will need to authenticate if you haven't already, using your username and password.
