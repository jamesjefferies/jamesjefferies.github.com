---
layout: post
title: "Scenic Railways - our railway hack"
date: 2012-10-16 16:22
comments: true
published: true
categories:
- Techie
- Hackday
- Railways

tags:
- Techie
- Hackday
- Railways

---

![screen shot of application](/images/scenic-railways.png)

Thanks to the [Off The Rails](/2012/10/16/railway-hackday-off-the-rails/) hackday, I was able to team up with some fellow software engineers to build something in a day. Our team consisted of [Frankie Roberto](http://twitter.com/frankieroberto), [Jez Nicholson](http://twitter.com/jnicho02), and [Joe Hughes](http://twitter.com/joooe). Frankie had had the idea for building an application which would show sights of interest visible from the train route, indicating rough placements and which side of the train to look on. I knew Frankie from Sheffield, Frankie had worked with Jez before on a previous hackday and Joe was interested in what we were doing, our team was formed! 

Interestingly, during the 'speed dating' section at the beginning of the day, when we chatted to other people about their ideas and what they were thinking of building, one chap, whose name I think was Phil, was thinking about Railway iSpy, which sounds pretty similar to what we actually built (without Big Chief i-Spy though!). Our application also bears an uncanny similiarity to the Peppa Pig episode [The Train Ride!](http://www.youtube.com/watch?v=Htl6NYcBE-k)

After some discussion on ideas, scope, implementation and the [Railway Performance Society](http://www.railperf.org.uk/) we started building a Rails web application and an iOS app. Although I know a lot about railways, I'm still in the early days of learning Rails and iOS, so the patience of Jez and Frankie whilst building [Scenic Railways](http://www.scenicrailways.org.uk) was much appreciated. So whilst the three of us built the web application, Joe got cracking with building an iOS application. 

![ios-1](/images/scenic-railways-on-iphone.png)

We got an initial version built in the time we had (from about 11am until 7pm) before the presentations were due to start. I worked on a bit of map integration using [leaflet.js](http://leaflet.cloudmade.com) whilst Jez and Frankie implemented the main structure. 

Although the version we finished was relatively basic, there are some nice features, the best one being that the sides to look out of the window on, reverse depending on direction of travel!  It could easily be extended in the future to add extra routes and extra points of interest (POIs). Joe had some ideas on making the iOS app competitive, by providing incentives for people to take photos of the points from the train! 

![screen shot of application](/images/scenic-railways-1.png)

So, feel free to have a look at the site [Scenic Railways](http://www.scenicrailways.org.uk) and you can even checkout the code from [github](https://github.com/frankieroberto/scenic-railways) and laugh at my Rails code (or lack of it!).
