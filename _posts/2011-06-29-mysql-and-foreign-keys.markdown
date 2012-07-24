---
layout: post
title: !binary |-
  TXlTUUwgYW5kIEZvcmVpZ24gS2V5cw==
wordpress_id: 366
wordpress_url: !binary |-
  aHR0cDovL2phbWVzamVmZmVyaWVzLmNvbS8/cD0zNjY=
date: 2011-06-29 22:25:40.000000000 +00:00
---
This is to remind me next time that MySQL isn’t as clever as you think it might be.

If you have Table A, with column 1, 2, 3 and Table B with columns 4, 5, 6 – Primary keys are columns 1 & 4 respectively.

Now you want to add a foreign key to table B, column 6, referencing column 1 in table A. No problem:

<code>ALTER TABLE tableB ADD CONSTRAINT fk_column_1 FOREIGN KEY (column6) REFERENCES tableA (column1);</code>

oh dear, fails with something like

<code>ERROR 1005 (HY000): Can't create table './databasename/#sql-55d1_b07.frm' (errno: 150)</code>

This fails because creating the primary key on columns 1 and 4 don’t automatically create indexes on those columns, and adding a foreign key requires there to be an index on the column you are referencing. Boom!
