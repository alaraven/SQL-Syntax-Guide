# SQL FUNCTIONS

### Aggregate Functions
> performs a calculation on a set of values, and returns a single value. Except for COUNT(*) , aggregate functions ignore null values. Aggregate functions are often used with the GROUP BY clause of the SELECT statement.

`AVG()`	Returns the average of values
`SUM()`	Returns the sum of values
`COUNT()`	Returns the number of rows in a result set
`MAX()`	Returns the maximum value
`MIN()`	Returns the minimum value

### String Functions
> Takes a string value as an input regardless of the data type of the returned value. 

`CONCAT()`	Returns a string by concatenating two or more string values.
`CONCAT_WS()`	Returns a string by concatenating two or more string values with a separator.
`FORMAT()`	Returns a value formatted with the specified format.
`LOWER()`	Converts a string to lowercase.
`UPPER()`	Converts a string to uppercase.
`TRIM()`	Remove leading and trailing spaces from a string.
`REVERSE()`	Returns the reverse order of a string value.
`SUBSTRING()`	Returns a substring from string.

### Date Functions
> The most difficult part when working with dates is to be sure that the format of the date you are trying to insert, matches the format of the date column in the database. As long as your data contains only the date portion, your queries will work as expected.

`NOW()`	Returns the current date and time.
`CURDATE()`	Returns the current date.
`CURTIME()`	Returns the current time
`DATE()`	Extract the date part of a date or datetime expression.
`DAY()`	Returns the day of the month (0-31).
`DAYNAME()`	Returns the name of the weekday.
`MONTH()`	Returns the month from the date passed (1-12).
`MONTHNAME()`	Returns the name of the month.
`YEAR()`	Returns the year.
`DATE_FORMAT()`	Displays date and time value in other formats.
`EXTRACT()`	Extract part of a date.
`DATE_ADD()`	Adds a specified time value (or interval) to a date value.
`DATE_SUB()`	Subtracts a specified time value (or interval) from a date value.
`DATEDIFF()`	Returns the number of days between two dates

### Server Date Functions
> Returns a date part of a date as an integer number. 

`GETDATE()`	Returns the current date and time.
`DATEPART()`	Returns the specified datepart of the specified date 
ie DATEPART(year,'2016-10-25') return 2016.
`DAY()`	Returns the day of the month (0-31).
`MONTH()`	Returns the month from the specified date (0-12).
`YEAR()`	Returns the year from the specified date.
`DATEADD()`	Adds or subtracts a specified time interval from a date.
`DATEDIFF()`	Returns the date or time between two specified dates.
`CONVERT()`	Displays date and time value in other formats.

### SQL Intro

`SELECT` emp_name, hire_date, salary `FROM` employees `WHERE` salary > 5000;
**But it makes more sense like this:**
`SELECT` emp_name, hire_date, salary 
`FROM` employees 
`WHERE` salary > 5000;

### Comments
> Used to explain sections of SQL statements, or to prevent execution of SQL statements.

**Single-line Comment (`--`):**
`--Select all the employees`
SELECT * FROM employees;
**Multi-line Comment (`/**/`):**
`/* Select all the employees whose salary is greater than 5000 */`
SELECT * FROM employees
WHERE salary > 5000;

### Creating a Database in MySQL

shell> `mysql -u root -p`
mysql> `CREATE DATABASE database_name;`
mysql> `CREATE DATABASE IF NOT EXISTS database_name;`
mysql> `USE database_name;`

### Creating Tables
```
CREATE TABLE table_name (
    column1_name data_type constraints,
    column2_name data_type constraints,
    ....
);
```
### Data Type Description

`INT` Stores numeric values in the range of -2147483648 to 2147483647
`DECIMAL` Stores decimal values with exact precision.
`CHAR` Stores fixed-length strings with a maximum size of 255 characters.
`VARCHAR` Stores variable-length strings with a maximum size of 65,535 characters.
`TEXT` Stores strings with a maximum size of 65,535 characters.
`DATE` Stores date values in the YYYY-MM-DD format.
`DATETIME` Stores combined date/time values in the YYYY-MM-DD HH:MM:SS format.
`TIMESTAMP` Stores timestamp values. TIMESTAMP values are stored as the number of seconds since the Unix epoch ('1970-01-01 00:00:01' UTC).
```
CREATE TABLE IF NOT EXISTS persons (
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(50) NOT NULL,
    birth_date DATE,
    phone VARCHAR(15) NOT NULL UNIQUE
);
```

### Creating a Table in SQL

`Syntax for MySQL Database`
```
CREATE TABLE persons (
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(50) NOT NULL,
    birth_date DATE,
    phone VARCHAR(15) NOT NULL UNIQUE
);
```
`Syntax for SQL Server Database`
```
CREATE TABLE persons (
    id INT NOT NULL PRIMARY KEY IDENTITY(1,1),
    name VARCHAR(50) NOT NULL,
    birth_date DATE,
    phone VARCHAR(15) NOT NULL UNIQUE
);
```

### SQL Constraints
> Used to specify rules for the data in a table. Constraints are used to limit the type of data that can go into a table. This ensures the accuracy and reliability of the data in the table. If there is any violation between the constraint and the data action, the action is aborted.

`NOT NULL` enforces a column to NOT accept NULL values.
`PRIMARY KEY` uniquely identifies each record in a table.
`UNIQUE` ensures that all values in a column are different. 
`DEFAULT` is used to set a default value for a column. 
`FOREIGN KEY` is a field (or collection of fields) in one table, that refers to the PRIMARY KEY in another table.
`CHECK` is used to limit the value range that can be placed in a column. 
```
CREATE TABLE employees (
    emp_id INT NOT NULL PRIMARY KEY,
    emp_name VARCHAR(55) NOT NULL,
    hire_date DATE NOT NULL,
    salary INT NOT NULL CHECK (salary >= 3000 AND salary <= 10000),
    dept_id INT,
    FOREIGN KEY (dept_id) REFERENCES departments(dept_id)
);
```

### SQL Insert Statement
> Adds one or more records to any single table in a relational database.

`INSERT INTO` table_name (column1,column2,...) VALUES (value1,value2,...);

mysql> DESCRIBE persons;
`INSERT INTO` persons (name, birth_date, phone)
VALUES ('Peter Peterson', '1990-07-15', '0711-020361');

### SQL Select Statement
> Returns a result set of records, from one or more tables.  

`SELECT` column1_name, column2_name, columnN_name FROM table_name;
`SELECT` * FROM table_name;

### SQL Where Claus
> Specifies that a statement should only affect rows that meet specified criteria.

SELECT column_list FROM table_name `WHERE` condition;
SELECT * FROM table_name `WHERE` condition;

SELECT * FROM employees
`WHERE` salary > 7000;

SELECT emp_id, emp_name, hire_date, salary
FROM employees
`WHERE` salary > 7000;

SELECT * FROM employees
`WHERE` emp_id = 2;

### Operator Description Example
`=	(Equal)` WHERE id = 2
`> (Greater than)`	WHERE age > 30
`<	(Less than)`	WHERE age < 18
`>=	(Greater than or equal)`	WHERE rating >= 4
`<=	(Less than or equal)`	WHERE price <= 100
`LIKE (Simple pattern matching)`	WHERE name LIKE 'Dav'
`IN (Check whether a specified value matches any value in a list or subquery)`	WHERE country IN ('USA', 'UK')
`BETWEEN (Check whether a specified value is within a range of values)`	WHERE rating BETWEEN 3 AND 5

### LIKE Operator Description
> Used to find matches between a character string and a specified pattern. This operator is most commonly used in conjunction with two other SQL operators, WHERE and SELECT, to search for a value in a column.

WHERE CustomerName LIKE '`a%`'	Finds any values that start with "a"
WHERE CustomerName LIKE '`%a`'	Finds any values that end with "a"
WHERE CustomerName LIKE '`%or%`'	Finds any values that have "or" in any position
WHERE CustomerName LIKE '`_r%`'	Finds any values that have "r" in the second position
WHERE CustomerName LIKE '`a__%`'	Finds any values that start with "a" and are at least 3 characters in length
WHERE ContactName LIKE '`a%o`'	Finds any values that start with "a" and ends with "o"

### SQL AND & OR Operators
> The AND and OR operators are used to filter records based on more than one condition: 
The `AND` operator displays a record if all the conditions separated by AND are TRUE. 
The `OR` operator displays a record if any of the conditions separated by OR is TRUE.

SELECT column1_name, column2_name, columnN_name
FROM table_name
WHERE condition1 `AND` condition2;

SELECT * FROM employees
WHERE salary > 7000 `AND` dept_id = 5;

SELECT * FROM employees
WHERE salary > 7000 `OR` dept_id = 5;

SELECT * FROM employees
WHERE salary > 5000 `AND` (dept_id = 1 `OR` dept_id = 5);

### COUNT AVG SUM
> The `COUNT()` function provides the number of rows that matches a specified condition. 
The `AVG()` function provides the average value of a numeric column. 
The `SUM()` function provides the total sum of a numeric column.

SELECT `COUNT`(column_name)
FROM table_name
WHERE condition;

SELECT `AVG`(column_name)
FROM table_name
WHERE condition;

SELECT `SUM`(column_name)
FROM table_name
WHERE condition;

### SQL IN & BETWEEN Operators
>The `IN` operator allows you to specify multiple values in a WHERE clause. The IN operator is a shorthand for multiple OR conditions.
The `BETWEEN` operator selects values within a given range. The values can be numbers, text, or dates. The BETWEEN operator is inclusive: begin and end values are included.

SELECT column_list FROM table_name
WHERE column_name `IN` (value1, value1,...);

SELECT * FROM employees
WHERE dept_id `IN` (1, 3);

SELECT * FROM employees
WHERE dept_id `NOT IN` (1, 3);

SELECT column1_name, column2_name, columnN_name
FROM table_name
WHERE column_name `BETWEEN` min_value AND max_value;

SELECT * FROM employees 
WHERE salary `BETWEEN` 7000 AND 9000;

SELECT * FROM employees WHERE hire_date
`BETWEEN` CAST('2006-01-01' AS DATE) AND CAST('2016-12-31' AS DATE);

SELECT * FROM employees
WHERE emp_name `BETWEEN` 'O' AND 'Z';

### SQL ORDER BY Clause
> Specifies that a SQL SELECT statement returns a result set with the rows being sorted by the values of one or more columns. The sort criteria do not have to be included in the result set.

SELECT * FROM employees 
`ORDER BY` emp_name ASC;

SELECT * FROM employees 
`ORDER BY` emp_name;

SELECT * FROM employees 
`ORDER BY` salary DESC;

SELECT * FROM trainees 
`ORDER BY` first_name;

SELECT * FROM trainees 
`ORDER BY` first_name, last_name;

### SQL TOP / MySQL LIMIT Clause
> The SQL TOP clause is used to fetch a TOP N number or X percent records from a table. Note − All the databases do not support the TOP clause. For example MySQL supports the LIMIT clause to fetch limited number of records.

SELECT `TOP` 3 * FROM employees
ORDER BY salary DESC;

SELECT `TOP` 30 PERCENT * FROM employees
ORDER BY salary DESC;

SELECT `TOP` 30 PERCENT * FROM employees
ORDER BY salary DESC;

SELECT * FROM employees 
ORDER BY salary DESC `LIMIT` 3;

SELECT * FROM employees 
ORDER BY salary DESC `LIMIT` 2, 1;

### SQL DISTINCT Clause
> Is used to return only distinct (different) values. Inside a table, a column often contains many duplicate values; and sometimes you only want to list the different (distinct) values.

SELECT city FROM customers;
SELECT `DISTINCT` city FROM customers;

### SQL Update Statement
> Changes the data of one or more records in a table. Either all the rows can be updated, or a subset may be chosen using a condition. 

`UPDATE` table_name
SET column1_name = value1, column2_name = value2,...
WHERE condition;

`UPDATE` employees SET emp_name = 'Sarah Ann Connor'
WHERE emp_id = 3;

`UPDATE` employees
SET salary = 6000, dept_id = 2
WHERE emp_id = 5;

### SQL DELETE Statement
> Removes one or more records from a table. A subset may be defined for deletion using a condition, otherwise all records are removed.

`DELETE` FROM table_name WHERE condition;

`DELETE` FROM persons WHERE id > 3;

`DELETE` FROM persons;

### SQL TRUNCATE TABLE Statement
> Command deletes the data inside a table, but not the table itself. 

`TRUNCATE` TABLE table_name;

`TRUNCATE` TABLE employees;

### PRIMARY KEY
> A field in a table which uniquely identifies each row/record in a database table. Primary keys must contain unique values. A primary key column cannot have NULL values.
```
CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    PRIMARY KEY (ID)
);

CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    CONSTRAINT PK_Person PRIMARY KEY (ID,LastName)
);
```

### FOREIGN KEY
> Is used to prevent actions that would destroy links between tables. 
```
CREATE TABLE Persons (
    PersonID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    PRIMARY KEY (PersonID)
);

CREATE TABLE Orders (
    OrderID int NOT NULL,
    OrderNumber int NOT NULL,
    PersonID int,
    PRIMARY KEY (OrderID),
    FOREIGN KEY (PersonID) REFERENCES Persons(PersonID)
);

INSERT INTO `tse`.`Orders`
(`OrderID`,
`OrderNumber`,
`PersonID`)
VALUES
(1,223,1);

INSERT INTO `tse`.`Persons`
(`PersonID`,
`LastName`,
`FirstName`,
`Age`)
VALUES
(1,
"Potter",
"matt",
34);

INSERT INTO `tse`.`Orders`
(`OrderID`,
`OrderNumber`,
`PersonID`)
VALUES
(1,223,1);
```

### SQL Joins
> Returns records that have matching values in both tables.
```
SELECT table1.column1, table2.column2...
FROM table1
INNER JOIN table2
ON table1.common_field = table2.common_field;

SQL> SELECT  ID, NAME, AMOUNT, DATE
   FROM CUSTOMERS
   INNER JOIN ORDERS
   ON CUSTOMERS.ID = ORDERS.CUSTOMER_ID;
```