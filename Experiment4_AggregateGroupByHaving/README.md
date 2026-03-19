# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**
--
-- Write a SQL query to find Who has the highest income among employee living in California?

Table: employee

```sql
SELECT name, MAX(income) AS "max(income)"
FROM employee
WHERE city = 'California'
GROUP BY name
HAVING MAX(income) = (
    SELECT MAX(income)
    FROM employee
    WHERE city = 'California'
);

```

**Output:**

<img width="891" height="426" alt="image" src="https://github.com/user-attachments/assets/491c99e6-d1c5-44d1-912a-eea44474242d" />


**Question 2**
---
-- Write a SQL query to calculate total purchase amount of all orders. Return total purchase amount.

Sample table: orders

```sql
SELECT SUM(purch_amt) AS TOTAL
FROM orders;

```

**Output:**

<img width="621" height="410" alt="image" src="https://github.com/user-attachments/assets/4fcabd22-bce2-41a7-8133-bee66f54fc00" />


**Question 3**
---
-- Write a SQL query to find the minimum purchase amount.

Sample table: orders

```sql
SELECT MIN(purch_amt) AS MINIMUM
FROM orders;

```

**Output:**

<img width="770" height="387" alt="image" src="https://github.com/user-attachments/assets/0ca9b109-9b28-4ba0-9e15-2071b56248f9" />


**Question 4**
---
-- How many male and female doctors are there in each medical specialty?

Sample table:Doctors Table

```sql
SELECT 
    Specialty,
    Gender,
    COUNT(*) AS TotalDoctors
FROM Doctors
GROUP BY Specialty, Gender
ORDER BY Specialty, Gender;

```

**Output:**

<img width="1350" height="737" alt="image" src="https://github.com/user-attachments/assets/0c489da0-5513-498f-aa46-d8d1431c84db" />


**Question 5**
---
--What is the most common diagnosis among patients?

Sample table:MedicalRecords Table

```sql
SELECT Diagnosis, COUNT(*) AS DiagnosisCount
FROM MedicalRecords
GROUP BY Diagnosis
ORDER BY COUNT(*) DESC
LIMIT 1;

```

**Output:**

<img width="1068" height="439" alt="image" src="https://github.com/user-attachments/assets/66441429-fd6b-4477-9eca-df4562cc7aa4" />


**Question 6**
---
-- Write SQL query to extract the email domain from each patient's email address and count the number of patients with the same email domain.

Sample table: Patients Table

```sql
SELECT 
    SUBSTR(email, INSTR(email, '@') + 1) AS EmailDomain,
    COUNT(*) AS TotalPatients
FROM Patients
GROUP BY SUBSTR(email, INSTR(email, '@') + 1);

```

**Output:**

<img width="903" height="488" alt="image" src="https://github.com/user-attachments/assets/2f8cfaa2-b260-4b7b-900c-7c67a1d972d8" />


**Question 7**
---
--Write the SQL query that accomplishes the selection of product which has lowest price in each category from the "products" table and includes only those products where the minimum price is less than 10.

Sample table: products

```sql
SELECT category_id, MIN(price) AS Price
FROM products
GROUP BY category_id
HAVING MIN(price) < 10;

```

**Output:**

<img width="964" height="466" alt="image" src="https://github.com/user-attachments/assets/f89e30cc-6989-43d7-91a8-3b9d20723b03" />


**Question 8**
---
--Which cities (addresses) in the "customer1" table have an average salary lesser than Rs. 15000

Sample table: customer1
```sql
SELECT address, AVG(salary) AS "AVG(salary)"
FROM customer1
GROUP BY address
HAVING AVG(salary) < 15000;

```

**Output:**

<img width="879" height="715" alt="image" src="https://github.com/user-attachments/assets/3bb7eed7-51ae-4ad4-8c02-946441cb5938" />

**Question 9**
---
-- Write the SQL query that achieves the grouping of data by city, calculates the average income for each city, and includes only those cities where the average income is greater than 500,000.

Sample table: employee

```sql
SELECT city, AVG(income) AS "AVG(income)"
FROM employee
GROUP BY city
HAVING AVG(income) > 500000;

```

**Output:**

<img width="1002" height="553" alt="image" src="https://github.com/user-attachments/assets/a1140b0e-9629-4558-b01a-6c20c9727525" />


**Question 10**
---
-- Write the SQL query that performs grouping by age groups and displays the maximum salary for each group, excluding groups where the maximum salary is not greater than 8000. 

Note: Calculate the age group as multiples of 5.

Eg., 20,22,23 comes in age group 20. 

25,27,29 comes in age group 25.

Sample table: customer1

```sql
SELECT 
    (age / 5) * 5 AS age_group,
    MAX(salary) AS "MAX(salary)"
FROM customer1
GROUP BY (age / 5) * 5
HAVING MAX(salary) > 8000;

```

**Output:**

<img width="933" height="457" alt="image" src="https://github.com/user-attachments/assets/9dd477ff-2178-40fb-b888-74256dab34fe" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
