---
title: "WHERE and HAVING"
subheadline: "Back to Basics - SQL 06"
date: 2025-12-09 09:00
author: "Charles De Barros"
header: 
    background-color: "#003f72"
    caption: This is a caption for the header image with link
    caption_url: https://unsplash.com/
category: ['Back to Basics', 'SQL']
tags: ["back to basics", "sql"]
image: https://res.cloudinary.com/charlesdebarros/image/upload/v1765302753/sql_where_and_having_difference_1024px_xfumxw.png
---

# SQL filtering with WHERE and HAVING
*(With diagrams, ilustrationsn and practice challenges)*

# Table of Contents

1. [SQL Filtering with WHERE and HAVING](#sql-filtering-with-where-and-having)  
   1.1. [Overview](#overview)
2. [Understanding WHERE](#understanding-where)  
   2.1. [What WHERE Does](#what-where-does)
   2.2. [Diagram: WHERE in Query Flow](#diagram-where-in-query-flow)  
   2.3. [Example](#example)
3. [What Is Aggregation?](#what-is-aggregation)  
   3.1. [Diagram: Aggregation Flow](#diagram-aggregation-flow)
4. [HAVING Filters Aggregated Groups](#having-filters-aggregated-groups)  
   4.1. [Diagram: HAVING in Query Flow](#diagram-having-in-query-flow)  
   4.2. [Example](#example-1)
5. [WHERE vs HAVING](#where-vs-having)  
   5.1. [Illustration: What Each Clause Can Filter](#illustration-what-each-clause-can-filter)  
6. [When to Use Each Clause](#when-to-use-each-clause)  
7. [Practice Challenges](#practice-challenges)  
   7.1. [Challenge 1](#challenge-1)  
   7.2. [Challenge 2](#challenge-2)  
   7.3. [Challenge 3](#challenge-3)  
8. [End of Article](#end-of-article)

# SQL Filtering with WHERE and HAVING  
*(With diagrams, illustrations, and extra challenges)*

## Overview
This article explores how SQL filters data using **WHERE** and **HAVING**, how aggregation works, and when to use each clause. It also includes diagrams, examples, and practice challenges.

---

#  Understanding WHERE

## What WHERE Does  
The **WHERE** clause filters individual rows *before* any grouping or aggregation happens.

### Diagram: WHERE in Query Flow
```
Raw Table Rows
      |
      v
 +-----------+
 |  WHERE    |  <-- filters rows BEFORE grouping
 +-----------+
      |
      v
(Filtered Rows)
```

### Example
```sql
SELECT product_name, price
FROM products
WHERE price > 300;
```

---

#  What Is Aggregation?

Aggregation combines multiple rows into summary values (SUM, COUNT, AVG, etc.).

### Diagram: Aggregation Flow
```
Filtered Rows
      |
      v
 +-------------+
 |  GROUP BY   |
 +-------------+
      |
      v
Aggregated Results
```

---

#  HAVING Filters Aggregated Groups

WHERE cannot filter aggregated values. That’s where **HAVING** comes in.

### Diagram: HAVING in Query Flow
```
Raw Rows
   |
   v
 +--------+
 | WHERE  |
 +--------+
   |
   v
Filtered Rows
   |
   v
 +-----------+
 | GROUP BY  |
 +-----------+
   |
   v
Aggregated Rows
   |
   v
 +--------+
 | HAVING |  <-- filters AFTER aggregation
 +--------+
```

### Example
```sql
SELECT customer_id, SUM(amount) AS total_spent
FROM sales
GROUP BY customer_id
HAVING SUM(amount) > 150;
```

---

#  WHERE vs HAVING

### Illustration: What Each Clause Can Filter
```
            +------------------------------------+
            |           WHERE CLAUSE             |
            |------------------------------------|
            | Filters single rows                 |
            | Cannot use aggregates               |
            | Runs BEFORE group-by                |
            +------------------------------------+

            +------------------------------------+
            |           HAVING CLAUSE            |
            |------------------------------------|
            | Filters aggregated data             |
            | Uses COUNT, SUM, etc                |
            | Runs AFTER group-by                 |
            +------------------------------------+
```

---

#  When to Use Each Clause

| Situation | Use WHERE | Use HAVING |
|----------|-----------|-------------|
| Filter rows by raw values | ✔ | ❌ |
| Filter groups by aggregated values | ❌ | ✔ |
| Exclude unnecessary rows early | ✔ | ❌ |
| Filter based on COUNT(), SUM() | ❌ | ✔ |

---

#  Practice Challenges

## Challenge 1  
**Table:** `orders(customer_id, order_amount, status)`  
**Task:**  
Show customers who:  
1. Only consider orders with status = 'Completed'  
2. Have more than 3 completed orders  
3. Spent more than £500 in total  

### Solution
```sql
SELECT customer_id,
       COUNT(*) AS num_orders,
       SUM(order_amount) AS total_spent
FROM orders
WHERE status = 'Completed'
GROUP BY customer_id
HAVING COUNT(*) > 3
   AND SUM(order_amount) > 500;
```

---

## Challenge 2  
**Table:** `products(category, price)`  
**Task:**  
List categories whose **average** product price is between £200 and £500.

### Solution
```sql
SELECT category, AVG(price) AS avg_price
FROM products
GROUP BY category
HAVING AVG(price) BETWEEN 200 AND 500;
```

---

## Challenge 3  
**Table:** `sales(store, amount, date)`  
**Task:**  
Show stores that had at least **10 sales above £50** in the month of January.

### Solution
```sql
SELECT store,
       COUNT(*) AS count_sales
FROM sales
WHERE amount > 50
  AND date BETWEEN '2025-01-01' AND '2025-01-31'
GROUP BY store
HAVING COUNT(*) >= 10;
```

---

# 📄 End of Article

