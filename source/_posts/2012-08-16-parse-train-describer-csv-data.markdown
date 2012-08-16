---
layout: post
title: "Parse Train Describer CSV Data"
date: 2012-08-16 12:35
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
If you are using the Network Rail Open Data Feeds, then hopefully you've had a look at the fantastic [wiki](http://wiki.openraildata.info/index.php/TD_Berth_Steps) started by [poggs](http://twitter.com/poggs). 

In the reference data section, it provides a link to a CSV file which poggs is sharing containing Train Describer berths.

I wanted to parse that data using a simple ruby script and get it in to my mongo database. 

You can use the mongoimport program to pull in the CSV by adding a header file, or you can use this little ruby script I wrote (with a *lot* of help from this [snippet](http://www.dzone.com/snippets/turn-csv-headers-array-hashes)) which converts to JSON and inserts it in to the mongo db.

{% gist 3369575 %}


