---
title: SQL Tricks - Date Functions
date: 2016-05-23 09:04:51
categories:
- database
tags:
- SQL
- postgresql
---
In this post I will go through few of the common date operations available in PostgreSQL database. The examples here uses HR Schema. The post [SQL Tricks - Finding Duplicates](../2016/SQL-Tricks-Finding-Duplicates.html) has instructions about the schema.  Let us get started and look at the functions in detail.

### CURRENT DATE/TIME()
The `CURRENT DATE/TIME` function returns current date/time. 
Examples :

```sql
SELECT current_time;
timetz
------
 "15:06:23.003683+00"
(1 row)
```

```sql
SELECT current_date;
date
----
2015-05-05
(1 row)
```

```sql
SELECT current_timestamp;
now
---
2016-05-05 08:01:45.375+05:30
(1 row)
```

```sql
SELECT date_part('day', TIMESTAMP '2016-05-05 08:01:45.375+05:30');
day
---
5 
(1 row)
```

### AGE()
The `AGE()`function used to retrieves subtracts arguments from current date and date as specified in the argument.
Examples
```sql
SELECT age(timestamp '2007-10-07');  
   age
-----------------------
 7 years 3 mons 7 days
(1 row)
```
The `AGE(timestamp, timestamp)` function used to retrieves the age between two date specified in the argument.

```sql
SELECT age(timestamp '2015-01-15', timestamp '1972-12-28');
    age
------------------
 42 years 18 days
(1 row)
```

### EXTRACT()

The extract function is used to retrieves subfields such as year or hour from date/time values.
EXTRACT(field from timestamp)
```sql
SELECT extract(hour from timestamp '20015-09-17 20:27:45'); 
 
 date_part
-----------
        20
(1 row)
```
```sql
SELECT extract(day from timestamp '2015-02-16 20:38:40');
 date_part
-----------
        16
(1 row)
```
### ISFINITE()
The isfinite() function is used to get test for finite date,time and interval.

```sql
SELECT isfinite(date '2015-04-16');
 isfinite
----------
 t
(1 row)

SELECT isfinite(interval '7 hours'); 
 isfinite
----------
 t
(1 row)

SELECT isfinite(timestamp '2015-04-16 21:30:30');
 isfinite
----------
 t
(1 row)
```
### JUSTIFY()

 JUSTIFY_DAYS(interval) function is used to adjust the  interval so 30-day time periods are represented as months.
 ```sql
  SELECT justify_days(interval '45 days');
 justify_days
 --------------
  1 mon 15 days
 (1 row)
 SELECT justify_hours(interval '28 hours');
    justify_hours
   ----------------
    1 day 04:00:00
   (1 row)
   
   SELECT justify_interval(interval '1 mon -2 hour');
    justify_interval
   ------------------
    29 days 22:00:00
 ```
 
 
