---
title: "Back to Basics – SQL 04 – ORDER BY, LIMIT, and Aggregations"
date: 2026-03-10 10:00
author: "Charles De Barros"
header:
  background-color: "#003f72"
  caption: "Structured Query Language is the foundation of relational data"
  caption_url: https://unsplash.com/
published: true
category: ["Back to Basics", "SQL"]
tags:
  - sql
  - order by
  - limit
  - aggregate functions
  - group by
series: "SQL from Zero to Pro"
series_part: 4
image: https://res.cloudinary.com/charlesdebarros/image/upload/v1753179253/22112368_6537887_uaprve.svg
description: "Learn how to sort results, limit rows, and summarise data using ORDER BY, LIMIT, and aggregate functions like COUNT, SUM, and AVG."
---

# SQL 04 – ORDER BY, LIMIT, and Aggregations
## Turning Raw Data into Useful Answers

So far, you’ve learned how to **retrieve and filter data**.  
Now it’s time to make that data **useful**.

In this article, you’ll learn how to:
- Sort query results
- Limit how many rows are returned
- Summarise large datasets using aggregate functions

This is **Part 04 of the SQL from Zero to Pro series**.

---

## Table of Contents

- [Sorting Results with ORDER BY](#sorting-results-with-order-by)
- [Limiting Rows with LIMIT](#limiting-rows-with-limit)
- [Why Aggregations Matter](#why-aggregations-matter)
- [Common Aggregate Functions](#common-aggregate-functions)
- [GROUP BY Explained](#group-by-explained)
- [Filtering Aggregates with HAVING](#filtering-aggregates-with-having)
- [SQL for Developers vs Analysts](#sql-for-developers-vs-analysts)
- [Practice Exercises](#practice-exercises)
- [Conclusion](#conclusion)

---

## Sorting Results with ORDER BY

By default, SQL does **not guarantee order**.

If order matters, you must explicitly specify it.

### Basic Syntax

```sql
SELECT *
FROM employees
ORDER BY last_name;
```

This sorts results in ascending order by default.

---

## DESC vs ASC

```sql
SELECT *
FROM employees
ORDER BY hire_date DESC;
```

* ASC → ascending (default)
* DESC → descending

---

## Sorting by Multiple Columns

```sql
SELECT *
FROM employees
ORDER BY department ASC, hire_date DESC;
```

**What this does:**

* Groups employees by department
* Shows newest hires first within each department

---

## Limiting Rows with LIMIT

The LIMIT clause restricts how many rows are returned.

**Example**

```sql
SELECT *
FROM products
LIMIT 10;
```

Returns only the first 10 rows.

---

## ORDER BY + LIMIT (Very Common)

```sql
SELECT *
FROM products
ORDER BY price DESC
LIMIT 5;
```

**Plain English:**  
“Show me the 5 most expensive products.”

---

## Why Aggregations Matter

Most real-world questions are **summary questions**, not row-level questions.

**Examples:**
* 
* How many users do we have?
* What is the average order value?
* What was total revenue last month?
* 
This is where **aggregate functions** come in.

---

## Common Aggregate Functions

**COUNT – Count Rows**

```sql
SELECT COUNT(*)
FROM users;
```

Counts total rows.

---

**SUM – Add Values**

```sql
SELECT SUM(total_amount)
FROM orders;
```

Adds up numeric values.

---

**AVG – Average Value**

```sql
SELECT AVG(price)
FROM products;
```

Calculates the _mean_.

---

**MIN and MAX**

```sql
SELECT MIN(price), MAX(price)
FROM products;
```

Finds _smallest_ and _largest_ values.

---

**GROUP BY Explained**

> GROUP BY allows you to aggregate per category.

**Example: Count Users by Country**

```sql
SELECT country, COUNT(*) AS user_count
FROM users
GROUP BY country;
```

What happens:

* Rows are grouped by country
* COUNT is applied to each group
* One row per country is returned

---

**Mental Model for GROUP BY**

> **GROUP BY** collapses many rows into fewer summary rows.

---

**Filtering Aggregates with HAVING**

You cannot use WHERE with aggregate results.

Use `HAVING` instead.

**Example:**

```sql
SELECT country, COUNT(*) AS user_count
FROM users
GROUP BY country
HAVING COUNT(*) > 100;
```

**Plain English:**  
“Show only countries with more than 100 users.”

---

**WHERE vs HAVING**

| Clause |	Filters |
| --- | --- |
| **WHERE** |	Rows before grouping |
| **HAVING** |	Groups after aggregation |

---

## SQL for Developers vs Analysts
**SQL for Developers**

Developers use these features to:

* Build leaderboards
* Paginate API results
* Optimise queries

**Common patterns:**

* ORDER BY with indexed columns
* LIMIT for pagination
* COUNT for monitoring and health checks

```sql
SELECT COUNT(*)
FROM orders
WHERE status = 'pending';
```

---

**SQL for Data Analysts**

Analysts use aggregations constantly to:

* Track KPIs
* Build dashboards
* Spot trends

**Common patterns:**

* GROUP BY + AVG
* Time-based aggregations
* HAVING for thresholds

```sql
SELECT department, AVG(salary)
FROM employees
GROUP BY department;
```

---

## Practice Exercises

**Exercise 1 – Sorting Data**

Write a query to:

* Select all columns
* From `employees`
* Order by `hire_date` from newest to oldest

---

**Exercise 2 – Limiting Results**

Write a query to:

* Select all columns
* From `products`
* Return only the 3 cheapest products

---

**Exercise 3 – Basic Aggregation**

Write a query to:

* Count the total number of users
* From the `users` table

---

**Exercise 4 – GROUP BY**

Write a query to:

* Count how many employees work in each department

---

**Bonus Practice**

Try combining:

* WHERE
* GROUP BY
* HAVING
* ORDER BY
* LIMIT

In a single query.

---

## Conclusion

With ORDER BY, LIMIT, and aggregations, SQL stops being about **rows** and starts being about **answers**.

If you can:

* Sort data intentionally
* Limit result sets
* Summarise large tables

You’re now doing **real-world SQL**.

In the next article (**SQL 05**), we’ll dive into **GROUP BY** patterns, **HAVING** in depth, and analytical thinking with SQL.

Happy querying 🚀

---

## Solutions to the exercises from the article – SQL 04

**Exercise 1 – Sorting Data (Answer)**

```sql
SELECT *
FROM employees
ORDER BY hire_date DESC;
```

**Explanation**

* ORDER BY hire_date sorts by hire date
* DESC ensures the newest hires appear first

---

**Exercise 2 – Limiting Results (Answer)**

```sql
SELECT *
FROM products
ORDER BY price ASC
LIMIT 3;
```

**Explanation**

* Products are sorted from cheapest to most expensive
* LIMIT 3 returns only the first three rows

---

**Exercise 3 – Basic Aggregation (Answer)**

```sql
SELECT COUNT(*)
FROM users;
```

**Explanation**

* **COUNT(*)** counts all rows in the table
* The result is a single number representing total users

**Exercise 4 – GROUP BY (Answer)**

```sql
SELECT department, COUNT(*) AS employee_count
FROM employees
GROUP BY department;
```

**Explanation**

* Rows are grouped by department
* **COUNT(*)** is applied to each group
* One row per department is returned

Bonus Practice – Combined Query (Example Answer)

```sql
SELECT department, COUNT(*) AS employee_count
FROM employees
WHERE active = true
GROUP BY department
HAVING COUNT(*) > 10
ORDER BY employee_count DESC
LIMIT 5;
```

**Plain English Explanation**

* Look only at active employees
* Group them by department
* Keep departments with more than 10 employees
* Sort departments by employee count (highest first)
* Return only the top 5 departments

Key Takeaways

* **ORDER BY** controls how results are sorted
* **LIMIT** controls how many rows are returned
* Aggregate functions summarise data
* **GROUP BY** changes row-level data into insights
* **HAVING** filters aggregated results

If you can read and write queries like these, you’re officially ___thinking analytically in SQL___.

Next up: **SQL 05 – GROUP BY Patterns, HAVING Deep Dive, and Analytical Thinking** 🚀