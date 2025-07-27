# 🗄️ SQL Fundamentals - Complete Beginner's Guide

> *Structured Query Language (SQL) - Your gateway to database mastery*

---

## 📋 Table of Contents

- [🎯 Introduction](#-introduction)
- [💾 Database Management Systems (DBMS)](#-database-management-systems-dbms)
- [🔧 CRUD Operations](#-crud-operations)
- [📝 SQL Statements](#-sql-statements)
- [🏗️ Data Types & Constraints](#️-data-types--constraints)
- [📊 Advanced Concepts](#-advanced-concepts)
- [🔍 Performance & Security](#-performance--security)

---

## 🎯 Introduction

**SQL** (Structured Query Language) is the universal language for communicating with databases. It enables you to:

- 📥 **Retrieve** data from databases
- ➕ **Insert** new records
- ✏️ **Update** existing information  
- 🗑️ **Delete** unwanted data

### Why Learn SQL?

- 🌐 **Universal**: Used across websites, mobile apps, and enterprise systems
- 🔤 **Simple**: English-like commands make it beginner-friendly
- 💼 **Essential**: Critical skill for data management and analysis

---

## 💾 Database Management Systems (DBMS)

A **DBMS** is software that enables users to interact with databases, providing an interface to define, create, and manage data.

### Popular DBMS Options

| DBMS | Best For | Key Features |
|------|----------|--------------|
| 🐬 **MySQL** | Web applications | Open-source, fast |
| 🐘 **PostgreSQL** | Complex queries | Advanced features, extensible |
| 🏢 **Oracle** | Enterprise | Robust, scalable |
| 🪟 **SQL Server** | Microsoft ecosystem | Integration, security |
| 🪶 **SQLite** | Mobile/embedded | Lightweight, serverless |

### Relational Databases

```
┌─────────────┐    ┌─────────────┐    ┌─────────────┐
│   CUSTOMERS │    │   ORDERS    │    │  PRODUCTS   │
├─────────────┤    ├─────────────┤    ├─────────────┤
│ customer_id │    │ order_id    │    │ product_id  │
│ name        │    │ customer_id │    │ name        │
│ email       │    │ product_id  │    │ price       │
│ city        │    │ quantity    │    │ category    │
└─────────────┘    └─────────────┘    └─────────────┘
```

**Key Concepts:**
- 📋 **Tables**: Store data in rows and columns
- 📄 **Records**: Each row represents an entity instance
- 🏷️ **Attributes**: Columns contain entity properties

---

## 🔧 CRUD Operations

The four fundamental database operations:

```mermaid
graph LR
    A[🆕 CREATE] --> B[📖 READ]
    B --> C[✏️ UPDATE]
    C --> D[🗑️ DELETE]
    D --> A
```

| Operation | Purpose | SQL Command |
|-----------|---------|-------------|
| **CREATE** | Insert new records | `INSERT` |
| **READ** | Retrieve data | `SELECT` |
| **UPDATE** | Modify existing records | `UPDATE` |
| **DELETE** | Remove records | `DELETE` |

---

## 📝 SQL Statements

### 🔍 SELECT Statement
*Retrieve data from the database*

**Basic Syntax:**
```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

**📝 Explanation:**
- `SELECT`: Specifies which columns to retrieve
- `FROM`: Indicates the source table
- `WHERE`: Filters rows based on conditions (optional)

**💡 Examples with Explanations:**

```sql
-- Example 1: Select specific columns
SELECT name, email, city
FROM customers;
```
*This retrieves only the name, email, and city columns from all customer records.*

```sql
-- Example 2: Select with WHERE condition
SELECT name, email
FROM customers
WHERE city = 'New York' AND age > 25;
```
*This finds customers who live in New York AND are older than 25 years.*

```sql
-- Example 3: Select all columns
SELECT *
FROM products
WHERE price BETWEEN 10.00 AND 50.00;
```
*The asterisk (*) selects all columns from products with prices between $10 and $50.*

```sql
-- Example 4: Using LIKE for pattern matching
SELECT name, phone
FROM customers
WHERE name LIKE 'John%';
```
*This finds all customers whose names start with 'John' (% is a wildcard).*

### ➕ INSERT Statement
*Add new records to a table*

**Basic Syntax:**
```sql
INSERT INTO table_name (column1, column2, ...)
VALUES (value1, value2, ...);
```

**📝 Explanation:**
- `INSERT INTO`: Specifies the target table
- `(column1, column2, ...)`: Lists the columns to insert data into
- `VALUES`: Provides the actual data values in the same order

**💡 Examples with Explanations:**

```sql
-- Example 1: Insert single record
INSERT INTO customers (name, email, city, age)
VALUES ('John Doe', 'john@email.com', 'Boston', 30);
```
*This adds a new customer with all specified details.*

```sql
-- Example 2: Insert multiple records at once
INSERT INTO products (name, price, category)
VALUES 
    ('Laptop', 999.99, 'Electronics'),
    ('Book', 19.99, 'Education'),
    ('Coffee Mug', 12.50, 'Kitchenware');
```
*This efficiently adds three products in a single statement.*

```sql
-- Example 3: Insert with partial data (other columns get default values)
INSERT INTO customers (name, email)
VALUES ('Jane Smith', 'jane@email.com');
```
*City and age columns will be NULL or use default values if defined.*

### ✏️ UPDATE Statement
*Modify existing records*

**Basic Syntax:**
```sql
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```

**📝 Explanation:**
- `UPDATE`: Specifies the table to modify
- `SET`: Defines which columns to change and their new values
- `WHERE`: Crucial! Specifies which rows to update (without it, ALL rows are updated)

**💡 Examples with Explanations:**

```sql
-- Example 1: Update single column for specific record
UPDATE customers
SET city = 'Chicago'
WHERE name = 'John Doe';
```
*This changes John Doe's city to Chicago. Only his record is affected.*

```sql
-- Example 2: Update multiple columns
UPDATE products
SET price = 899.99, category = 'Electronics - Sale'
WHERE name = 'Laptop';
```
*This updates both price and category for the laptop product.*

```sql
-- Example 3: Update based on condition
UPDATE employees
SET salary = salary * 1.10
WHERE department = 'Sales' AND performance_rating >= 4;
```
*This gives a 10% raise to sales employees with high performance ratings.*

```sql
-- Example 4: Update using calculations
UPDATE orders
SET total_amount = quantity * unit_price
WHERE order_date = '2024-01-15';
```
*This calculates and updates the total amount for orders from a specific date.*

### 🗑️ DELETE Statement
*Remove records from a table*

**Basic Syntax:**
```sql
DELETE FROM table_name
WHERE condition;
```

**📝 Explanation:**
- `DELETE FROM`: Specifies the table to delete from
- `WHERE`: Critical condition to specify which rows to delete
- ⚠️ **Warning**: Without WHERE, ALL records will be deleted!

**💡 Examples with Explanations:**

```sql
-- Example 1: Delete specific record
DELETE FROM customers
WHERE email = 'old@email.com';
```
*This removes the customer with the specified email address.*

```sql
-- Example 2: Delete based on multiple conditions
DELETE FROM orders
WHERE order_date < '2023-01-01' AND status = 'cancelled';
```
*This removes old cancelled orders from before 2023.*

```sql
-- Example 3: Delete using subquery
DELETE FROM products
WHERE category_id IN (
    SELECT id FROM categories WHERE name = 'Discontinued'
);
```
*This removes all products in discontinued categories.*

```sql
-- Example 4: Safe deletion with LIMIT (MySQL)
DELETE FROM logs
WHERE created_date < '2023-01-01'
LIMIT 1000;
```
*This safely deletes old logs in batches of 1000 records.*

### 🔗 JOIN Statement
*Combine rows from multiple tables*

**Basic Syntax:**
```sql
SELECT columns
FROM table1
JOIN table2 ON table1.column = table2.column;
```

**📝 Explanation:**
- `JOIN`: Combines data from multiple tables
- `ON`: Specifies the relationship condition between tables
- Different JOIN types determine which records are included

**💡 Examples with Detailed Explanations:**

#### INNER JOIN
```sql
-- Example 1: Get customer names with their order details
SELECT c.name, c.email, o.order_date, o.total_amount
FROM customers c
INNER JOIN orders o ON c.customer_id = o.customer_id;
```
*This returns only customers who have placed orders. Customers without orders are excluded.*

#### LEFT JOIN
```sql
-- Example 2: Get all customers and their orders (if any)
SELECT c.name, c.email, o.order_date, o.total_amount
FROM customers c
LEFT JOIN orders o ON c.customer_id = o.customer_id;
```
*This returns ALL customers, even those who haven't placed any orders (order columns will be NULL).*

#### Multiple JOINs
```sql
-- Example 3: Join three tables
SELECT 
    c.name as customer_name,
    p.name as product_name,
    oi.quantity,
    oi.unit_price
FROM customers c
INNER JOIN orders o ON c.customer_id = o.customer_id
INNER JOIN order_items oi ON o.order_id = oi.order_id
INNER JOIN products p ON oi.product_id = p.product_id
WHERE o.order_date >= '2024-01-01';
```
*This complex query shows what products each customer bought in 2024.*

#### Self JOIN
```sql
-- Example 4: Find employees and their managers
SELECT 
    e.name as employee_name,
    m.name as manager_name
FROM employees e
LEFT JOIN employees m ON e.manager_id = m.employee_id;
```
*This joins the employees table with itself to show the management hierarchy.*

---

## 🏗️ Data Types & Constraints

### 📊 Common Data Types

| Data Type | Description | Example |
|-----------|-------------|---------|
| `INTEGER` | Whole numbers | `42`, `1000` |
| `VARCHAR(n)` | Variable-length strings | `'Hello World'` |
| `DATE` | Date values | `'2024-01-15'` |
| `BOOLEAN` | True/false values | `TRUE`, `FALSE` |
| `DECIMAL(p,s)` | Fixed-point numbers | `123.45` |

### 🔒 Constraints

```sql
CREATE TABLE users (
    id INTEGER PRIMARY KEY,           -- 🔑 Unique identifier
    email VARCHAR(255) UNIQUE,        -- 🎯 No duplicates
    name VARCHAR(100) NOT NULL,       -- ❗ Required field
    age INTEGER CHECK (age >= 18),    -- ✅ Validation rule
    department_id INTEGER,
    FOREIGN KEY (department_id)       -- 🔗 References another table
        REFERENCES departments(id)
);
```

**Constraint Types:**
- 🔑 **PRIMARY KEY**: Ensures uniqueness and identifies records
- 🔗 **FOREIGN KEY**: Maintains relationships between tables
- ❗ **NOT NULL**: Column must have a value
- 🎯 **UNIQUE**: Ensures unique values in column
- ✅ **CHECK**: Validates data against conditions

---

## 📊 Advanced Concepts

### 📈 Aggregate Functions & GROUP BY

**Basic Syntax:**
```sql
SELECT column1, AGGREGATE_FUNCTION(column2)
FROM table_name
GROUP BY column1
HAVING condition;
```

**📝 Explanation:**
- `GROUP BY`: Groups rows with same values in specified columns
- `AGGREGATE_FUNCTION`: Performs calculations on grouped data
- `HAVING`: Filters groups (like WHERE but for grouped data)

**💡 Examples with Detailed Explanations:**

#### Basic Aggregate Functions
```sql
-- Example 1: Calculate summary statistics
SELECT 
    COUNT(*) as total_customers,
    AVG(age) as average_age,
    MAX(age) as oldest_customer,
    MIN(age) as youngest_customer,
    SUM(total_purchases) as total_revenue
FROM customers;
```
*This provides a statistical overview of your customer base.*

#### GROUP BY with Aggregates
```sql
-- Example 2: Sales by department
SELECT 
    department,
    COUNT(*) as employee_count,
    AVG(salary) as avg_salary,
    MAX(salary) as highest_salary
FROM employees
GROUP BY department
ORDER BY avg_salary DESC;
```
*This shows staffing and salary statistics for each department, ordered by average salary.*

#### HAVING Clause
```sql
-- Example 3: Find departments with high average salaries
SELECT 
    department,
    COUNT(*) as employee_count,
    AVG(salary) as avg_salary
FROM employees
GROUP BY department
HAVING AVG(salary) > 50000 AND COUNT(*) >= 5;
```
*This finds departments with at least 5 employees and average salary above $50,000.*

#### Complex Grouping
```sql
-- Example 4: Monthly sales analysis
SELECT 
    YEAR(order_date) as year,
    MONTH(order_date) as month,
    COUNT(order_id) as total_orders,
    SUM(total_amount) as monthly_revenue,
    AVG(total_amount) as avg_order_value
FROM orders
WHERE order_date >= '2023-01-01'
GROUP BY YEAR(order_date), MONTH(order_date)
ORDER BY year DESC, month DESC;
```
*This provides monthly sales performance metrics for business analysis.*

### 🔢 ORDER BY Clause

**Basic Syntax:**
```sql
SELECT columns
FROM table_name
ORDER BY column1 [ASC|DESC], column2 [ASC|DESC];
```

**📝 Explanation:**
- `ORDER BY`: Sorts the result set
- `ASC`: Ascending order (default, A-Z, 1-10)
- `DESC`: Descending order (Z-A, 10-1)
- Multiple columns create nested sorting

**💡 Examples with Detailed Explanations:**

```sql
-- Example 1: Simple sorting
SELECT name, salary, department
FROM employees
ORDER BY salary DESC;
```
*This lists employees from highest to lowest salary.*

```sql
-- Example 2: Multiple column sorting
SELECT name, department, salary, hire_date
FROM employees
ORDER BY department ASC, salary DESC, hire_date ASC;
```
*This sorts by department first (A-Z), then by salary within each department (high to low), then by hire date (oldest first).*

```sql
-- Example 3: Sorting with aggregate functions
SELECT 
    department,
    COUNT(*) as employee_count,
    AVG(salary) as avg_salary
FROM employees
GROUP BY department
ORDER BY avg_salary DESC, employee_count DESC;
```
*This ranks departments by average salary, with larger departments ranked higher in case of ties.*

```sql
-- Example 4: Using column positions
SELECT name, salary, department
FROM employees
ORDER BY 2 DESC, 1 ASC;
```
*This sorts by the 2nd column (salary) descending, then 1st column (name) ascending.*

### 🔍 Subqueries (Nested Queries)

**Basic Syntax:**
```sql
SELECT columns
FROM table_name
WHERE column OPERATOR (
    SELECT column
    FROM another_table
    WHERE condition
);
```

**📝 Explanation:**
- **Inner query** executes first and returns a result
- **Outer query** uses the inner query's result
- Can be used in WHERE, SELECT, FROM, or HAVING clauses

**💡 Examples with Detailed Explanations:**

#### WHERE Clause Subquery
```sql
-- Example 1: Find employees earning above average
SELECT name, salary, department
FROM employees
WHERE salary > (
    SELECT AVG(salary)
    FROM employees
);
```
*The inner query calculates the average salary, then the outer query finds employees earning more than that average.*

#### IN Operator with Subquery
```sql
-- Example 2: Find customers who have placed orders
SELECT name, email, city
FROM customers
WHERE customer_id IN (
    SELECT DISTINCT customer_id
    FROM orders
    WHERE order_date >= '2024-01-01'
);
```
*This finds customers who have ordered something this year.*

#### EXISTS Operator
```sql
-- Example 3: Find products that have been ordered
SELECT product_name, price, category
FROM products p
WHERE EXISTS (
    SELECT 1
    FROM order_items oi
    WHERE oi.product_id = p.product_id
);
```
*EXISTS is efficient for checking if related records exist without returning actual data.*

#### Subquery in SELECT Clause
```sql
-- Example 4: Add calculated columns
SELECT 
    name,
    salary,
    department,
    (SELECT AVG(salary) FROM employees e2 WHERE e2.department = e1.department) as dept_avg_salary,
    salary - (SELECT AVG(salary) FROM employees e3 WHERE e3.department = e1.department) as salary_diff
FROM employees e1;
```
*This shows each employee's salary compared to their department's average salary.*

### 👁️ Views
*Virtual tables for simplified access*

```sql
CREATE VIEW high_earners AS
SELECT name, salary, department
FROM employees
WHERE salary > 50000;
```

---

## 🔍 Performance & Security

### ⚡ Indexes
*Speed up data retrieval*

```sql
CREATE INDEX idx_customer_email ON customers(email);
CREATE INDEX idx_order_date ON orders(order_date);
```

### 💼 Transactions
*Ensure data integrity with ACID properties*

```sql
BEGIN TRANSACTION;
    UPDATE accounts SET balance = balance - 100 WHERE id = 1;
    UPDATE accounts SET balance = balance + 100 WHERE id = 2;
COMMIT;
```

**ACID Properties:**
- ⚛️ **Atomicity**: All operations succeed or all fail
- 🔄 **Consistency**: Database remains in valid state
- 🔒 **Isolation**: Concurrent transactions don't interfere
- 💾 **Durability**: Committed changes persist

### 📦 Stored Procedures
*Precompiled SQL code for better performance*

```sql
CREATE PROCEDURE GetCustomerOrders(@customer_id INT)
AS
BEGIN
    SELECT * FROM orders 
    WHERE customer_id = @customer_id;
END
```

### ⚡ Triggers
*Automatic responses to database events*

```sql
CREATE TRIGGER update_last_modified
    BEFORE UPDATE ON customers
    FOR EACH ROW
BEGIN
    SET NEW.last_modified = NOW();
END;
```

### 🎯 Normalization
*Organize data to eliminate redundancy*

```
First Normal Form (1NF)   →   Second Normal Form (2NF)   →   Third Normal Form (3NF)
┌─────────────────────┐       ┌─────────────────────┐       ┌─────────────────────┐
│ Eliminate repeating │   →   │ Remove partial key  │   →   │ Remove transitive   │
│ groups              │       │ dependencies        │       │ dependencies        │
└─────────────────────┘       └─────────────────────┘       └─────────────────────┘
```

---

## 🎓 Key Takeaways

> 💡 **Remember**: Every SQL statement ends with a semicolon (`;`)

✅ **Master these fundamentals:**
- Understand CRUD operations
- Practice basic SQL statements
- Learn about data types and constraints
- Explore advanced features like joins and subqueries
- Consider performance with indexes and transactions

---

## 🚀 Next Steps

1. **Practice**: Try these commands on a real database
2. **Experiment**: Create your own tables and relationships  
3. **Learn More**: Explore specific DBMS documentation
4. **Build Projects**: Apply SQL in real-world scenarios

---

*🎯 SQL is the foundation of data management - master it to unlock powerful data insights!*
