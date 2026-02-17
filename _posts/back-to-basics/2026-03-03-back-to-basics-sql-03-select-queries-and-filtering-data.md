---
title: "Back to Basics - SQL 03 – SELECT Queries and Filtering Data"
date: 2026-03-03 10:00
author: "Charles De Barros"
header:
  background-color: "#003f72"
  caption: "Structured Query Language is the foundation of relational data"
  caption_url: https://unsplash.com/
category: ["Back to Basics", "SQL"]
tags:
  - sql
  - select statement
  - where clause
  - filtering data
  - database queries
series: "SQL from Zero to Pro"
series_part: 3
image: https://res.cloudinary.com/charlesdebarros/image/upload/v1753179253/22112368_6537887_uaprve.svg
description: "Learn how to query data using SELECT, WHERE, comparison operators, and logical conditions. Core SQL skills for developers and analysts."
---

# SELECT Queries & filtering data - asking the right questions of your data

The **SELECT statement** is the most frequently used SQL command.  
If SQL is a language, **SELECT is the sentence you’ll write the most**.

In this article, you’ll learn how to:
- Retrieve data from tables
- Filter rows using conditions
- Combine multiple filters
- Think like the database when querying data

This is **Part 03 of the SQL from Zero to Pro series**.

---

## Table of Contents

- [What Does SELECT Do?](#what-does-select-do)
- [Selecting Columns](#selecting-columns)
- [Filtering Rows with WHERE](#filtering-rows-with-where)
- [Comparison Operators](#comparison-operators)
- [Logical Operators](#logical-operators)
- [Filtering Text and Dates](#filtering-text-and-dates)
- [SQL for Developers vs Analysts](#sql-for-developers-vs-analysts)
- [Practice Exercises](#practice-exercises)
- [Conclusion](#conclusion)

---

## What does SELECT do?

The `SELECT` statement retrieves data from one or more tables.

### Basic structure

```sql
SELECT column_name
FROM table_name;
```

**Example**
```sql
SELECT name
FROM customers;
```

**What this means:**

* Look in the customers table
* Return values from the name column
* Include every row

---

### Selecting columns
**Selecting all columns**
```sql
SELECT * FROM employees;
```

> ⚠️ __`SELECT *`__ is useful for learning, but should be avoided in production queries.

---

### Selecting specific columns
```sql
SELECT first_name, last_name
FROM employees;
```

Benefits:
* Faster queries
* Clear intent
* Less unnecessary data

---

### Filtering rows with WHERE

The `WHERE` clause filters rows based on a condition.

**Basic example**
```sql
SELECT *
FROM employees
WHERE department = 'HR';
```

**Plain English:**

* Look in `employees`
* Keep only rows where `department` is HR

---

### Comparison Operators

SQL uses comparison operators to filter values.

| Operator | Meaning | Example |
| --- | --- | ---| 
| = | Equal to | department = 'HR' |
| !=  or <> | Not equal	 | status != 'inactive' |
| > | Greater than | salary > 50000 |
| < | Less than	| age < 30 |
| >= | Greater or equal	| price >= 100 |
| <= | Less or equal | score <= 60 |

**Example**
```sql
SELECT name, price
FROM products
WHERE price > 100;
```

--- 

### Logical operators

Logical operators allow you to combine conditions.

#### AND
```sql
SELECT *
FROM employees
WHERE department = 'Sales'
AND salary > 60000;
```

Both conditions must be true.

---

#### OR
```sql
SELECT *
FROM employees
WHERE department = 'HR'
OR department = 'Finance';
```

Either condition can be true.

---

#### NOT
```sql
SELECT *
FROM users
WHERE NOT active = true;

```

Negates a condition.

---

### Filtering text and dates
**Filtering text**

Text values must be wrapped in quotes.
```sql
SELECT *
FROM customers
WHERE country = 'UK';
```

Text comparisons may be **case-sensitive** depending on collation.

**Filtering dates**
```sql
SELECT *
FROM orders
WHERE order_date >= '2025-01-01';
```

Using proper date types allows:

* Sorting
* Range filtering
* Date calculations

---

### SQL for Developers vs Analysts
**SQL for Developers**

Developers focus on:

* Precise filters
* Performance
* Index usage

**Common patterns:**

* Filtering by primary keys
* Using WHERE clauses in JOINs
* Defensive querying (avoiding unexpected rows)

```sql
SELECT *
FROM users
WHERE id = 42;
```

**SQL for Data Analysts**

Analysts focus on:

* Exploring datasets
* Finding trends
* Narrowing down results

**Common patterns:**

* Multiple filters
* Broad queries refined step-by-step
* Temporary exploratory queries

```sql
SELECT *
FROM sales
WHERE region = 'EU'
AND sale_date >= '2025-01-01';
```

--- 

## Practice exercises

**Exercise 1 – Read the Query**

Explain what this query does in plain English:

```sql
SELECT email
FROM users
WHERE active = true;
```

**Exercise 2 – Write a filtered query**

Write a query to:

* Select `name` and `price`
* From `products`
* Where price is less than `50`

**Exercise 3 – Combine conditions**

Write a query that:

* Selects all columns
* From employees
* Where department is `Engineering`
* And hire date is after `2024-01-01`

**Bonus practice**

Experiment with:

* `>` vs `>=`
* Combining `AND` and `OR`
* Filtering text vs numeric values

## Conclusion

The `SELECT` and `WHERE` clauses form the **foundation of SQL querying**.

If you can:

* Select specific columns
* Filter rows accurately
* Combine conditions logically

You already have the skills needed to query real-world databases.

In the next article (**SQL 04**), we’ll explore **sorting results, limiting rows, and aggregating data**, which is where SQL starts answering _business-level questions_.

Happy querying 🚀


## Solutions to the exercises from the article - SQL 03

---

**## **Exercise 1 – Read the query (answer)**

```sql
SELECT email
FROM users
WHERE active = true;
```

**Plain English explanation**

* Look in the `users` table
* Keep only users whose `active` status is `true`
* Return only the `email` column

This query returns the email addresses of all active users.

---

**Exercise 2 – Write a filtered uery (answer)**

```sql
SELECT name, price
FROM products
WHERE price < 50;
```

**What this query does**

* Retrieves product names and prices
* Excludes products priced at `50` or higher

---

**Exercise 3 – Combine conditions (answer)**

```sql
SELECT *
FROM employees
WHERE department = 'Engineering'
AND hire_date > '2024-01-01';
```

**Plain English explanation**

* Look in the `employees` table
* Keep only employees in the Engineering department
* Include only those hired after January 1st, 2024

---

**Bonus Practice – Example exploration**

Below are a few example queries you might try while experimenting.

**Using Greater Than vs Greater Than or Equal To**
```sql
SELECT *
FROM products
WHERE price >= 100;
```

Returns products priced at **100 or more**, including exactly 100.

**Combining AND and OR**
```sql
SELECT *
FROM employees
WHERE department = 'HR'
OR department = 'Finance'
AND active = true;
```

> ⚠️ Important: `AND` is evaluated before `OR`.

To make the logic explicit:

```sql
SELECT *
FROM employees
WHERE (department = 'HR' OR department = 'Finance')
AND active = true;
```
---

**Filtering text vs numeric values**

```sql
-- Text comparison
SELECT *
FROM customers
WHERE country = 'UK';

-- Numeric comparison
SELECT *
FROM orders
WHERE total_amount > 500;
```

Text values are quoted, numeric values are not.


**Key takeaways**

* `SELECT` chooses columns
* `FROM` chooses the table
* `WHERE` filters rows
* Comparison and logical operators let you narrow results precisely

If you can confidently read and write these queries, you’re officially **querying like a SQL user** — not just memorising syntax.

Next up: **SQL 04 – ORDER BY, LIMIT, and Aggregations** 🚀
