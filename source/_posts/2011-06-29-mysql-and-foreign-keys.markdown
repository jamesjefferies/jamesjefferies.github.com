---
comments: true
date: 2011-06-29 22:25:40
layout: post
slug: mysql-and-foreign-keys
title: MySQL and Foreign Keys
wordpress_id: 366
tags:
- link
- linkedin
- mysql
---

This is to remind me next time that MySQL isn’t as clever as you think it might be.

If you have Table A, with column 1, 2, 3 and Table B with columns 4, 5, 6 – Primary keys are columns 1 & 4 respectively.

Now you want to add a foreign key to table B, column 6, referencing column 1 in table A. No problem:

`ALTER TABLE tableB ADD CONSTRAINT fk_column_1 FOREIGN KEY (column6) REFERENCES tableA (column1);`

oh dear, fails with something like

`ERROR 1005 (HY000): Can't create table './databasename/#sql-55d1_b07.frm' (errno: 150)`

This fails because creating the primary key on columns 1 and 4 don’t automatically create indexes on those columns, and adding a foreign key requires there to be an index on the column you are referencing. Boom!
