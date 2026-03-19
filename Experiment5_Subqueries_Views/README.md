# Experiment 5: Subqueries and Views

## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```

**Question 1**
--
-- Write a SQL query that retrieves the names of students and their corresponding grades, where the grade is equal to the minimum grade achieved in each subject.

Sample table: GRADES
```sql
SELECT g.student_name, g.grade
FROM GRADES g
WHERE g.grade = (
    SELECT MIN(g2.grade)
    FROM GRADES g2
    WHERE g2.subject = g.subject
);

```

**Output:**

<img width="961" height="522" alt="image" src="https://github.com/user-attachments/assets/5281894d-b16a-4d82-995f-03d8e4f40532" />


**Question 2**
---
--From the following tables, write a SQL query to determine the commission of the salespeople in Paris. Return commission.
```sql
SELECT DISTINCT commission
FROM salesman
WHERE city = 'Paris';

```

**Output:**

<img width="624" height="420" alt="image" src="https://github.com/user-attachments/assets/c434a1fe-ebf5-44f8-bcd2-3af47241c962" />


**Question 3**
---
-- Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is greater than $4500.

Sample table: CUSTOMERS

```sql
SELECT *
FROM CUSTOMERS
WHERE SALARY > 4500;

```

**Output:**

<img width="1281" height="544" alt="image" src="https://github.com/user-attachments/assets/7bd9eb98-fcb2-43c0-b20b-effa0c7fc1ca" />


**Question 4**
---
-- Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose Address as Delhi

Sample table: CUSTOMERS

```sql
SELECT *
FROM CUSTOMERS
WHERE ADDRESS = 'Delhi';

```

**Output:**

<img width="1250" height="452" alt="image" src="https://github.com/user-attachments/assets/a67ee3cc-d759-4f95-8272-d702e84fc268" />


**Question 5**
---
-- Write a SQL query to List departments with names longer than the average length

```sql
SELECT department_id, department_name
FROM Departments
WHERE LENGTH(department_name) > (
    SELECT AVG(LENGTH(department_name))
    FROM Departments
);

```

**Output:**

<img width="909" height="506" alt="image" src="https://github.com/user-attachments/assets/ed28178a-0318-439a-9247-9d78d9134f69" />


**Question 6**
---
-- Write a SQL query to Identify customers whose city is different from the city of the customer with the highest ID

SAMPLE TABLE: customer

```sql
SELECT *
FROM customer
WHERE city != (
    SELECT city
    FROM customer
    ORDER BY id DESC
    LIMIT 1
);

```

**Output:**

<img width="1258" height="612" alt="image" src="https://github.com/user-attachments/assets/3647af8c-d929-40a0-85f5-21b4446ccc9f" />



**Question 7**
---
-- Write a SQL query to Retrieve the names and cities of customers who have the same city as customers with IDs 3 and 7

SAMPLE TABLE: customer

```sql
SELECT name, city
FROM customer
WHERE city IN (
    SELECT city
    FROM customer
    WHERE id IN (3, 7)
);

```

**Output:**

<img width="927" height="548" alt="image" src="https://github.com/user-attachments/assets/4f74c555-0bfc-4131-a194-71bb9de3a8dc" />


**Question 8**
---
-- Write a SQL query to Retrieve the medications with dosages equal to the highest dosage

Medications Table

```sql
SELECT *
FROM Medications
WHERE dosage = (
    SELECT MAX(dosage)
    FROM Medications
);

```

**Output:**

<img width="1126" height="529" alt="image" src="https://github.com/user-attachments/assets/d719a2c8-6653-471b-b212-1bca75cdeac9" />


**Question 9**
---
-- Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is LESS than $2500.

Sample table: CUSTOMERS

```sql
SELECT *
FROM CUSTOMERS
WHERE SALARY < 2500;

```

**Output:**

<img width="1285" height="559" alt="image" src="https://github.com/user-attachments/assets/9d15bc03-b7c5-480e-96aa-fb65da563fb7" />


**Question 10**
---
-- Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is greater than $1500.

Sample table: CUSTOMERS

```sql
SELECT *
FROM CUSTOMERS
WHERE SALARY > 1500;

```

**Output:**

<img width="1261" height="721" alt="image" src="https://github.com/user-attachments/assets/581ce1b2-7370-4022-b03a-f92da1b6a1a7" />



## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
