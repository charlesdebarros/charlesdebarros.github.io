---
title: "Back to Basics - SQL 01 – A Practical Beginner’s Guide"
date: 2026-02-17 09:00
author: "Charles De Barros"
header:
  background-color: "#003f72"
  caption: "Structured Query Language is the foundation of relational data"
  caption_url: https://unsplash.com/
category: ["Back to Basics", "SQL"]
tags:
  - sql
  - sql basics
  - relational databases
  - data analysis
  - backend development
series: "SQL from Zero to Pro"
series_part: 1
image: https://res.cloudinary.com/charlesdebarros/image/upload/v1753179253/22112368_6537887_uaprve.svg
description: "Learn what SQL is, how it works, and how developers and analysts use it in practice. Part 1 of a complete SQL beginner series."
---

# SQL Introduction: What SQL is and how it works

> SQL (Structured Query Language) is the standard language used to interact with relational databases.  

If you work with **data, applications, analytics, or backend systems**, SQL is a foundational skill.

This article is **Part 01 of a 10-part SQL series**, designed for:
- **Developers** building applications
- **Analysts** querying and interpreting data
- **Beginners** who want clarity without jargon

---

<!-- ## 📚 SQL Series Roadmap (SQL 01 → SQL 10)  

1. **SQL 01 – SQL Introduction (You are here)**
2. SQL 02 – Tables, Rows, Columns, and Data Types  
3. SQL 03 – SELECT Queries and Filtering Data  
4. SQL 04 – Sorting, Limiting, and Aggregations  
5. SQL 05 – GROUP BY, HAVING, and Analytics Patterns  
6. SQL 06 – JOINs Explained Visually  
7. SQL 07 – Subqueries and CTEs  
8. SQL 08 – Indexes and Performance Basics  
9. SQL 09 – Transactions, ACID, and Data Integrity  
10. SQL 10 – Real-World SQL Patterns and Best Practices  

--- -->

## Table of Contents

- [What Is SQL?](#what-is-sql)
- [How SQL Works](#how-sql-works)
- [Relational vs Non-Relational Databases](#relational-vs-non-relational-databases)
- [SQL vs RDBMS](#sql-vs-rdbms)
- [Is SQL Case-Sensitive?](#is-sql-case-sensitive)
- [Basic SQL Syntax Examples](#basic-sql-syntax-examples)
- [SQL for Developers vs Analysts](#sql-for-developers-vs-analysts)
- [Practice Exercises](#practice-exercises)
- [Conclusion](#conclusion)
- [Solutions to the exercises from the article](#solutions-to-the-exercises-from-the-article)

---

## What is SQL?

**SQL (Structured Query Language)** is a declarative programming language used to **create, read, update, and delete data** stored in relational databases.

> 💡 **One-sentence definition (featured snippet friendly):**  
> SQL is a language that allows you to query and manipulate structured data stored in relational database tables.

### Mental Model: How to visualise SQL

- A **database** → a folder  
- A **table** → a spreadsheet  
- A **row** → one record  
- A **column** → one attribute  
- **SQL** → the language you use to ask questions  

### Example SQL query

```sql
SELECT name
FROM customers
WHERE country = 'UK';
```

---

## SQL 01: The Fundamentals

### What this means in plain English:
1. Look in the **customers** table
2. Find rows where **country** is 'UK'
3. Return only the **name** column

---

## How SQL works: The Query lifecycle
SQL follows a specific step-by-step process to get you your data:

1. You write a SQL query.
2. The database parses and validates it (checking for syntax errors).
3. The query planner decides how to execute it (finding the fastest path).
4. Tables and indexes are scanned.
5. A result set is returned.

---

## SQL Is declarative
SQL is a **declarative** language, meaning you describe **what** you want, not **how** to get it.

`SELECT * FROM products WHERE price > 100;`

**The database decides:**
* Which index to use
* How to scan rows
* How to optimize performance

---

## SQL Sublanguages (Quick Reference)

| Category | Purpose | Commands |
| :--- | :--- | :--- |
| **DQL** | Query data | `SELECT` |
| **DDL** | Define structure | `CREATE`, `ALTER`, `DROP` |
| **DML** | Modify data | `INSERT`, `UPDATE`, `DELETE` |
| **DCL** | Control access | `GRANT`, `REVOKE` |

---

## Relational (SQL) vs. Non-Relational (NoSQL)

### Relational databases (SQL)
* Fixed schema
* Tables with rows and columns
* Strong consistency (**ACID**)
* Excellent for structured data
* **Examples:** MySQL, PostgreSQL, Oracle, SQL Server

### Non-Relational databases (NoSQL)
* Flexible schema
* JSON, key-value, or graph data
* Horizontally scalable
* Designed for high-volume or unstructured data
* **Examples:** MongoDB, Redis, Cassandra, Neo4j

### Key differences

| Feature | SQL (Relational) | NoSQL |
| :--- | :--- | :--- |
| **Schema** | Fixed | Flexible |
| **Query Language** | SQL | Database-specific |
| **Transactions** | Strong | Often eventual |
| **Use Case** | Structured data | Massive or unstructured data |

---

## SQL vs. RDBMS
* **SQL = The Language:** Defines syntax and rules for interacting with data.
* **RDBMS = The Software:** Relational Database Management Systems that execute SQL and store data (e.g., MySQL, PostgreSQL, SQLite).

> 🧠 **Analogy:** SQL is like English; MySQL or PostgreSQL are like phones that let you speak it.

---

## Is SQL case-sensitive?

| Item | Case-sensitive |
| :--- | :--- |
| **SQL keywords** | ❌ No (`SELECT` is the same as `select`) |
| **Table & column names** | ⚠️ Depends on the OS/Database |
| **String values** | ⚠️ Depends on collation settings |

---

## Basic SQL syntax examples

### SELECT – Query data
```sql
SELECT * FROM employees;
SELECT first_name, last_name FROM employees;
SELECT * FROM employees WHERE department = 'HR';
```

### INSERT - Add data
```sql
INSERT INTO employees (first_name, last_name)
VALUES ('Jane', 'Doe');
```

### UPDATE – Modify data
```sql
UPDATE employees
SET department = 'Marketing'
WHERE id = 101;
```

### UPDATE – Modify data
```sql
UPDATE employees
SET department = 'Marketing'
WHERE id = 101;
```

### DELETE – Remove data
```sql
DELETE FROM employees WHERE id = 101;
```

---

## SQL for Developers vs. Analysts

**SQL for Developers**

* Power APIs and backend services  
* Enforce data integrity  
* Optimize performance & Index tuning  
* Work with migrations and transactions  

**SQL for Data Analysts**

* Explore datasets  
* Build reports and dashboards  
* Use GROUP BY and Aggregations  
* Window functions for deep insights 

---

## Practice Exercises

### Exercise 1 – Identify the parts

Identify the table name, selected columns, and filter condition:

```sql
SELECT email FROM users WHERE active = true;
```

### Exercise 2 – Write your first query

Write a query to select all columns from a table called products where the price is greater than 50.

### Exercise 3 – Think like SQL

Explain in plain English what this query does:
```sql
SELECT name FROM customers ORDER BY created_at DESC;
```

---

## Conclusion

SQL sits at the intersection of software development, data analysis, and business intelligence. In the next article (SQL 02), we’ll break down tables, rows, columns, and data types.

Happy querying! 🚀

---

## Solutions to the exercises from the article

**Exercise 1 – Identify the Parts**

Query: 
```sql
SELECT email FROM users WHERE active = true;
```

* Table name: `users`  
* Selected columns: `email`  
* Filter condition: `active = true` (This ensures you only get records for users who are currently marked as active).  

---

**Exercise 2 – Write Your First Query**

Task: 
```
Select all columns from a table called products where the price is greater than 50.
```

__Solution:__
```sql
SELECT * FROM products 
WHERE price > 50;
```

**Exercise 3 – Think Like SQL**

Query: 
```sql
SELECT name FROM customers ORDER BY created_at DESC;
```

Plain English Explanation:

"Go to the customers table, grab the name of every customer, and list them starting from the most recently created (newest) down to the oldest."

---

### __Bonus__: How the database "thinks" (The execution order)

While we write SQL in the order of SELECT -> FROM -> WHERE, the database actually executes it in a different order to be efficient:

* **FROM**: Where is the data? (Find the table)  
* **WHERE**: Which rows do I need? (Filter the data)  
* **SELECT**: Which columns should I show? (Pick the fields)  
* **ORDER BY**: How should I present them? (Sort the results)  