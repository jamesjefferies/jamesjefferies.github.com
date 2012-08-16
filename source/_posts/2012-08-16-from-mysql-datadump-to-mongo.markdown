---
layout: post
title: "From MySQL datadump to mongo"
date: 2012-08-16 14:42
comments: true
categories:
- Ruby
- Techie
- MongoDB
tags:
- MongoDB

---
Let us say that you have a MySQL dump of  a database table, with a load of data which ideally, you'd like to pull into a Mongo DB as json.

What you could do is…

## Import data in to MySQL database

Usual kind of thing here, assuming you have a MySQL username for a created database:

```
mysql -uusername -p -Ddbname < mysqldumpfile.sql
```

## Export data from MySQL database in json format

There is a cracking ruby gem [mysql2xxxx](https://github.com/seamusabshere/mysql2xxxx) which will export from a mysql database to various formats, including json.

You can drive it via code or a number of binaries are provided. So:

```
mysql2json --user=username --password=password --database=dbname --execute="select * from my_special_table" > my_special_file.json
```

## Importing the json straight in to your mongodb

Then you can use mongoimport to pull in the json. If your export from ```mysql2json``` is surrounded by the square brackets, you'll need the ```--jsonArray``` option. Your command will need to be something like:


```
mongoimport --type json --file my_special_file.json --collection mycollection --db mymongodb --jsonArray
```

## Summary

Simple three step transformation from MySQL dump to Mongo. You may know a better, more straightforward way of doing this, please add a comment if you do!
