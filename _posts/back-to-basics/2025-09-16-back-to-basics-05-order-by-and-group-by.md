---
title: "ORDER BY and GROUP BY"
subheadline: "Back to Basics - SQL 05"
date: 2025-09-16 09:00
author: "Charles De Barros"
header: 
    background-color: "#003f72"
    caption: This is a caption for the header image with link
    caption_url: https://unsplash.com/
category: ['Back to Basics', 'SQL']
tags: ["back to basics", "sql"]
image: #
---

![Ordering Chaos](https://res.cloudinary.com/charlesdebarros/image/upload/v1758016165/brett-jordan-M3cxjDNiLlQ-unsplash_misrtr.jpg)
<em>Photo by <a href="https://unsplash.com/@brett_jordan?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Brett Jordan</a> on <a href="https://unsplash.com/photos/brown-wooden-letter-blocks-on-white-surface-M3cxjDNiLlQ?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Unsplash</a></em>
      

# <span class="sql-statement-headline">ORDER BY</span> vs <span class="sql-statement-headline">GROUP BY</span> in SQL: A Complete Guide with Examples

## Table of Contents
1. [Introduction](#introduction)  
2. [What is ORDER BY?](#what-is-order-by)  
   - [Basic Syntax](#basic-syntax-order-by)  
   - [Beginner Example](#beginner-example-order-by)  
   - [Intermediate Example](#intermediate-example-order-by)  
   - [Advanced Example](#advanced-example-order-by)  
3. [What is GROUP BY?](#what-is-group-by)  
   - [Basic Syntax](#basic-syntax-group-by)  
   - [Beginner Example](#beginner-example-group-by)  
   - [Intermediate Example](#intermediate-example-group-by)  
   - [Advanced Example](#advanced-example-group-by)  
4. [ORDER BY vs GROUP BY: Key Differences](#order-by-vs-group-by-key-differences)  
5. [Common Mistakes and How to Avoid Them](#common-mistakes-and-how-to-avoid-them)  
6. [Tips for Using ORDER BY and GROUP BY Effectively](#tips-for-using-order-by-and-group-by-effectively)  
7. [Practice Table and Queries](#practice-table-and-queries)  
8. [Conclusion](#conclusion)  

---

## Introduction
When working with SQL, two clauses often cause confusion for beginners and even intermediate users: **ORDER BY** and **GROUP BY**. At first glance, they may look similar—both organize query results in some way. However, they serve very different purposes.  

In this article, we’ll break down what each clause does, provide beginner-to-advanced examples, highlight common mistakes, share pro tips, and give you a practice table to strengthen your SQL skills.

---

## What is ORDER BY?
The **ORDER BY** clause is used to **sort** the results of a query. It doesn’t change the data itself—it just arranges the rows in a specified order.

### Basic Syntax (ORDER BY)
```sql
SELECT column1, column2
FROM table_name
ORDER BY column1 [ASC|DESC];
```

- `ASC` = Ascending order (default).  
- `DESC` = Descending order.  

---

### Beginner Example (ORDER BY)
```sql
SELECT name, age
FROM employees
ORDER BY age ASC;
```
**Explanation:** This query retrieves all employee names and ages, sorted from youngest to oldest.

---

### Intermediate Example (ORDER BY)
```sql
SELECT name, department, salary
FROM employees
ORDER BY department ASC, salary DESC;
```
**Explanation:** First sorts by department alphabetically. Within each department, it sorts salaries from highest to lowest.

---

### Advanced Example (ORDER BY)
```sql
SELECT name, salary,
       RANK() OVER (ORDER BY salary DESC) AS salary_rank
FROM employees;
```
**Explanation:** Uses a **window function** with `ORDER BY` to rank employees based on salary, highest to lowest.

---

## What is GROUP BY?
The **GROUP BY** clause is used to **aggregate data** by grouping rows that share a value. It’s commonly paired with aggregate functions like `SUM()`, `COUNT()`, `AVG()`, `MAX()`, and `MIN()`.

### Basic Syntax (GROUP BY)
```sql
SELECT column1, aggregate_function(column2)
FROM table_name
GROUP BY column1;
```

---

### Beginner Example (GROUP BY)
```sql
SELECT department, COUNT(*) AS total_employees
FROM employees
GROUP BY department;
```
**Explanation:** Counts how many employees are in each department.

---

### Intermediate Example (GROUP BY)
```sql
SELECT department, AVG(salary) AS avg_salary
FROM employees
GROUP BY department
ORDER BY avg_salary DESC;
```
**Explanation:** Groups employees by department, calculates the average salary, then orders departments by the highest average salary.

---

### Advanced Example (GROUP BY)
```sql
SELECT department, job_title, SUM(salary) AS total_salary
FROM employees
GROUP BY department, job_title
HAVING SUM(salary) > 50000
ORDER BY total_salary DESC;
```
**Explanation:** Groups by both department and job title, calculates the total salary for each group, filters groups with salaries above 50,000 using `HAVING`, and sorts by total salary.

---

## ORDER BY vs GROUP BY: Key Differences

| Feature              | ORDER BY                                  | GROUP BY                                   |
|----------------------|-------------------------------------------|--------------------------------------------|
| Purpose              | Sorts rows in a specified order           | Groups rows into summary rows               |
| Works With           | Any column (selected or not)              | Columns in SELECT that are not aggregated   |
| Aggregate Functions  | Not required                              | Typically used with aggregates (COUNT, SUM) |
| Output Rows          | Same number of rows as original query     | Fewer rows (summarized)                     |
| Example Use Case     | Sort employees by salary                  | Count employees per department              |

---

## Common Mistakes and How to Avoid Them

1. **Using GROUP BY without aggregates**  
   ```sql
   SELECT department, name
   FROM employees
   GROUP BY department;
   ```
   ❌ Error: `name` is neither grouped nor aggregated.  

   ✅ Fix:
   ```sql
   SELECT department, COUNT(name)
   FROM employees
   GROUP BY department;
   ```

2. **Forgetting ORDER BY after GROUP BY**  
   GROUP BY doesn’t guarantee sorted output. Always add `ORDER BY` if you want a specific order.

   ✅ Example:
   ```sql
   SELECT department, AVG(salary) AS avg_salary
   FROM employees
   GROUP BY department
   ORDER BY avg_salary DESC;
   ```

3. **Confusing ORDER BY with GROUP BY**  
   - `ORDER BY` sorts rows.  
   - `GROUP BY` combines rows.  

   ✅ Tip: If you need **summaries**, use `GROUP BY`. If you need **sorting**, use `ORDER BY`.

4. **Using column aliases incorrectly in GROUP BY**  
   Some SQL engines don’t allow aliases in `GROUP BY`. Always group by actual column names.  

   ✅ Example:
   ```sql
   SELECT department AS dept, COUNT(*)
   FROM employees
   GROUP BY department;
   ```

---

## Tips for Using ORDER BY and GROUP BY Effectively

- Always pair **GROUP BY** with aggregate functions.  
- Use **ORDER BY** to control readability—especially when presenting reports.  
- Combine them wisely:  
  ```sql
  SELECT department, COUNT(*) AS total
  FROM employees
  GROUP BY department
  ORDER BY total DESC;
  ```
- Use **HAVING** with GROUP BY to filter aggregated results (not WHERE).  
- Be careful with performance—sorting large datasets (`ORDER BY`) or grouping many columns (`GROUP BY`) can be slow. Use indexes when possible.  
- Use column positions in `ORDER BY` (e.g., `ORDER BY 2`) only for quick queries. For production code, always use explicit column names for clarity.

---

## Practice Table and Queries

Let’s use a simple table called **employees**:

| id | name     | department   | job_title   | age | salary |
|----|----------|--------------|-------------|-----|--------|
| 1  | Alice    | IT           | Developer   | 25  | 50000  |
| 2  | Bob      | IT           | Developer   | 30  | 60000  |
| 3  | Charlie  | HR           | Recruiter   | 28  | 45000  |
| 4  | Diana    | HR           | Manager     | 40  | 70000  |
| 5  | Edward   | Sales        | Executive   | 35  | 65000  |

### Practice Queries:
1. List employees by salary, highest to lowest.  
   ```sql
   SELECT name, salary
   FROM employees
   ORDER BY salary DESC;
   ```

2. Count how many employees are in each department.  
   ```sql
   SELECT department, COUNT(*) AS total_employees
   FROM employees
   GROUP BY department;
   ```

3. Find the department with the highest average salary.  
   ```sql
   SELECT department, AVG(salary) AS avg_salary
   FROM employees
   GROUP BY department
   ORDER BY avg_salary DESC
   LIMIT 1;
   ```

4. Show the total salary for each job title, but only if it’s above 100,000.  
   ```sql
   SELECT job_title, SUM(salary) AS total_salary
   FROM employees
   GROUP BY job_title
   HAVING SUM(salary) > 100000;
   ```

---

## Conclusion
Understanding the difference between **ORDER BY** and **GROUP BY** is essential for mastering SQL.  
- **ORDER BY** helps you control the order of results.  
- **GROUP BY** lets you summarize and aggregate data.  

When combined correctly, they become powerful tools for data analysis. Avoid the common mistakes, practice with the queries above, and you’ll quickly gain confidence in using both clauses effectively.  
