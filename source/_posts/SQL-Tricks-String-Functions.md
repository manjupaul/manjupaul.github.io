---
title: SQL Tricks - String Functions
date: 2016-09-16 10:05:01
categories:
- database
tags:
- SQL
- mysql
---
In this post I will go through few of the common string operations available in MySQL database. The examples here uses HR Schema. The post [SQL - Structured Query Language](../2015/SQL-Structured-Query-Language.html) has instructions about the schema.  Let us get started and look at the functions in detail.

### Concatenate
`concat` function returns the string that results from concatenating the arguments. In the example below, we are producing a json like structure.

```sql
select concat('{', 'FirstName:',  first_name, ', ' , 'LastName:', last_name , '}') as employee_json
from employees;
+-------------------------------------+
| employee_json                       |
+-------------------------------------+
| {FirstName:Steven, LastName:King}   |
| {FirstName:Neena, LastName:Kochhar} |
| {FirstName:Lex, LastName:De Haan}   |
+-------------------------------------+
3 rows in set (0.00 sec)

```

### Substring
The 'substr' function takes as argument a string, the starting position and optionally the length.

```sql
mysql> SELECT SUBSTRING('Quadratically',5);
+------------------------------+
| SUBSTRING('Quadratically',5) |
+------------------------------+
| ratically                    |
+------------------------------+
1 row in set (0.00 sec)

mysql> SELECT SUBSTRING('Quadratically',5,6);
+--------------------------------+
| SUBSTRING('Quadratically',5,6) |
+--------------------------------+
| ratica                         |
+--------------------------------+
1 row in set (0.00 sec)
```

### Substring Index
The `substring_index` function takes the `string` a `delimiter` and a `count`. Internally it will split the string based on the delimiter and return parts identified by the `count`.

```sql
mysql> SELECT SUBSTRING_INDEX('www.mysql.com.au', '.', 2);
+--------------------------------------------+
| SUBSTRING_INDEX('www.mysql.co.au', '.', 2) |
+--------------------------------------------+
| www.mysql                                  |
+--------------------------------------------+
1 row in set (0.00 sec)


mysql> SELECT SUBSTRING_INDEX('www.mysql.com.au', '.', -2);
+---------------------------------------------+
| SUBSTRING_INDEX('www.mysql.com.au', '.', -2) |
+---------------------------------------------+
| com.au                                       |
+---------------------------------------------+
1 row in set (0.00 sec)

```

### Length
The basic `length` function returns the total bytes in a string. The `char_length` function will return the number of characters in a string.
```sql
mysql> select first_name, length(first_name), char_length(first_name) from employees limit 3;
+------------+--------------------+-------------------------+
| first_name | length(first_name) | char_length(first_name) |
+------------+--------------------+-------------------------+
| Steven     |                  6 |                       6 |
| Neena      |                  5 |                       5 |
| Lex        |                  3 |                       3 |
+------------+--------------------+-------------------------+
3 rows in set (0.01 sec)
```