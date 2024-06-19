# Learning Pro SQL
Learn Pro SQL using PostgreSQL through pgAdmin
Following helped me built this guide:
1. Jose Portilla Udemy Course [The Complete SQL Bootcamp: Go from Zero to Hero](https://www.udemy.com/course/the-complete-sql-bootcamp)

## Table of Contents
1. [Installation](#installation)
2. [Populate Database](#populate-database)
3. [SQL Commands And Keywords](#sql-commands-and-keywords)

## Installation
1. Go to the following link to download the PostgreSQL

    `https://www.enterprisedb.com/downloads/postgres-postgresql-downloads`

    Note: Remember the password you set for the PostgreSQL superuser (postgres).

2. If you need to install the pgAdmin, you may use following link

    `https://www.pgadmin.org/download/`

3. Open pgAdmin and you may need to enter password for pgAdmin for the first time.

4. Then connect with PostgreSQL server by entering postgres password.
![Connect with PostgreSQL](images/Connect_PostgreSQL.PNG)

## Populate Database
Here we going to restore an existing data base and learn SQL through it.
1. Create an empty database
![Create Database](images/Create_Database.PNG)
![Name Database](images/Name_Database.PNG)

2. Restore Database using dvdrental.tar file, which is folder databases.
![Restore Database Option](images/Restore_Database.PNG)
![Select tar file](images/Restore_Database_2.PNG)
![Check Data options](images/Restore_Database_3.PNG)
![Successful Restoring Pop-up](images/Restore_Database_4.PNG)
![Database Tables view](images/Restore_Database_5.PNG)

3. Rename Database by going into properties, which can be accessed through right click on the Database name.
![Selecting Database Properties](images/Rename_Database_1.PNG)
![Renaming Database](images/Rename_Database_2.PNG)

4. Opening Query Tool
![Opening Query tool](images/Query_tool.PNG)
![Query Tool UI](images/Query_tool_2.PNG)

## SQL Commands And Keywords
Performing commands on dvd rental database.

#### SELECT
Selecting all the rows from table payment.

```
SELECT * FROM payment;
```
![SELECT Statement](images/SELECT_statement.PNG)

#### WHERE
Selecting all the rows, where amount is greater than 3.

```
SELECT * FROM payment
WHERE amount > 3;
```
![WHERE Keyword](images/SELECT_WHERE_statement.PNG)

#### COUNT
Counting all the rows of the payment table.

```
SELECT COUNT(*) FROM payment;
```
![COUNT Keyword](images/SELECT_COUNT_statement.PNG)

#### LIKE
Selecting all the rows from table actor, where the first_name starts from 'P'.

```
SELECT * FROM actor
WHERE first_name LIKE 'P%';
```
![LIKE Keyword](images/WHERE_LIKE_Keyword.PNG)

Counting all the films with title containing 'Truman'

```
SELECT COUNT(*) FROM film
WHERE title LIKE '%Truman%';
```
![COUNT LIKE Keyword](images/LIKE_keyword.PNG)

#### ILIKE
ILIKE is case insensitive version of LIKE.

Selecting all the rows of table film, where description has a case insensitive word 'robot' in it. ('roBot' / 'Robot' / 'ROBOT' / 'RoBoT')

```
SELECT * FROM film
WHERE description ILIKE '%robot%';
```

![ILIKE Keyword](images/ILIKE_Keyword.PNG)

#### DISTINCT
DISTINCT used the find different values.

Selecting distinct districts from address table.

```
SELECT DISTINCT(district) FROM address;
```

![DISTINCT Keyword](images/DISTINCT_keyword.PNG)

#### GROUP BY
Grouping of a column by applying aggregation functionality of other one.

```
SELECT staff_id, COUNT(*) FROM payment
GROUP BY staff_id
```

![GROUP BY Keyword](images/GROUP_BY_Keyword.PNG)

You may use different aggregation function e.g. COUNT, AVG, SUM, etc.

```
SELECT rating, ROUND(AVG(replacement_cost),2) FROM film
GROUP BY rating
```

![GROUP BY AVG Keyword](images/GROUP_BY_AVG_Keyword.PNG)

#### HAVING
Used after GROUP BY to filter results.

Let's say we need to get customers who have done 40 or more payments/transactions.

```
SELECT customer_id, COUNT(*) FROM payment
GROUP BY customer_id
HAVING COUNT(*)>=40;
```

NOTE: It doesn't matter for keyword COUNT, which column is inserted. 

![HAVING AVG Keyword](images/HAVING_Keyword.PNG)


#### ORDER BY
Sorting of the data/rows by some column.

Let's say you want to order payments table by amount from max to low.

```
SELECT * FROM payment
ORDER BY amount DESC
```

![ORDER BY Keyword](images/ORDER_BY_Keyword.PNG)

You may order data by some new column generated through aggregation.

Let take an example in which you need to know which are top five customer w.r.t. amount of spending.

```
SELECT customer_id, SUM(amount) FROM payment
GROUP BY customer_id
ORDER BY SUM(amount) DESC
LIMIT 5
```

![ORDER BY Aggregated Column](images/ORDER_BY_Aggregated_column.PNG)

#### INNER JOIN - ON
The INNER JOIN takes the intersection of the two tables based on a specific columns. It returns all the columns of both tables. ON keyword is used with JOIN statements to tell on which condition the tables must be joined.

```
SELECT * FROM payment
INNER JOIN customer
ON payment.customer_id = customer.customer_id
```

![INNER JOIN on tables](images/INNER_JOIN_ON.PNG)

You may use WHERE keyword to filter results of JOIN and also choose which column to return.

```
SELECT district, customer.email FROM address
INNER JOIN customer
ON address.address_id = customer.address_id
WHERE district = 'California'
```

![INNER JOIN with WHERE](images/INNER_JOIN_with_WHERE.PNG)

You may also join multiple tables in a single query. 

```
SELECT
	TITLE,
	ACTOR.FIRST_NAME,
	ACTOR.LAST_NAME
FROM
	FILM
	INNER JOIN FILM_ACTOR ON FILM_ACTOR.FILM_ID = FILM.FILM_ID
	INNER JOIN ACTOR ON ACTOR.ACTOR_ID = FILM_ACTOR.ACTOR_ID
WHERE
	FIRST_NAME = 'Nick'
	AND LAST_NAME = 'Wahlberg'
```

![MULTI INNER JOIN with WHERE](images/MULTI_INNER_JOIN_with_WHERE.PNG)

#### AS
AS is used to rename column or table.

Let's see AS Keyword in action:

```
SELECT customer_id, amount AS amount_spent
FROM payment
```

![AS Keyword](images/AS_Keyword.PNG)

AS keyword is also used to write clean query by aliasing the table name.

```
SELECT district, c.email FROM address as a
INNER JOIN customer as c
ON a.address_id = c.address_id
WHERE district = 'California'
```
![AS for table name](images/AS_table_name.PNG)

NOTE: You can't use Aliased name for HAVING keyword

![HAVING - Aliased Name](images/HAVING_on_aliased_name.PNG)

#### UNION
The UNION operator is used to combine the result-set of two or more SELECT statements. 

1. Every SELECT statement within UNION must have the same number of columns
2. The columns must also have similar data types
3. The columns in every SELECT statement must also be in the same order

We will be utilizing w3schools.com [example](https://www.w3schools.com/sql/sql_union.asp)


![UNION Demo Database](images/UNION_demo_database.PNG)

```
SELECT City FROM Customers
UNION
SELECT City FROM Suppliers
ORDER BY City;
```

![UNION Keyword](images/UNION_SQL.PNG)



