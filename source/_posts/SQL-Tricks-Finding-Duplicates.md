---
title: SQL Tricks - Finding Duplicates
date: 2016-09-16 10:03:42
categories:
- database
tags:
- SQL
- PostgreSQL
---
In today's post I will be looking into few of the commonly used SQL queries and functions. To demonstrate the queries, we will using PostgreSQL database. In [Docker-PostgreSQL](Docker-PostgreSQL.md), I have outlined the steps to run a PostgreSQL container. You can execute the [pg_hr_schema.sql](pg_hr_schema.sql) to populate data used in these examples. <!-- more --> Additionally lets insert few records into `locations`.  

```
INSERT INTO locations VALUES 
        ( 4000 
        , 'Murtenstrasse 921'
        , '3095'
        , 'Bern'
        , 'BE'
        , 'CH'
        );

INSERT INTO locations VALUES 
        ( 4100 
        , 'Pieter Breughelstraat 837'
        , '3029SK'
        , 'Utrecht'
        , 'Utrecht'
        , 'NL'
        );

INSERT INTO locations VALUES 
        ( 4200 
        , 'Mariano Escobedo 9991'
        , '11932'
        , 'Mexico City'
        , 'Distrito Federal,'
        , 'MX'
        );



INSERT INTO locations VALUES 
        ( 5000 
        , 'Murtenstrasse 921'
        , '3095'
        , 'Bern'
        , 'BE'
        , 'CH'
        );

INSERT INTO locations VALUES 
        ( 5100 
        , 'Pieter Breughelstraat 837'
        , '3029SK'
        , 'Utrecht'
        , 'Utrecht'
        , 'NL'
        );

INSERT INTO locations VALUES 
        ( 5200 
        , 'Mariano Escobedo 9991'
        , '11932'
        , 'Mexico City'
        , 'Distrito Federal,'
        , 'MX'
        );        
```

### Finding Duplicates
 
 ```sql

select street_address, postal_code, city, state_province, country_id, count(*) as cnt
from locations 
group by street_address, postal_code, city, state_province, country_id
having count(*) > 1
 
 ```
 
 ### Deleting duplicates
 Now that we have found the rows which are duplicate, lets delete the duplicate rows. To achieve this we will use `ctid`, the system identifier on each row.
 
 ```sql
 
 delete from locations where ctid not in (
    select max(ctid) from locations 
    group by street_address, postal_code, city, state_province, country_id
 );

 ```
 What is `ctid` column ?
 > The physical location of the row version within its table. Note that although the ctid can be used to locate the row version very quickly, a row's ctid will change if it is updated or moved by VACUUM FULL. Therefore ctid is useless as a long-term row identifier. The OID, or even better a user-defined serial number, should be used to identify logical rows.