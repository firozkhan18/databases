### 1. **What is SQL?**

**Answer:**

SQL (Structured Query Language) is a standard language for managing and manipulating relational databases. It allows users to create, read, update, and delete (CRUD) data in databases. SQL is used to query and modify data, as well as to define and manage database structures.

### 2. **What is the difference between `INNER JOIN` and `LEFT JOIN`?**

**Answer:**

- **`INNER JOIN`:** Returns rows that have matching values in both tables. If there is no match, the row is not included in the result set.

  **Example:**

  ```sql
  SELECT employees.name, departments.department_name
  FROM employees
  INNER JOIN departments ON employees.department_id = departments.id;
  ```

  This query returns only those employees who have a matching department.

- **`LEFT JOIN` (or `LEFT OUTER JOIN`):** Returns all rows from the left table and the matched rows from the right table. If there is no match, the result is `NULL` on the right side.

  **Example:**

  ```sql
  SELECT employees.name, departments.department_name
  FROM employees
  LEFT JOIN departments ON employees.department_id = departments.id;
  ```

  This query returns all employees, including those who do not belong to any department. For such employees, the `department_name` will be `NULL`.

### 3. **What is a `GROUP BY` clause?**

**Answer:**

The `GROUP BY` clause is used to group rows that have the same values into summary rows. It is often used with aggregate functions like `SUM`, `AVG`, `MAX`, `MIN`, and `COUNT` to perform calculations on each group.

**Example:**

```sql
SELECT department_id, COUNT(*)
FROM employees
GROUP BY department_id;
```

This query counts the number of employees in each department.

### 4. **What is a `HAVING` clause?**

**Answer:**

The `HAVING` clause is used to filter groups of rows created by the `GROUP BY` clause. Unlike the `WHERE` clause, which filters rows before grouping, `HAVING` filters after the grouping has been done.

**Example:**

```sql
SELECT department_id, COUNT(*)
FROM employees
GROUP BY department_id
HAVING COUNT(*) > 5;
```

This query returns departments that have more than 5 employees.

### 5. **How can you retrieve unique values from a column?**

**Answer:**

To retrieve unique values from a column, you use the `DISTINCT` keyword.

**Example:**

```sql
SELECT DISTINCT department_id
FROM employees;
```

This query returns a list of unique department IDs from the employees table.

### 6. **What is a `SUBQUERY`?**

**Answer:**

A `SUBQUERY` (or inner query) is a query nested inside another query. It can be used to perform operations that depend on the result of the outer query.

**Example:**

```sql
SELECT name
FROM employees
WHERE department_id IN (SELECT id FROM departments WHERE department_name = 'Sales');
```

This query retrieves the names of employees who work in the 'Sales' department.

### 7. **How do you update data in a table?**

**Answer:**

You use the `UPDATE` statement to modify existing records in a table.

**Example:**

```sql
UPDATE employees
SET salary = salary * 1.10
WHERE performance_rating = 'Excellent';
```

This query increases the salary of employees with an 'Excellent' performance rating by 10%.

### 8. **What is the `ORDER BY` clause?**

**Answer:**

The `ORDER BY` clause is used to sort the result set of a query by one or more columns. You can specify the sort direction as `ASC` (ascending) or `DESC` (descending).

**Example:**

```sql
SELECT name, salary
FROM employees
ORDER BY salary DESC;
```

This query retrieves employees sorted by their salary in descending order.

### 9. **What is the difference between `UNION` and `UNION ALL`?**

**Answer:**

- **`UNION`:** Combines the result sets of two or more `SELECT` statements and removes duplicate rows.

  **Example:**

  ```sql
  SELECT name FROM employees
  UNION
  SELECT name FROM contractors;
  ```

- **`UNION ALL`:** Combines the result sets of two or more `SELECT` statements and includes all rows, including duplicates.

  **Example:**

  ```sql
  SELECT name FROM employees
  UNION ALL
  SELECT name FROM contractors;
  ```

### 10. **How do you delete data from a table?**

**Answer:**

You use the `DELETE` statement to remove rows from a table.

**Example:**

```sql
DELETE FROM employees
WHERE department_id = 3;
```

This query deletes all employees who belong to department ID 3.

### 11. **What is an `INDEX` and why is it used?**

**Answer:**

An `INDEX` is a database object that improves the speed of data retrieval operations on a table at the cost of additional storage and potential slowdown of `INSERT`, `UPDATE`, and `DELETE` operations. Indexes are used to quickly locate rows without having to scan the entire table.

**Example:**

```sql
CREATE INDEX idx_employee_name
ON employees(name);
```

This query creates an index on the `name` column of the `employees` table.

### 12. **What is a `VIEW` in SQL?**

**Answer:**

A `VIEW` is a virtual table based on the result of a `SELECT` query. It does not store data physically but provides a way to simplify complex queries, enhance security by restricting access to specific columns, or present data in a specific format.

**Example:**

```sql
CREATE VIEW employee_details AS
SELECT name, salary
FROM employees
WHERE status = 'Active';
```

This query creates a view named `employee_details` that shows the names and salaries of active employees.

### 13. **What is the difference between `TRUNCATE` and `DELETE`?**

**Answer:**

- **`TRUNCATE`:** Removes all rows from a table and resets any auto-increment values. It is faster than `DELETE` because it does not generate individual row delete operations and cannot be rolled back.

  **Example:**

  ```sql
  TRUNCATE TABLE employees;
  ```

- **`DELETE`:** Removes rows from a table based on a condition. It can be rolled back if used within a transaction.

  **Example:**

  ```sql
  DELETE FROM employees WHERE department_id = 3;
  ```

### 14. **What is a `CASE` statement in SQL?**

**Answer:**

The `CASE` statement allows you to perform conditional logic in SQL queries. It returns a value based on conditions provided.

**Example:**

```sql
SELECT name,
       CASE
           WHEN salary > 50000 THEN 'High'
           WHEN salary BETWEEN 30000 AND 50000 THEN 'Medium'
           ELSE 'Low'
       END AS salary_grade
FROM employees;
```

This query categorizes employees' salaries into 'High', 'Medium', or 'Low' based on their salary amounts.

### 15. **How do you find the second highest salary in a table?**

**Answer:**

You can find the second highest salary using a subquery with `LIMIT` or by using the `ROW_NUMBER()` window function.

**Example Using Subquery:**

```sql
SELECT MAX(salary) AS second_highest_salary
FROM employees
WHERE salary < (SELECT MAX(salary) FROM employees);
```

**Example Using `ROW_NUMBER()`:**

```sql
WITH RankedSalaries AS (
    SELECT salary,
           ROW_NUMBER() OVER (ORDER BY salary DESC) AS rank
    FROM employees
)
SELECT salary
FROM RankedSalaries
WHERE rank = 2;
```

### 16. **What are aggregate functions in SQL?**

**Answer:**

Aggregate functions perform calculations on a set of values and return a single value. Common aggregate functions include:

- **`COUNT()`**: Counts the number of rows.
- **`SUM()`**: Calculates the sum of a numeric column.
- **`AVG()`**: Calculates the average value of a numeric column.
- **`MAX()`**: Returns the maximum value in a set.
- **`MIN()`**: Returns the minimum value in a set.

**Example:**

```sql
SELECT AVG(salary) AS average_salary, MAX(salary) AS highest_salary
FROM employees;
```

This query calculates the average and highest salary from the `employees` table.

### 17. **What is normalization in SQL?**

**Answer:**

Normalization is the process of organizing data in a database to reduce redundancy and improve data integrity. It involves dividing large tables into smaller tables and defining relationships between them. The goals of normalization include minimizing duplication of data and ensuring data consistency.

**Example of Normalization:**

- **1st Normal Form (1NF):** Ensure that all columns contain atomic (indivisible) values.
- **2nd Normal Form (2NF):** Ensure that all non-key columns are fully dependent on the primary key.
- **3rd Normal Form (3NF):** Ensure that all columns are dependent only on the primary key, not on other non-key columns.

### 18. **How do you perform a `JOIN` operation in SQL?**

**Answer:**

A `JOIN` operation combines rows from two or more

 tables based on a related column between them.

**Example:**

```sql
SELECT employees.name, departments.department_name
FROM employees
JOIN departments ON employees.department_id = departments.id;
```

This query retrieves employee names and their corresponding department names by joining the `employees` and `departments` tables based on the `department_id` column.

### 19. **How do you handle `NULL` values in SQL?**

**Answer:**

Handling `NULL` values in SQL often involves using functions and conditions to check for or replace `NULL` values.

**Examples:**

- **`IS NULL` and `IS NOT NULL`:** Check for `NULL` values.

  ```sql
  SELECT name
  FROM employees
  WHERE manager_id IS NULL;
  ```

- **`COALESCE()`:** Replaces `NULL` with a specified value.

  ```sql
  SELECT name, COALESCE(bonus, 0) AS bonus
  FROM employees;
  ```

- **`IFNULL()` or `NVL()`:** Similar to `COALESCE()` but may vary by database system.

  ```sql
  SELECT name, IFNULL(bonus, 0) AS bonus
  FROM employees;
  ```

### 20. **What are window functions in SQL?**

**Answer:**

Window functions perform calculations across a set of table rows related to the current row. They are used to provide ranking, running totals, moving averages, and other analytical operations.

**Common Window Functions:**

- **`ROW_NUMBER()`:** Assigns a unique number to each row based on the order specified.
- **`RANK()`:** Assigns a rank to each row, with gaps in ranking values for duplicates.
- **`DENSE_RANK()`:** Similar to `RANK()` but without gaps in ranking values.
- **`SUM()`, `AVG()`, `MIN()`, `MAX()`:** Aggregate functions used as window functions to calculate over a specific range.

**Example:**

```sql
SELECT name, salary,
       RANK() OVER (ORDER BY salary DESC) AS salary_rank
FROM employees;
```

This query ranks employees based on their salary.

In SQL, **joins** are used to combine rows from two or more tables based on a related column between them. Understanding different types of joins is crucial for querying relational databases effectively. Below are the primary types of joins with explanations and examples:

### 1. **INNER JOIN**

**Definition:** 
- An `INNER JOIN` returns rows that have matching values in both tables. If there is no match, the rows are not included in the result set.

**Example:**

Consider two tables, `employees` and `departments`:

```sql
-- employees table
CREATE TABLE employees (
    id INT PRIMARY KEY,
    name VARCHAR(100),
    department_id INT
);

-- departments table
CREATE TABLE departments (
    id INT PRIMARY KEY,
    department_name VARCHAR(100)
);

-- Sample data
INSERT INTO employees VALUES (1, 'Alice', 101);
INSERT INTO employees VALUES (2, 'Bob', 102);
INSERT INTO employees VALUES (3, 'Charlie', NULL);

INSERT INTO departments VALUES (101, 'HR');
INSERT INTO departments VALUES (102, 'Finance');
```

**Query:**

```sql
SELECT employees.name, departments.department_name
FROM employees
INNER JOIN departments ON employees.department_id = departments.id;
```

**Result:**

| name    | department_name |
|---------|------------------|
| Alice   | HR               |
| Bob     | Finance          |

In this example, only employees with a valid `department_id` that matches an `id` in the `departments` table are included.

### 2. **LEFT JOIN (LEFT OUTER JOIN)**

**Definition:** 
- A `LEFT JOIN` returns all rows from the left table and the matched rows from the right table. If there is no match, the result is `NULL` on the right side.

**Example:**

**Query:**

```sql
SELECT employees.name, departments.department_name
FROM employees
LEFT JOIN departments ON employees.department_id = departments.id;
```

**Result:**

| name    | department_name |
|---------|------------------|
| Alice   | HR               |
| Bob     | Finance          |
| Charlie | NULL             |

Here, the `LEFT JOIN` includes all employees, even if they do not belong to any department.

### 3. **RIGHT JOIN (RIGHT OUTER JOIN)**

**Definition:** 
- A `RIGHT JOIN` returns all rows from the right table and the matched rows from the left table. If there is no match, the result is `NULL` on the left side.

**Example:**

**Query:**

```sql
SELECT employees.name, departments.department_name
FROM employees
RIGHT JOIN departments ON employees.department_id = departments.id;
```

**Result:**

| name    | department_name |
|---------|------------------|
| Alice   | HR               |
| Bob     | Finance          |
| NULL    | Marketing        |

In this example, `RIGHT JOIN` includes all departments, even if no employees are assigned to some of them.

### 4. **FULL JOIN (FULL OUTER JOIN)**

**Definition:** 
- A `FULL JOIN` returns all rows when there is a match in one of the tables. It returns `NULL` for rows that do not have a match in either table.

**Example:**

**Query:**

```sql
SELECT employees.name, departments.department_name
FROM employees
FULL JOIN departments ON employees.department_id = departments.id;
```

**Result:**

| name    | department_name |
|---------|------------------|
| Alice   | HR               |
| Bob     | Finance          |
| Charlie | NULL             |
| NULL    | Marketing        |

This query includes all employees and all departments, with `NULL` values where there is no match.

### 5. **CROSS JOIN**

**Definition:** 
- A `CROSS JOIN` returns the Cartesian product of the two tables. This means it combines every row of the first table with every row of the second table.

**Example:**

**Query:**

```sql
SELECT employees.name, departments.department_name
FROM employees
CROSS JOIN departments;
```

**Result:**

| name    | department_name |
|---------|------------------|
| Alice   | HR               |
| Alice   | Finance          |
| Alice   | Marketing        |
| Bob     | HR               |
| Bob     | Finance          |
| Bob     | Marketing        |
| Charlie | HR               |
| Charlie | Finance          |
| Charlie | Marketing        |

Here, every employee is paired with every department.

### 6. **SELF JOIN**

**Definition:** 
- A `SELF JOIN` is a regular join where a table is joined with itself. This is useful for hierarchical or recursive relationships.

**Example:**

Consider an `employees` table where `manager_id` refers to another employee who is the manager:

```sql
-- employees table
CREATE TABLE employees (
    id INT PRIMARY KEY,
    name VARCHAR(100),
    manager_id INT
);

-- Sample data
INSERT INTO employees VALUES (1, 'Alice', NULL);
INSERT INTO employees VALUES (2, 'Bob', 1);
INSERT INTO employees VALUES (3, 'Charlie', 1);
```

**Query:**

```sql
SELECT e1.name AS employee_name, e2.name AS manager_name
FROM employees e1
LEFT JOIN employees e2 ON e1.manager_id = e2.id;
```

**Result:**

| employee_name | manager_name |
|---------------|--------------|
| Alice         | NULL         |
| Bob           | Alice        |
| Charlie       | Alice        |

In this query, each employee is shown along with their manager’s name.

Certainly! Here are some common SQL query-related coding questions along with their answers. These examples cover a range of SQL operations, including selection, aggregation, filtering, and complex joins.

### 1. **Find the second highest salary from the `employees` table**

**Question:**
Write a query to find the second highest salary from the `employees` table.

**Table Structure:**
```sql
CREATE TABLE employees (
    id INT PRIMARY KEY,
    name VARCHAR(100),
    salary DECIMAL(10, 2)
);
```

**Example Data:**
```sql
INSERT INTO employees (id, name, salary) VALUES (1, 'Alice', 50000);
INSERT INTO employees (id, name, salary) VALUES (2, 'Bob', 60000);
INSERT INTO employees (id, name, salary) VALUES (3, 'Charlie', 70000);
INSERT INTO employees (id, name, salary) VALUES (4, 'David', 80000);
```

**Answer:**

```sql
SELECT MAX(salary) AS second_highest_salary
FROM employees
WHERE salary < (SELECT MAX(salary) FROM employees);
```

### 2. **List all employees who have not been assigned a department**

**Question:**
Write a query to list all employees who do not have an assigned department. Assume the `employees` table has a `department_id` column which can be `NULL`.

**Table Structure:**
```sql
CREATE TABLE employees (
    id INT PRIMARY KEY,
    name VARCHAR(100),
    department_id INT
);
```

**Example Data:**
```sql
INSERT INTO employees (id, name, department_id) VALUES (1, 'Alice', 101);
INSERT INTO employees (id, name, department_id) VALUES (2, 'Bob', NULL);
INSERT INTO employees (id, name, department_id) VALUES (3, 'Charlie', 102);
```

**Answer:**

```sql
SELECT name
FROM employees
WHERE department_id IS NULL;
```

### 3. **Find the average salary by department**

**Question:**
Write a query to find the average salary of employees in each department.

**Table Structure:**
```sql
CREATE TABLE employees (
    id INT PRIMARY KEY,
    name VARCHAR(100),
    salary DECIMAL(10, 2),
    department_id INT
);
```

**Example Data:**
```sql
INSERT INTO employees (id, name, salary, department_id) VALUES (1, 'Alice', 50000, 101);
INSERT INTO employees (id, name, salary, department_id) VALUES (2, 'Bob', 60000, 101);
INSERT INTO employees (id, name, salary, department_id) VALUES (3, 'Charlie', 70000, 102);
```

**Answer:**

```sql
SELECT department_id, AVG(salary) AS average_salary
FROM employees
GROUP BY department_id;
```

### 4. **Get the total number of employees in each department**

**Question:**
Write a query to get the total number of employees in each department.

**Answer:**

```sql
SELECT department_id, COUNT(*) AS total_employees
FROM employees
GROUP BY department_id;
```

### 5. **Find employees who earn more than their manager**

**Question:**
Assume an `employees` table where each employee has a `manager_id` pointing to their manager. Write a query to find employees who earn more than their manager.

**Table Structure:**
```sql
CREATE TABLE employees (
    id INT PRIMARY KEY,
    name VARCHAR(100),
    salary DECIMAL(10, 2),
    manager_id INT
);
```

**Example Data:**
```sql
INSERT INTO employees (id, name, salary, manager_id) VALUES (1, 'Alice', 50000, NULL);
INSERT INTO employees (id, name, salary, manager_id) VALUES (2, 'Bob', 60000, 1);
INSERT INTO employees (id, name, salary, manager_id) VALUES (3, 'Charlie', 70000, 1);
```

**Answer:**

```sql
SELECT e1.name AS employee_name, e2.name AS manager_name
FROM employees e1
JOIN employees e2 ON e1.manager_id = e2.id
WHERE e1.salary > e2.salary;
```

### 6. **Find departments with the highest number of employees**

**Question:**
Write a query to find which departments have the highest number of employees.

**Answer:**

```sql
SELECT department_id, COUNT(*) AS employee_count
FROM employees
GROUP BY department_id
HAVING COUNT(*) = (
    SELECT MAX(employee_count)
    FROM (
        SELECT department_id, COUNT(*) AS employee_count
        FROM employees
        GROUP BY department_id
    ) AS dept_counts
);
```

### 7. **Find employees who joined in the last 30 days**

**Question:**
Assume an `employees` table with a `join_date` column. Write a query to find employees who joined in the last 30 days.

**Table Structure:**
```sql
CREATE TABLE employees (
    id INT PRIMARY KEY,
    name VARCHAR(100),
    join_date DATE
);
```

**Example Data:**
```sql
INSERT INTO employees (id, name, join_date) VALUES (1, 'Alice', CURDATE() - INTERVAL 10 DAY);
INSERT INTO employees (id, name, join_date) VALUES (2, 'Bob', CURDATE() - INTERVAL 40 DAY);
```

**Answer:**

```sql
SELECT name
FROM employees
WHERE join_date >= CURDATE() - INTERVAL 30 DAY;
```

### 8. **List the top 3 highest salaries**

**Question:**
Write a query to list the top 3 highest salaries from the `employees` table.

**Answer:**

```sql
SELECT DISTINCT salary
FROM employees
ORDER BY salary DESC
LIMIT 3;
```

### 9. **Find the employees who have the same salary**

**Question:**
Write a query to find employees who have the same salary as at least one other employee.

**Answer:**

```sql
SELECT e1.name, e1.salary
FROM employees e1
JOIN employees e2 ON e1.salary = e2.salary
WHERE e1.id <> e2.id;
```

### 10. **Retrieve the names of employees who report to the same manager**

**Question:**
Write a query to retrieve names of employees who report to the same manager.

**Answer:**

```sql
SELECT e1.name AS employee_name, e2.name AS manager_name
FROM employees e1
JOIN employees e2 ON e1.manager_id = e2.id
WHERE e1.manager_id IN (
    SELECT manager_id
    FROM employees
    GROUP BY manager_id
    HAVING COUNT(*) > 1
);
```

