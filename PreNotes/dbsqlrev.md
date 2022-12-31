# Database/SQL

## What is a Database?
- A **database** is a collection of information that is organized so that it can be easily accessed, managed and updated

## Relational Database
- A type of database
- Uses a structure that allows us to identify and access data in relation to another piece of data in the database
- Often data in relational databases are organized into **tables**.

## Tables
- Tables can consist of hundreds, thousands or even millions of rows of data
- Each **row** is called a **record**.
- Similarly tables can have many columns of data.
- **Columns** are labeled with descriptive names to indicate what kind of data is stored in that specific column (Ex: age, name, country ...)
- **Each column** holds a specific data type

## Relational Database Management System (RDBMS)
- **RDBMS** is a program that allows you to perform **CRUD** operations and administer a relational database.
- Most **RDBMS** use the SQL language to access the database.

 ## What is SQL?
 - SQL stands for Structured Query Language
 - It's a standard language used for accessing and manipulating databases
 - It's consider a programming language mainly for communicating with data stored in a RDBMS
 - SQL syntax is similar to the English language making it relatively easy to write, read and interpret.
 
 ## Example of RDBMS
 - SQLite, MySQL, PostgreSQL...
 - Many RDBMS use SQL (and variations of SQL) to access data in tables
    - Note that across all RDBMS there is a minimal set of SQL commands that are the same, but other commands may vary depending on the RDBMS

## Why do we need SQL?/Why we use SQL?
- Allows users to access data in RDBMS
- Allows users to describe data (different tables can hold different data)
- Allow users to define the data in a database and manipulate that data. (Creating tables, adding/deleting records, defining columns for a table)
- Allows to embed within other languages using SQL modules, libraries & pre-compilers
- Allows users to create and drop databases and tables
- Allows users to create view, stored procedure, functions in a database
- Allows users to set permissions on tables, procedures and views


## SQL Architecture
- SQL Query -> Query Language Processor -> DBMS Engine -> Physical Database
- Parser + Optimizer -> Query Language Processor
- File Manager + Transaction Manager -> DBMS Engine

# Keys in databases
- There are two types of key that are often used in databases: **Primary** and **Foreign**
- Primary keys are a field/piece of data in a table that uniquely identifies each row/record in a table
    - Subsequently, that means all primary keys **must contain** unique values
    - And also primary keys **cannot** contain NULL values
- A table can **only have** one primary key defined on any field/column of data
    - When multiple fields/columns are used as a primary key for a table, they are called a **composite key**

### Composite Keys
- As a **primary key**, a composite key needs to maintain that it has unique values
- How these uniques values differ from one field being used as a **primary key** is that now you can group fields/columns to get a unique value/combine value
- **Composite keys** solve the problem of having a primary key for a table that has no field(s) that can have a unique value for every row/record.

## Keys in Databases Cont'd
- **Foreign keys** is a key that is used to link two tables together. This is sometimes called a **referencing key**. 
- **Foreign keys** like primary keys can consist of a column or multiple columns that match a primary key in a different table 
- The relationship between the table is that a Foreign key in one table matches a Primary key in the other table

## Key Examples
```SQL
CREATE TABLE CUSTOMERS (
    ID INT NOT NULL,
    NAME VARCHAR(20) NOT NULL,
    AGE INT NOT NULL,
    SALARY DECIMAL(18, 2),
    PRIMARY KEY (ID) 
);

CREATE TABLE ORDERS (
    ID INT NOT NULL,
    CUSTOMER_ID INT references CUSTOMERS(ID),
    AMOUNT DOUBLE, 
    PRIMARY KEY (ID)
)

// Creating/Adding Foreign Key
ALTER TABLE ORDERS
    ADD FOREIGN KEY (CUSTOMER_ID) REFERENCES CUSTOMERS (ID);

```

## SQL Statements
- There are different categories for the different types of SQL statements.
- DDL - Data Definition Language - CREATE, ALTER, DROP
- DML - Data Manipulation Language - SELECT, INSERT, UPDATE, DELETE
- DCL - Data Control Language - GRANT, REVOKE
- TCL - Transaction Control Language - SAVEPOINT, ROLLBACK, COMMIT


## SELECT Query
- SQL **SELECT** statement allows fetching of data from a database table with the result in the form of a table.
- These result tables are known as **result sets**.
### Syntax
```SQL
SELECT * FROM table_name; /* Gets the whole table/all available records for that table */
SELECT col_name1, col_name2, col_nameN FROM table_name; /* depending on which columns you exist those will only show in the result set*/
```

## SQL WHERE
- Used to specify a condition when fetching data from a single table or multiple tables from joining
- If the data/record meets the specified condition, then it will be added to the result set. 
- In short WHERE, is used to filter out the necessary records
### Syntax
```SQL
SELECT column1, column2, columnN
FROM table_name
WHERE (condition) /* The parentheses aren't necessary it's to indicate where the condition should go */
```

## INSERT Query
- Used to add new rows of data to a table 
### Syntax
```SQL
INSERT INTO table_name (column1, column2, ...columnN)
VALUES (value1, value2, ...valueN)
```
- The data values for a column should be listed in the same order as the column was listed.
- If you said (NAME, AGE, DATE), then your values for those columns should be (name_here, age_here, date_here). 

## SQL Joins
- Joins are a clause used to combine records from two or more tables in a database. 
- This is done using values common to each field from the fields being combined
- There are 4 different types of joins:
    - INNER JOIN
    - LEFT JOIN
    - RIGHT JOIN
    - FULL JOIN
### Syntax
```SQL
SELECT ID, NAME, AGE, AMOUNT 
FROM CUSTOMERS INNER JOIN ORDERS
ON CUSTOMERS.ID = ORDERS.CUSTOMER_ID
```

## SQL Joins In-Depth
- Usually, tables are joined based on primary key and foreign key connecting the table. 
- If two tables both have a column that is labeled the same but contain values that aren't use the same way (not have the same purpose as each other) then you can differentiate or get either column by specifying the tablename with the dot operator before the column name
```SQL
/* Let's consider that the Employees table has a column named Address (this refers to the employees' home addresses) and the Customers table also has a column named Address (this refers to the customer's home address). For joining and get either addresses using the SELECT query */
SELECT employeeID, customerID, Employees.Address 
FROM Orders 
JOIN Customers ON Customers.id = Orders.CustomerID
JOIN Employees ON Employees.id = Orders.EmployeeID
```

## OTHER SQL Keywords
- **AS** can be used to make alias for table names
```SQL
FROM CUSTOMERS AS c
```
- **USING** is used during joins if join occurs on two columns that are named the same.
```SQL
JOIN Customers ON Customers.id = Orders.id
/* USING keyword */
JOIN Customers USING (id)
```

## INNER JOIN
- This join is most common or used where records that have matching values in both tables are fetched/selected and displayed in the result set
- It should be noted that if there are records in one table that don't have a match in the other table, then those records are shown

## LEFT JOIN
- Shows all records of the left table and also matching values records are fetched as well
- When displayed, you may see records in the result set that may not a have value for the column used to join that matches with the right table

## RIGHT JOIN 
- Is the inversion of the LEFT JOIN where instead all the right table records are shown along with matched values records that have been fetched
- Again there may be records that don't have a value for a column due to no matches in value from the right table with the left table

## FULL JOIN
- Grabs all the records from both tables, and any records that don't have matches are shown regardless of what table it comes from
- Again records that don't have match values are displayed but this time unlike Left or Right Join all such records are shown.
