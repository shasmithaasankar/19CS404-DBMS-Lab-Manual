# Experiment 3: DML Commands

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
**Question 1**
--
-- Write a SQL statement to update the product_name as 'Grapefruit' whose product_id is 4 in the products table.

```sql
UPDATE products
SET product_name='Grapefruit'
WHERE product_id=4;

```

**Output:**

<img width="1232" height="324" alt="image" src="https://github.com/user-attachments/assets/97d1412f-ffe2-4a86-996b-d1434ca70fc1" />


**Question 2**
---
--Write a SQL query to find all orders that meet the following conditions. Exclude combinations of order date equal to '2012-08-17' or customer ID greater than 3005 and purchase amount less than 1000.

```sql
SELECT *
FROM orders
WHERE NOT (
    ord_date = '2012-08-17'
    OR (customer_id > 3005 AND purch_amt < 1000)
);

```

**Output:**

<img width="1244" height="834" alt="image" src="https://github.com/user-attachments/assets/3d15ade2-bf85-47f4-ac2e-0b5f972eb217" />


**Question 3**
---
-- Write a SQL query to Delete customers from 'customer' table where 'GRADE' is exactly 2.

```sql
DELETE FROM customer
WHERE GRADE=2;
```

**Output:**

<img width="975" height="684" alt="image" src="https://github.com/user-attachments/assets/af6be85e-6c26-4ac4-b65b-c9f02b3ae74d" />


**Question 4**
---
-- Write a query to list all products that have a discounted price between $100 and $250. Return product_id, original_price, discount_percentage, and discounted_price from products table.

```sql
SELECT 
    product_id,
    original_price,
    discount_percentage,
    original_price - (original_price * discount_percentage) AS discounted_price
FROM products
WHERE original_price - (original_price * discount_percentage)
      BETWEEN 100 AND 250;


```

**Output:**

<img width="1245" height="405" alt="image" src="https://github.com/user-attachments/assets/8d48162e-35e1-45a4-b83f-d98f1be7e703" />




**Question 5**
---
-- Write a SQL query to Delete customers from 'customer' table where 'CUST_COUNTRY' is neither 'India' nor 'USA'.

```sql
DELETE FROM customer
WHERE CUST_COUNTRY NOT IN('India','USA');

```

**Output:**

<img width="1254" height="658" alt="image" src="https://github.com/user-attachments/assets/48d07b8f-c3e2-4830-b7e0-1993ec4e5ebb" />




**Question 6**
---
-- Write a query to fetch details of employees with the address as “DELHI(DEL)” from EmployeeInfo table.

```sql
SELECT *
FROM EmployeeInfo
WHERE Address='Delhi(DEL)';
```

**Output:**

<img width="1270" height="367" alt="image" src="https://github.com/user-attachments/assets/985a3264-0e73-47fd-b453-414c536f2681" />

**Question 7**
---
-- Write a SQL query to select orders between 500 and 4000 (begin and end values are included). Exclude orders amount 948.50 and 1983.43. Return ord_no, purch_amt, ord_date, customer_id, and salesman_id.

```sql
SELECT ord_no, purch_amt, ord_date, customer_id, salesman_id
FROM orders
WHERE purch_amt BETWEEN 500 AND 4000
  AND purch_amt NOT IN (948.50, 1983.43);

```

**Output:**

<img width="1240" height="495" alt="image" src="https://github.com/user-attachments/assets/4e17cfe0-a232-4909-a42a-17d919f21499" />


**Question 8**
---
--Write a SQL query to identify products where the discount amount is greater than $50. Return product_id, original_price, discount_percentage, and discount_amount.

```sql
SELECT 
    product_id,
    original_price,
    discount_percentage,
    original_price * discount_percentage AS discount_amount
FROM products
WHERE original_price * discount_percentage > 50;

```

**Output:**

<img width="1240" height="359" alt="image" src="https://github.com/user-attachments/assets/3ce2b49d-f035-4d5d-8b23-2e471c12b64c" />


**Question 9**
---
-- Write a SQL query to determine the age group of value1 in the Calculations table as 'Child' if it is less than 13, 'Teen' if it is between 13 and 19, and 'Adult' if it is 20 or older.

```sql
SELECT 
    id,
    value1,
    CASE
        WHEN value1 < 13 THEN 'Child'
        WHEN value1 BETWEEN 13 AND 19 THEN 'Teen'
        ELSE 'Adult'
    END AS age_group
FROM Calculations;

```

**Output:**

<img width="1052" height="460" alt="image" src="https://github.com/user-attachments/assets/d99567bb-ee67-4ac3-b21c-f769752fce51" />


**Question 10**
---
-- Write a SQL query to Delete customers with following conditions

'CUST_COUNTRY' is not in a list of specified countries ('UK', 'USA', 'Canada')
'GRADE' is greater than or equal to 3

```sql
DELETE FROM Customer
WHERE CUST_COUNTRY NOT IN('UK','USA','Canada')
AND GRADE>=3;
```

**Output:**

<img width="1248" height="507" alt="image" src="https://github.com/user-attachments/assets/59eb4c7a-4637-4a2f-980a-b720593dbfff" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
