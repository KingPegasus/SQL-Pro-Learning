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

`SELECT * FROM payment`
![SELECT Statement](images/SELECT_statement.PNG)

#### WHERE
Selecting all the rows, where amount is greater than 3.

```
SELECT * FROM payment
WHERE amount > 3
```
![WHERE Keyword](images/SELECT_WHERE_statement.PNG)

#### COUNT
Counting all the rows of the payment table.

`SELECT COUNT(*) FROM payment`
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
ILIKE case insensitive version of LIKE.

