# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**
--
-- Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name"), with an inner join on the "doctor_id" column and conditions filtering for patients whose doctor has the first name 'Emily', last name 'Johnson', and a non-null discharge date.

```sql
select p.first_name as patient_name
from patients p
join doctors d on p.doctor_id=d.doctor_id
where d.first_name='Emily'
and d.last_name='Johnson'
and p.discharge_date is not null;
```

**Output:**

<img width="692" height="501" alt="image" src="https://github.com/user-attachments/assets/87221565-afdc-4e31-aa7a-c65edcca03e5" />


**Question 2**
---
-- From the following tables write a SQL query to find those customers with a grade less than 300. Return cust_name, customer city, grade, Salesman, salesmancity. The result should be ordered by ascending customer_id. 

```sql
select c.cust_name,
c.city,c.grade,s.name as "Salesman",
s.city
from customer c
join salesman s on c.salesman_id=s.salesman_id
where c.grade<300
order by c.customer_id asc;
```

**Output:**

<img width="1241" height="802" alt="image" src="https://github.com/user-attachments/assets/f7372214-e5d2-4d91-8b57-bb0d391f2315" />


**Question 3**
---
--Write the SQL query that achieves the selection of all columns from the "customer" table (aliased as "c"), with a left join on the "customer_id" column and a condition filtering for orders with an order date later than '2012-08-17'.

```sql
select c.*
from customer c
left join orders o on c.customer_id=o.customer_id
where o.ord_date>'2012-08-17';
```

**Output:**

<img width="1262" height="855" alt="image" src="https://github.com/user-attachments/assets/c97bc98e-0596-4327-be8f-ca5bb165735d" />

**Question 4**
---
--Write the SQL query that accomplishes the selection of the first name from the "patients" table (aliased as "patient_name") and the first name from the "doctors" table (aliased as "doctor_name"), with an inner join on the "doctor_id" column and a condition filtering for patients with a non-null discharge date.

```sql
select p.first_name as patient_name,
d.first_name as doctor_name
from patients p
join doctors d on p.doctor_id=d.doctor_id
where p.discharge_date is not null;
```

**Output:**

<img width="1036" height="506" alt="image" src="https://github.com/user-attachments/assets/4e7065b7-6fd7-4cc6-b8cb-62f87d96a5c5" />


**Question 5**
---
-- Write the SQL query that achieves the selection of all columns from the "nurses" table (aliased as "n"), with an inner join on the "department_id" column and a condition filtering for nurses in the 'Pediatrics' department.

```sql
select n.*
from nurses n
join departments d on n.department_id=d.department_id
where d.department_name ='Pediatrics';
```

**Output:**

<img width="1336" height="520" alt="image" src="https://github.com/user-attachments/assets/678cfec8-b121-487e-9c9a-72c47b8af8a9" />


**Question 6**
---
-- Write the SQL query that achieves the selection of the first name from the "patients" table, with an inner join on the "patient_id" column and a condition filtering for surgeries with a surgery date of '2024-01-15'.:

```sql
select p.first_name
from patients p
join surgeries s on p.patient_id=s.patient_id
where s.surgery_date='2024-01-15';
```

**Output:**

<img width="664" height="501" alt="image" src="https://github.com/user-attachments/assets/2e2bdd66-d41f-4ce6-be92-514a3e8d8d11" />


**Question 7**
---
-- From the following tables write a SQL query to find salespeople who received commissions of more than 12 percent from the company. Return Customer Name, customer city, Salesman, commission.  

```sql
select c.cust_name as "Customer Name",c.city,
s.name as "Salesman",
s.commission
from customer c
join salesman s on c.salesman_id=s.salesman_id
where s.commission>0.12;
```

**Output:**

<img width="1298" height="719" alt="image" src="https://github.com/user-attachments/assets/ee381a92-e5d4-412b-b385-3f64f22b09bd" />


**Question 8**
---
-- Write the SQL query that achieves the selection of the "cust_name" and "city" columns from the "customer" table (aliased as "c"), and the "ord_no," "ord_date," and "purch_amt" columns from the "orders" table (aliased as "o"), with a left join on the "customer_id" column and a condition filtering for customers in the city 'London'.

```sql
select c.cust_name,
c.city,
o.ord_no,
o.ord_date,
o.purch_amt
from customer c
left join orders o on c.customer_id = o.customer_id
where c.city='London';
```

**Output:**

<img width="1311" height="612" alt="image" src="https://github.com/user-attachments/assets/56216aa0-0b9a-4ca8-8662-b915f12130e8" />


**Question 9**
---
-- Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and the first name from the "doctors" table (aliased as "doctor_name"), with an inner join on the "doctor_id" column and a condition filtering for patients with a null discharge date.

```sql
select p.first_name as patient_name,
d.first_name as doctor_name
from patients p
inner join doctors d on p.doctor_id =d.doctor_id
where p.discharge_date is null;

```

**Output:**

<img width="984" height="578" alt="image" src="https://github.com/user-attachments/assets/e180296f-efc9-4cfd-96f6-46cc2cdc1dc2" />


**Question 10**
---
-- Write the SQL query that achieves the selection of the "cust_name" column from the "customer" table (aliased as "c"), with a left join on the "customer_id" column and a condition filtering for orders with a purchase amount less than 100.

```sql
select c.cust_name
from customer c
left join orders o on c.customer_id = o.customer_id
where o.purch_amt<100;
```

**Output:**

<img width="781" height="566" alt="image" src="https://github.com/user-attachments/assets/1bd40c58-d9ed-41d3-9cb0-dceb117a0f53" />



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
