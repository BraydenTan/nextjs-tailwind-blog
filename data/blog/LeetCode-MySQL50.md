---
title: LeetCode MySQL50
date: '2024-01-03'
tags: ['LeetCode', 'MySQL']
draft: false
summary: LeetCode MySQL50
images: ['/static/images/sql50.png']
layout: PostLayout
canonicalUrl: leetcode0001
---

# Part A (SELECT) 1-5

**1.(1757. Recyclable and Low Fat Products)**

```sql
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| product_id  | int     |
| low_fats    | enum    |
| recyclable  | enum    |
+-------------+---------+
--product_id is the primary key (column with unique values) for this table.
--low_fats is an ENUM (category) of type ('Y', 'N') where 'Y' means this product is low fat and 'N' means it is not.
--recyclable is an ENUM (category) of types ('Y', 'N') where 'Y' means this product is recyclable and 'N' means it is not.

Input:
Products table:
+-------------+----------+------------+
| product_id  | low_fats | recyclable |
+-------------+----------+------------+
| 0           | Y        | N          |
| 1           | Y        | Y          |
| 2           | N        | Y          |
| 3           | Y        | Y          |
| 4           | N        | N          |
+-------------+----------+------------+
Output:
+-------------+
| product_id  |
+-------------+
| 1           |
| 3           |
+-------------+
--Explanation: Only products 1 and 3 are both low fat and recyclable.

# Write your MySQL query statement below
select product_id from Products where low_fats = 'Y' and recyclable = 'Y';
```

**2.(584. Find Customer Referee)**

```sql
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| id          | int     |
| name        | varchar |
| referee_id  | int     |
+-------------+---------+
In SQL, id is the primary key column for this table.
Each row of this table indicates the id of a customer, their name, and the id of the customer who referred them.


Find the names of the customer that are not referred by the customer with id = 2.

Return the result table in any order.

The result format is in the following example.


Example 1:

Input:
Customer table:
+----+------+------------+
| id | name | referee_id |
+----+------+------------+
| 1  | Will | null       |
| 2  | Jane | null       |
| 3  | Alex | 2          |
| 4  | Bill | null       |
| 5  | Zack | 1          |
| 6  | Mark | 2          |
+----+------+------------+
Output:
+------+
| name |
+------+
| Will |
| Jane |
| Bill |
| Zack |
+------+

*Answer*
select name from Customer where referee_id <> 2 or referee_id is NULL;

```

**3.(595. Big Countries)**

```sql
A country is big if:

it has an area of at least three million (i.e., 3000000 km2), or
it has a population of at least twenty-five million (i.e., 25000000).
Write a solution to find the name, population, and area of the big countries.

Return the result table in any order.

The result format is in the following example.
Example 1:

Input:
World table:
+-------------+-----------+---------+------------+--------------+
| name        | continent | area    | population | gdp          |
+-------------+-----------+---------+------------+--------------+
| Afghanistan | Asia      | 652230  | 25500100   | 20343000000  |
| Albania     | Europe    | 28748   | 2831741    | 12960000000  |
| Algeria     | Africa    | 2381741 | 37100000   | 188681000000 |
| Andorra     | Europe    | 468     | 78115      | 3712000000   |
| Angola      | Africa    | 1246700 | 20609294   | 100990000000 |
+-------------+-----------+---------+------------+--------------+
Output:
+-------------+------------+---------+
| name        | population | area    |
+-------------+------------+---------+
| Afghanistan | 25500100   | 652230  |
| Algeria     | 37100000   | 2381741 |
+-------------+------------+---------+

# Answers
select
    name ,population , area
from
    World
where
    area >= 3000000 or population >= 25000000;

```

**4.(1148. Article Views I)**

```sql
Write a solution to find all the authors that viewed at least one of their own articles.

Return the result table sorted by id in ascending order.

The result format is in the following example.


Example 1:

Input:
Views table:
+------------+-----------+-----------+------------+
| article_id | author_id | viewer_id | view_date  |
+------------+-----------+-----------+------------+
| 1          | 3         | 5         | 2019-08-01 |
| 1          | 3         | 6         | 2019-08-02 |
| 2          | 7         | 7         | 2019-08-01 |
| 2          | 7         | 6         | 2019-08-02 |
| 4          | 7         | 1         | 2019-07-22 |
| 3          | 4         | 4         | 2019-07-21 |
| 3          | 4         | 4         | 2019-07-21 |
+------------+-----------+-----------+------------+
Output:
+------+
| id   |
+------+
| 4    |
| 7    |
+------+
--Answer

SELECT DISTINCT
    author_id AS id
FROM
    Views
WHERE
    author_id = viewer_id
ORDER BY
    id ;
```

**5.(1683. Invalid Tweets)**

```sql
Write a solution to find the IDs of the invalid tweets.
The tweet is invalid if the number of characters used in the
 content of the tweet is strictly greater than 15.

Return the result table in any order.

The result format is in the following example.



Example 1:

Input:
Tweets table:
+----------+----------------------------------+
| tweet_id | content                          |
+----------+----------------------------------+
| 1        | Vote for Biden                   |
| 2        | Let us make America great again! |
+----------+----------------------------------+
Output:
+----------+
| tweet_id |
+----------+
| 2        |
+----------+
Explanation:
Tweet 1 has length = 14. It is a valid tweet.
Tweet 2 has length = 32. It is an invalid tweet.

--Answer
SELECT tweet_id FROM Tweets WHERE CHAR_LENGTH(content) > 15;
```

# Part B (BASIC JOIN) 6-14

**6.(1378. Replace Employee ID With The Unique Identifier)**

```sql
Write a solution to show the unique ID of each user,
If a user does not have a unique ID replace just show null.

Return the result table in any order.

The result format is in the following example.

Example 1:

Input:
Employees table:
+----+----------+
| id | name     |
+----+----------+
| 1  | Alice    |
| 7  | Bob      |
| 11 | Meir     |
| 90 | Winston  |
| 3  | Jonathan |
+----+----------+
EmployeeUNI table:
+----+-----------+
| id | unique_id |
+----+-----------+
| 3  | 1         |
| 11 | 2         |
| 90 | 3         |
+----+-----------+
Output:
+-----------+----------+
| unique_id | name     |
+-----------+----------+
| null      | Alice    |
| null      | Bob      |
| 2         | Meir     |
| 3         | Winston  |
| 1         | Jonathan |
+-----------+----------+
Explanation:
Alice and Bob do not have a unique ID, We will show null instead.
The unique ID of Meir is 2.
The unique ID of Winston is 3.
The unique ID of Jonathan is 1.

--Answer
SELECT
    Employees.name ,EmployeeUNI.unique_id
FROM
    Employees
LEFT JOIN
    EmployeeUNI
ON
    Employees.id = EmployeeUNI.id;
```

**7.(1068. Product Sales Analysis I)**

```sql
Write a solution to report the product_name, year, and price for each sale_id in the Sales table.

Return the resulting table in any order.

The result format is in the following example.



Example 1:

Input:
Sales table:
+---------+------------+------+----------+-------+
| sale_id | product_id | year | quantity | price |
+---------+------------+------+----------+-------+
| 1       | 100        | 2008 | 10       | 5000  |
| 2       | 100        | 2009 | 12       | 5000  |
| 7       | 200        | 2011 | 15       | 9000  |
+---------+------------+------+----------+-------+
Product table:
+------------+--------------+
| product_id | product_name |
+------------+--------------+
| 100        | Nokia        |
| 200        | Apple        |
| 300        | Samsung      |
+------------+--------------+
Output:
+--------------+-------+-------+
| product_name | year  | price |
+--------------+-------+-------+
| Nokia        | 2008  | 5000  |
| Nokia        | 2009  | 5000  |
| Apple        | 2011  | 9000  |
+--------------+-------+-------+
Explanation:
From sale_id = 1, we can conclude that Nokia was sold for 5000 in the year 2008.
From sale_id = 2, we can conclude that Nokia was sold for 5000 in the year 2009.
From sale_id = 7, we can conclude that Apple was sold for 9000 in the year 2011.

--Answer
SELECT
    Product.product_name , Sales.year , Sales.price
FROM
    Sales
LEFT JOIN
    Product
ON
    Product.product_id = Sales.product_id;
```

**8.(1581. Customer Who Visited but Did Not Make Any Transactions)**

```sql
Write a solution to find the IDs of the users who visited without
making any transactions and the number of times they made these types of visits.
Return the result table sorted in any order.
The result format is in the following example.
Example 1:

Input:
Visits
+----------+-------------+
| visit_id | customer_id |
+----------+-------------+
| 1        | 23          |
| 2        | 9           |
| 4        | 30          |
| 5        | 54          |
| 6        | 96          |
| 7        | 54          |
| 8        | 54          |
+----------+-------------+
Transactions
+----------------+----------+--------+
| transaction_id | visit_id | amount |
+----------------+----------+--------+
| 2              | 5        | 310    |
| 3              | 5        | 300    |
| 9              | 5        | 200    |
| 12             | 1        | 910    |
| 13             | 2        | 970    |
+----------------+----------+--------+
Output:
+-------------+----------------+
| customer_id | count_no_trans |
+-------------+----------------+
| 54          | 2              |
| 30          | 1              |
| 96          | 1              |
+-------------+----------------+
Explanation:
Customer with id = 23 visited the mall once and made one transaction during the visit with id = 12.
Customer with id = 9 visited the mall once and made one transaction during the visit with id = 13.
Customer with id = 30 visited the mall once and did not make any transactions.
Customer with id = 54 visited the mall three times. During 2 visits they did not make any transactions, and during one visit they made 3 transactions.
Customer with id = 96 visited the mall once and did not make any transactions.
As we can see, users with IDs 30 and 96 visited the mall one time without making any transactions.
Also, user 54 visited the mall twice and did not make any transactions.

--Thought for Answer
SELECT * FROM Visits v LEFT JOIN Transactions t ON v.visit_id = t.visit_id;

| visit_id | customer_id | transaction_id | visit_id | amount |
| -------- | ----------- | -------------- | -------- | ------ |
| 1        | 23          | 12             | 1        | 910    |
| 2        | 9           | 13             | 2        | 970    |
| 4        | 30          | null           | null     | null   |
| 5        | 54          | 9              | 5        | 200    |
| 5        | 54          | 3              | 5        | 300    |
| 5        | 54          | 2              | 5        | 310    |
| 6        | 96          | null           | null     | null   |
| 7        | 54          | null           | null     | null   |
| 8        | 54          | null           | null     | null   |

--So which mean , we need to find the record with null
--we can
SELECT customer_id, count(customer_id) count_no_trans
FROM Visits v
LEFT JOIN transactions t
ON v.visit_id = t.visit_id
WHERE transaction_id IS NULL
GROUP BY customer_id;

--or solution without JOIN any table but using NOT IN

SELECT customer_id,count(visit_id) as count_no_trans
FROM Visits
WHERE visit_id not in (SELECT DISTINCT visit_id FROM Transactions)
GROUP BY customer_id
```

**9.(197. Rising Temperature)**

```sql
/*Write a solution to find all dates' Id with higher temperatures
compared to its previous dates (yesterday).
Return the result table in any order.
The result format is in the following example.*/

/*Example 1:
Input:
Weather table:*/
+----+------------+-------------+
| id | recordDate | temperature |
+----+------------+-------------+
| 1  | 2015-01-01 | 10          |
| 2  | 2015-01-02 | 25          |
| 3  | 2015-01-03 | 20          |
| 4  | 2015-01-04 | 30          |
+----+------------+-------------+
Output:
+----+
| id |
+----+
| 2  |
| 4  |
+----+
/*Explanation:
In 2015-01-02, the temperature was higher than the previous day (10 -> 25).
In 2015-01-04, the temperature was higher than the previous day (20 -> 30).*/

--Answer（Self Join Method）
--First if
SELECT *
FROM Weather a
JOIN Weather b
ON DATEDIFF(a.recordDate, b.recordDate) = 1
;
| id | recordDate | temperature | id | recordDate | temperature |
| -- | ---------- | ----------- | -- | ---------- | ----------- |
| 2  | 2015-01-02 | 25          | 1  | 2015-01-01 | 10          |
| 3  | 2015-01-03 | 20          | 2  | 2015-01-02 | 25          |
| 4  | 2015-01-04 | 30          | 3  | 2015-01-03 | 20          |

--in the end add condition which is temperature a > temperature b

SELECT a.id
FROM Weather a
JOIN Weather b
ON DATEDIFF(a.recordDate, b.recordDate) = 1
WHERE a.Temperature > b.Temperature;

--Correct Answer:
+----+
| id |
+----+
| 2  |
| 4  |
+----+



```

**10.(1661. Average Time of Process per Machine)**

```sql
--There is a factory website that has several machines each running the same number of processes.
--Write a solution to find the average time each machine takes to complete a process.
--The time to complete a process is the 'end' timestamp minus the 'start' timestamp.
--The average time is calculated by the total time to complete every process on the machine divided by the number of processes that were run.
--The resulting table should have the machine_id along with the average time as processing_time, which should be rounded to 3 decimal places.

--Return the result table in any order.
--The result format is in the following example.

--Example 1:

--Input:
--Activity table:
+------------+------------+---------------+-----------+
| machine_id | process_id | activity_type | timestamp |
+------------+------------+---------------+-----------+
| 0          | 0          | start         | 0.712     |
| 0          | 0          | end           | 1.520     |
| 0          | 1          | start         | 3.140     |
| 0          | 1          | end           | 4.120     |
| 1          | 0          | start         | 0.550     |
| 1          | 0          | end           | 1.550     |
| 1          | 1          | start         | 0.430     |
| 1          | 1          | end           | 1.420     |
| 2          | 0          | start         | 4.100     |
| 2          | 0          | end           | 4.512     |
| 2          | 1          | start         | 2.500     |
| 2          | 1          | end           | 5.000     |
+------------+------------+---------------+-----------+
Output:
+------------+-----------------+
| machine_id | processing_time |
+------------+-----------------+
| 0          | 0.894           |
| 1          | 0.995           |
| 2          | 1.456           |
+------------+-----------------+
/*Explanation:
There are 3 machines running 2 processes each.
Machine 0's average time is ((1.520 - 0.712) + (4.120 - 3.140)) / 2 = 0.894
Machine 1's average time is ((1.550 - 0.550) + (1.420 - 0.430)) / 2 = 0.995
Machine 2's average time is ((4.512 - 4.100) + (5.000 - 2.500)) / 2 = 1.456 */

--Answer 1 (Runtime: 249 ms)
SELECT
    a1.machine_id,
    ROUND(AVG(a2.timestamp -a1.timestamp),3) AS processing_time
FROM
    Activity AS a1 JOIN Activity AS a2 ON
    a1.machine_id=a2.machine_id AND
    a1.process_id=a2.process_id AND
    a1.activity_type ='start' AND a2.activity_type ='end'
    GROUP BY machine_id;

```
