---
title: "SQL 01"
subheadline: "Back to Basics"
date: 2025-07-21 10:00
author: "Charles De Barros"
header: 
    background-color: "#003f72"
    caption: This is a caption for the header image with link
    caption_url: https://unsplash.com/
category: ['Back to Basics', 'SQL']
tags: ["back to basics", "sql"]
image: https://res.cloudinary.com/charlesdebarros/image/upload/v1753179253/22112368_6537887_uaprve.svg
---

# Mastering the Basics of SQL: A Beginner's Guide to Structured Query Language

![SQL](https://res.cloudinary.com/charlesdebarros/image/upload/v1753179253/22112368_6537887_uaprve.svg)

In today’s data-driven world, understanding how to manage and retrieve data effectively is a highly valuable skill. Whether you're a software developer, data analyst, business intelligence specialist, or just tech-curious, learning SQL can be your first step toward harnessing the power of data. This article is a comprehensive beginner’s guide to SQL (Structured Query Language), including what it is, how it works, its relationship with relational databases, how it compares to database management syst...

## What is SQL?

SQL (Structured Query Language) is a standardized language used to communicate with **relational databases**. It allows users to **create, read, update, and delete (CRUD)** data stored in structured tables. Pronounced either as *"S-Q-L"* or *"sequel"*, SQL is the backbone of most database applications today.

SQL has been around since the 1970s and is the most widely used language for managing data stored in relational database systems. Some popular systems that use SQL include:

- MySQL
- PostgreSQL
- Microsoft SQL Server
- Oracle Database
- SQLite

SQL is declarative, meaning you specify *what* data you want, not *how* to get it. For example:

```sql
SELECT name FROM customers WHERE country = 'UK';
```

This command retrieves the names of all customers located in the UK. You don’t need to tell the database how to scan rows or optimize the query—it handles that under the hood.

## How SQL Works

SQL operates on relational databases, which store data in tables. Each table contains rows (records) and columns (attributes or fields). Think of a table as a spreadsheet, where each row is a single item (like a customer), and each column is a detail about that item (like name, email, or phone number).

When you write SQL code, you are sending commands to the database server, which processes the query, performs the requested operations, and returns results.

SQL is divided into several sublanguages:

* Data Query Language (DQL): For querying data.

    ```SELECT```

* Data Definition Language (DDL): For defining structures.

    ```CREATE, DROP, ALTER```

* Data Manipulation Language (DML): For modifying data.

    ```INSERT, UPDATE, DELETE```

* Data Control Language (DCL): For permissions.

    ```GRANT, REVOKE```

Here’s a simple example to demonstrate SQL in action:  
* Create a new table  
```sql
CREATE TABLE products (
    id INT PRIMARY KEY,
    name VARCHAR(100),
    price DECIMAL(10, 2)
);
```

* Insert a row into the table  
```sql
INSERT INTO products (id, name, price)
VALUES (1, 'Laptop', 999.99);
```

* Query the table  
```sql
SELECT * FROM products;
```

## Relational vs. Non-Relational Databases

To understand SQL fully, it helps to grasp the concept of relational databases and how they compare with non-relational (NoSQL) databases.
Relational Databases

Relational databases organize data into structured tables with predefined schemas. Each table has a unique primary key, and relationships between tables are maintained using foreign keys.

Examples:

* MySQL
* PostgreSQL
* Oracle
* SQL Server

These databases require SQL to interact with the data.
Non-Relational Databases (NoSQL)

Non-relational databases store data in formats like JSON, key-value pairs, wide-columns, or graphs. They are often used for unstructured or semi-structured data.

Types include:

* Document stores (MongoDB)
* Key-value stores (Redis)
* Column-family stores (Cassandra)
* Graph databases (Neo4j)

NoSQL databases don’t use SQL as their primary language and are favored in scenarios requiring horizontal scaling, flexible schemas, or high-speed ingestion of semi-structured data.

### Key Differences:

| Feature |	Relational (SQL) | 	Non-Relational (NoSQL) |  
| --- | --- | --- |
| Schema	| Fixed	| Flexible   |
| Data Structure	| Tables with rows/columns |	Documents, key-value, etc. |
| Query Language	| SQL	| No standard; database-specific |
| Transactions	| Strong (ACID) |	Often eventual consistency |
| Use Case	| Structured data |	Unstructured or high-volume data |


## SQL vs. RDBMS (MySQL, PostgreSQL, etc.)

It’s important to distinguish between SQL and the systems that use it.
SQL: The Language

SQL is just the language—a set of rules and syntax for querying relational data. It’s like knowing English: you can use it to communicate, but you still need a phone or a computer to talk to someone.
RDBMS: The Systems

Relational Database Management Systems (RDBMS) like MySQL, PostgreSQL, SQLite, and Microsoft SQL Server are the actual programs that store and manage data. They interpret your SQL commands and return results.

Each RDBMS may implement SQL slightly differently or extend it with proprietary features. For example:

> MySQL supports full-text search and has different default behaviors for string comparison.  
> PostgreSQL has strong support for advanced data types (arrays, JSONB) and powerful indexing options.

Despite these differences, the core SQL syntax is largely consistent across systems. Here's a basic example that works in almost any SQL-based RDBMS:

```sql
SELECT name, email FROM users WHERE active = true;
```

## Is SQL Case-Sensitive?

This is a common beginner question. The answer is: it depends.  
### SQL Keywords

> SQL keywords (like SELECT, FROM, WHERE) are not case-sensitive. The following statements are equivalent:

```sql
SELECT * FROM users;
select * from users;
SeLeCt * FrOm users;
```  

### Identifiers (Table and Column Names)

Whether table names and column names are case-sensitive depends on the database system and sometimes the operating system.

> MySQL: Case sensitivity depends on the underlying OS and how the database was configured.  
> PostgreSQL: Converts unquoted identifiers to lowercase.  
> SQL Server: Not case-sensitive by default, but can be configured to be.  

### String Comparisons

String case sensitivity depends on collation settings.

```sql
SELECT * FROM users WHERE name = 'Alice';
``` 

Might or might not return 'alice' depending on the collation.
Basic SQL Syntax Examples
####  1. SELECT – Querying Data
```sql
SELECT * FROM employees;
SELECT first_name, last_name FROM employees;
SELECT * FROM employees WHERE department = 'HR';
SELECT * FROM employees ORDER BY hire_date DESC;
```
#### 2. INSERT – Adding Data
```sql
INSERT INTO employees (first_name, last_name, department)
VALUES ('Jane', 'Doe', 'Engineering');
```

#### 3. UPDATE – Modifying Data
```sql
UPDATE employees
SET department = 'Marketing'
WHERE id = 101;
```

#### 4. DELETE – Removing Data
```sql
DELETE FROM employees WHERE id = 101;
```

#### 5. JOIN – Combining Tables
```sql
SELECT orders.id, customers.name
FROM orders
JOIN customers ON orders.customer_id = customers.id;
```

## Tips for Writing Good SQL Code (for Beginners)
####  1. Use Descriptive Aliases
```sql
SELECT o.id AS order_id, c.name AS customer_name
FROM orders o
JOIN customers c ON o.customer_id = c.id;
```

#### 2. Avoid SELECT * in Production
```sql
SELECT name, email FROM users;
```

#### 3. Indent and Format Your Code
```sql
SELECT first_name, last_name
FROM employees
WHERE department = 'Sales'
ORDER BY hire_date DESC;
```

#### 4. Use Comments
```sql
-- Get sales employees hired in the last year
SELECT * FROM employees
WHERE department = 'Sales'
  AND hire_date >= '2024-07-01';
```

#### 5. Practice with Real Data

Try sites like Kaggle, Mode SQL Tutorial, or LeetCode.

#### 6. Learn to Debug

Break queries into parts and test conditions individually.
#### 7. Understand Indexing

Use _CREATE INDEX_ and _EXPLAIN_ to analyze performance.

## Conclusion

SQL is an indispensable tool in the world of data. Whether you're working with MySQL, PostgreSQL, or any other relational database, understanding SQL unlocks a wide range of opportunities. It's not just about writing queries—it's about asking the right questions of your data.

Start small, write often, and soon enough, you'll be navigating databases like a pro. 

Happy querying!