---
title: "Back to Basics - SQL 02 – Understanding How Data Is Structured"
date: 2026-02-24 10:00
author: "Charles De Barros"
header:
  background-color: "#003f72"
  caption: "Structured Query Language is the foundation of relational data"
  caption_url: https://unsplash.com/
category: ["Back to Basics", "SQL"]
tags:
  - sql
  - sql basics
  - database tables
  - data types
  - relational databases
series: "SQL from Zero to Pro"
series_part: 2
image: https://res.cloudinary.com/charlesdebarros/image/upload/v1753179253/22112368_6537887_uaprve.svg
description: "Learn how relational databases store data using tables, rows, columns, and data types. SQL fundamentals explained visually and practically."
---

# Tables, Rows, Columns, and Data Types

Before writing powerful SQL queries, you need to understand **how data is actually stored**.

This article explains:
- What tables, rows, and columns really are  
- Why schemas and data types matter  
- How developers and analysts think about data structure differently  

This is **Part 02 of the SQL from Zero to Pro series**.

---

## Table of Contents

- [What Is a Database Table?](#what-is-a-database-table)
- [Rows: Records in a Table](#rows-records-in-a-table)
- [Columns: Attributes and Fields](#columns-attributes-and-fields)
- [Schemas and Table Structure](#schemas-and-table-structure)
- [Common SQL Data Types](#common-sql-data-types)
- [Why Data Types Matter](#why-data-types-matter)
- [SQL for Developers vs Analysts](#sql-for-developers-vs-analysts)
- [Practice Exercises](#practice-exercises)
- [Conclusion](#conclusion)
- [Solutions to the exercises from the article](#solutions-to-the-exercises-from-the-article)

---

## What Is a Database Table?

A **table** is where relational databases store data.

Think of a table as a **spreadsheet**:
- Columns define **what kind of data** is stored
- Rows store **individual records**

### Example: `customers` Table

| id | name | email | country |
|---|----|------|--------|
| 1 | Alice | alice@email.com | UK |
| 2 | Bob | bob@email.com | PT |

Each table usually represents **one real-world concept**, such as:
- customers
- orders
- products
- employees

---

## Rows: Records in a Table

A **row** represents a **single record**.

In the `customers` table:
- One row = one customer
- Each row contains values for every column

```text
(1, Alice, alice@email.com, UK)
(2, Bob, bob@email.com, PT)
```

---

## Primary Keys

Most tables have a __primary key__:

* Uniquely identifies each row
* Often an id column

```sql
id INT PRIMARY KEY
```

🧠 No two rows can share the same primary key value.

---

## Columns: Attributes and Fields

A column defines a single attribute of the data.

Examples:

* name
* email
* price
* created_at

Each column has:

* A name
* A data type
* Optional constraints

```sql
name VARCHAR(100)
```

__Column Rules__

* Every value in a column must follow the same data type
* Columns describe what kind of data is allowed

---

## Schemas and Table Structure

A __schema__ is a logical container for tables.

Think of it like:

* A folder inside a database
* A way to organise tables

```text
database
 └── public
     ├── users
     ├── orders
     └── products
```

__Why Schemas Matter__

Schemas help with:

* Organisation
* Permissions
* Avoiding name collisions

---

Common SQL Data Types

Data types define what kind of values a column can store.

| __Numeric Types__ | |
| === | === |
| Type | Example |
| INT | 42 |
| DECIMAL | 99.99 |
| FLOAT | 3.14 |


| __Text Types__ | |
| === | === |
| Type | Example |
| VARCHAR | 'Alice' |
| TEXT | Long descriptions |


| __Date & Time Types__ | |
| === | === |
| Type | Example |
| DATE | 2025-07-21 |
| TIMESTAMP | 2025-07-21 10:00 |


| __Boolean Type__ | |
| === | === |
| Type | Example |
| BOOLEAN | true / false |

--- 

## Why Data Types Matter

Choosing the right data type affects:

* Storage size
* Performance
* Data accuracy

__Example__
```sql
price VARCHAR(10)   ❌
price DECIMAL(10,2) ✅
```

__Benefits of Correct Data Types__

* Prevent invalid data
* Speed up queries
* Enable indexing
* Reduce bugs

---

## SQL for Developers vs Analysts
### SQL for Developers

__Developers care about:__

* Data integrity
* Constraints
* Performance

__Common focus areas:__

* Primary and foreign keys
* NOT NULL and UNIQUE constraints
* Index-friendly data types
* Schema migrations

---

## SQL for Data Analysts

__Analysts care about:__

* Querying and aggregations
* Readability
* Business meaning

__Common focus areas:__

* Column naming clarity
* Date/time consistency
* Numeric precision
* NULL handling

---

## Practice Exercises

### Exercise 1 – Identify the Structure

Given this table definition, identify:

* Table name
* Columns
* Data types

```sql
CREATE TABLE products (
  id INT PRIMARY KEY,
  name VARCHAR(100),
  price DECIMAL(10,2),
  in_stock BOOLEAN
);
```
---

### Exercise 2 – Design a Table

Design a table called employees with:

* id
* first name
* last name
* email
* hire date

Write the `CREATE TABLE` statement.

---

### Exercise 3 – Think Like a Database

Why is `DATE` a better choice than `VARCHAR` for a birth date?

Write your answer in plain English.

### Bonus Practice

Create a table locally using SQLite or an online SQL editor and try:

* Adding columns
* Inserting rows
* Selecting specific columns

---

## Conclusion

Tables, rows, columns, and data types form the __foundation of every relational database__.

If you understand:

* How tables are structured
* Why data types exist
* Then writing SQL queries becomes __dramatically easier__.

In the next article (__SQL 03__), we’ll dive into __SELECT queries and filtering data__, where SQL really starts to feel powerful.

Happy querying 🚀


## Solutions to the exercises from the article

### Exercise 1 – Identify the Structure (Answer)

Given the table definition:

```sql
CREATE TABLE products (
  id INT PRIMARY KEY,
  name VARCHAR(100),
  price DECIMAL(10,2),
  in_stock BOOLEAN
);
```

__Table Name__

* products

__Columns and Data Types__

| Column Name | Data Type | Description |
| === | === | === |
| id | INT | Unique identifier for each product |
| name | VARCHAR(100) | Name of the product |
| price | DECIMAL(10,2) | Product price with two decimal places |
| in_stock | BOOLEAN | Indicates if the product is available |

__Primary Key__

* `id` is the __primary key__
* It uniquely identifies each row in the table

---

### Exercise 2 – Design a Table (Answer)
__Requirements Recap__

Create a table called employees with:

* id
* first name
* last name
* email
* hire date

__One Possible Solution__

```sql
CREATE TABLE employees (
  id INT PRIMARY KEY,
  first_name VARCHAR(100),
  last_name VARCHAR(100),
  email VARCHAR(255),
  hire_date DATE
);
```

__Why These Choices?__

* `INT` for `id`: efficient and commonly indexed
* `VARCHAR` for names and email: flexible length
* `DATE` for hire date: enables date-based queries and sorting

---

### Exercise 3 – Think Like a Database (Answer)
__Question__

Why is `DATE` a better choice than `VARCHAR` for a birth date?

__Answer (Plain English)__

Using the `DATE` data type ensures that:

* Only valid dates can be stored
* Dates can be sorted correctly
* Date calculations (age, duration) are possible
* Indexing and filtering are faster

If dates are stored as 'VARCHAR', the database:

* Cannot reliably compare or sort them
* Cannot perform date arithmetic
* Cannot enforce date validity

---

Next up: __SQL 03 – SELECT Queries and Filtering Data__ 🚀