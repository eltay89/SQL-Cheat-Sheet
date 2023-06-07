# SQL Cheat Sheet

## Table of Contents
- [SELECT statement](#select-statement)
- [SELECT statement with WHERE clause](#select-statement-with-where-clause)
- [SELECT statement with ORDER BY clause](#select-statement-with-order-by-clause)
- [INSERT statement](#insert-statement)
- [UPDATE statement](#update-statement)
- [DELETE statement](#delete-statement)
- [JOIN statement](#join-statement)
- [GROUP BY statement](#group-by-statement)
- [HAVING statement](#having-statement)
- [SubQueries](#subqueries)

## Illustrations
(Add any relevant images or diagrams here)

## Scope of Functionalities
This cheat sheet covers the following SQL functionalities:
- Retrieving data from a table with SELECT statements
- Filtering data with WHERE clauses
- Sorting data with ORDER BY clauses
- Inserting data with INSERT statements
- Modifying existing data with UPDATE statements
- Deleting data with DELETE statements
- Combining data from multiple tables with JOIN statements
- Grouping data with GROUP BY statements
- Filtering grouped data with HAVING statements

## Examples of Use
Here are some examples of using SQL statements:

### SELECT statement
Retrieve all columns from the "employees" table:
```sql
SELECT * FROM employees;
```

###  SELECT statement with WHERE clause
Retrieve all columns from the "employees" table where the salary is greater than 50000:
```sql
SELECT * FROM employees
WHERE salary > 50000;
```

### SELECT statement with ORDER BY clause
Retrieve all columns from the "employees" table sorted by last name in descending order:
```sql
SELECT * FROM employees
ORDER BY last_name DESC;
```
### INSERT statement
Insert a new row into the "employees" table:
```sql
INSERT INTO employees (first_name, last_name, salary)
VALUES ('John', 'Doe', 60000);
```
### UPDATE statement
Update the salary of an employee in the "employees" table:
```sql
UPDATE employees
SET salary = 65000
WHERE employee_id = 123;
```
### DELETE statement
Delete an employee from the "employees" table:
```sql
DELETE FROM employees
WHERE employee_id = 123;
```

### JOIN statement
Retrieve all columns from the "employees" and "departments" tables where the employee's department_id matches the department's department_id:
```sql
SELECT * FROM employees
JOIN departments
ON employees.department_id = departments.department_id;
```

### GROUP BY statement
Group employees by department and count the number of employees in each department:
```sql
SELECT department_id, COUNT(*) as num_employees
FROM employees
GROUP BY department_id;
```

### HAVING statement
Retrieve departments with more than 5 employees:
```sql
SELECT department_id, COUNT(*) as num_employees
FROM employees
GROUP BY department_id
HAVING COUNT(*) > 5;
```

## SubQueries

A subquery is a query within another query. It is embedded within the WHERE or HAVING clause of the main query.

### Use subqueries in the WHERE clause to:

- Filter rows based on values from another table:

```sql
SELECT * FROM customers 
WHERE country IN (SELECT country FROM countries WHERE region = 'Europe');
```

- Filter rows based on an aggregate value from another table:

```sql 
SELECT * FROM products 
WHERE price > (SELECT AVG(price) FROM products);
```

- Filter rows that have matches in another table:

```sql
SELECT * FROM customers 
WHERE EXISTS (SELECT 1 FROM orders WHERE orders.customer_id = customers.id); 
``` 

### Use subqueries in the FROM clause to:

- Treat the subquery results as a temporary table:

```sql
SELECT * FROM (SELECT * FROM products WHERE price > 10) AS expensive_products;
```

- Join the subquery results with another table:

```sql
SELECT * FROM customers 
JOIN (SELECT * FROM orders WHERE total > 100) AS big_orders 
ON customers.id = big_orders.customer_id;
```

### Use subqueries in the SELECT clause to:  

- Include an aggregate value from another table: 

```sql
SELECT name, (SELECT MAX(age) FROM users) AS max_age 
FROM groups; 
```

- Include values from another table that depend on the main query:

```sql
SELECT name, 
(SELECT COUNT(*) FROM products WHERE products.group_id = groups.id) AS product_count 
FROM groups;
```

### Project Status
This SQL cheat sheet is complete and is suitable for use as a quick reference guide.
This cheat sheet was created by Mohamed ELtay and is based on personal experience and various SQL resources.
Feel free to suggest improvements or corrections via pull requests or issues.

# Employees Table
```
employee_id	first_name	last_name	salary	department_id
    123	        John	         Doe	        60000	       1
    456	        Jane	         Smith	        75000          2
    789	        Bob	         Johnson
```
