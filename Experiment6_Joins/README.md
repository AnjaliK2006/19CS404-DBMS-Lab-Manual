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
<img width="1224" height="794" alt="image" src="https://github.com/user-attachments/assets/f611862b-eb0b-42ab-8930-b8e9e77a6e07" />


```sql
SELECT 
    c.cust_name AS "Customer Name",
    c.city AS "city",
    s.name AS "Salesman",
    s.commission AS "commission"
FROM 
    customer c
JOIN 
    salesman s
ON 
    c.salesman_id = s.salesman_id;

```

**Output:**

<img width="1093" height="803" alt="image" src="https://github.com/user-attachments/assets/f4726c72-1fab-418c-9f58-ec77297154e1" />


**Question 2**
---
<img width="1447" height="742" alt="image" src="https://github.com/user-attachments/assets/bd391ffa-83dd-4f3e-9484-e8e6988edbbd" />


```sql
SELECT 
    p.date_of_birth,
    a.*
FROM 
    patients p
INNER JOIN 
    appointments a
ON 
    p.patient_id = a.patient_id
WHERE 
    p.first_name = 'Alice';

```

**Output:**

<img width="1266" height="503" alt="image" src="https://github.com/user-attachments/assets/1323649c-160f-487b-bc15-7b695ea0a711" />

**Question 3**
---
<img width="1422" height="823" alt="image" src="https://github.com/user-attachments/assets/edd0a4e4-ddf9-407d-84c7-8c0ae7c8b717" />


```sql
SELECT 
    c.cust_name AS "Customer Name",
    c.city AS "city",
    s.name AS "Salesman",
    s.city AS "city",
    s.commission AS "commission"
FROM 
    customer c
JOIN 
    salesman s
ON 
    c.salesman_id = s.salesman_id
WHERE 
    c.city <> s.city
    AND s.commission > 0.12;

```

**Output:**

<img width="1296" height="653" alt="image" src="https://github.com/user-attachments/assets/4f223ca0-c78c-4771-8325-d8d78b09eb31" />


**Question 4**
---
<img width="1469" height="852" alt="image" src="https://github.com/user-attachments/assets/c378a1ae-eaee-4e21-a2dc-c55494175178" />


```sql
SELECT 
    c.cust_name AS "Customer Name",
    c.city AS "city",
    s.name AS "Salesman",
    s.commission AS "commission"
FROM 
    customer c
JOIN 
    salesman s
ON 
    c.salesman_id = s.salesman_id
WHERE 
    s.commission > 0.12;

```

**Output:**

<img width="1218" height="763" alt="image" src="https://github.com/user-attachments/assets/a4b33918-153e-4f19-8e9f-a02653db7aa8" />


**Question 5**
---
<img width="1288" height="801" alt="image" src="https://github.com/user-attachments/assets/aedefaf3-2f20-4ba6-84b2-9ec998a33029" />


```sql
SELECT 
    o.ord_no,
    o.ord_date,
    o.purch_amt,
    c.cust_name AS "Customer Name",
    c.grade,
    s.name AS "Salesman",
    s.commission
FROM 
    orders o
JOIN 
    customer c
ON 
    o.customer_id = c.customer_id
JOIN 
    salesman s
ON 
    o.salesman_id = s.salesman_id;

```

**Output:**

<img width="1360" height="858" alt="image" src="https://github.com/user-attachments/assets/6899fe3c-cd53-4cb7-882b-fd6c77b33fd5" />


**Question 6**
---
<img width="1400" height="586" alt="image" src="https://github.com/user-attachments/assets/32a26a68-0606-4b60-b84e-c8fa654c04e7" />


```sql
SELECT 
    s.name AS salesman_name,
    c.cust_name AS customer_name
FROM 
    salesman s
LEFT JOIN 
    customer c
ON 
    s.salesman_id = c.salesman_id;

```

**Output:**

<img width="684" height="798" alt="image" src="https://github.com/user-attachments/assets/0fee4699-d622-4f34-9341-322300dc9f07" />


**Question 7**
---
<img width="1424" height="740" alt="image" src="https://github.com/user-attachments/assets/10bdb3b7-03a0-4d0c-a6b0-447a276f792e" />

```sql
SELECT p.*
FROM patients p
INNER JOIN test_results tr ON p.patient_id = tr.patient_id
WHERE (tr.test_name = 'Blood Test' OR tr.test_name = 'Blood Pressure')
  AND tr.result NOT LIKE '%Normal%';
```

**Output:**

<img width="1712" height="385" alt="image" src="https://github.com/user-attachments/assets/fa8d4b0f-9110-4d75-900e-1380b8b4da63" />


**Question 8**
---
<img width="1268" height="811" alt="image" src="https://github.com/user-attachments/assets/a1fcab51-623d-4c23-9f08-78c0891c1a5f" />


```sql
SELECT
    o.ord_no,
    o.purch_amt,
    o.ord_date,
    c.cust_name,
    c.city AS customer_city,
    c.grade,
    s.name AS salesman_name,
    s.city AS salesman_city,
    s.commission
FROM
    orders o
INNER JOIN
    customer c
ON
    o.customer_id = c.customer_id
INNER JOIN
    salesman s
ON
    o.salesman_id = s.salesman_id;

```

**Output:**

<img width="1688" height="829" alt="image" src="https://github.com/user-attachments/assets/de3173bc-39bc-4a87-bcb7-d59489f10bf4" />


**Question 9**
---
<img width="1437" height="535" alt="image" src="https://github.com/user-attachments/assets/c28105ce-f497-4812-97bf-f1b36f5ce801" />


```sql
SELECT c.*
FROM customer c
LEFT JOIN orders o ON c.customer_id = o.customer_id
WHERE o.ord_date > '2012-08-17';

```

**Output:**

<img width="1284" height="721" alt="image" src="https://github.com/user-attachments/assets/6b0b235f-6e43-42cb-9126-223a7164eff3" />


**Question 10**
---
<img width="1436" height="748" alt="image" src="https://github.com/user-attachments/assets/fa1372d4-44a5-45cf-bb47-a366600ef83d" />

```sql
SELECT
    p.first_name AS patient_name,
    d.specialization AS Doctor_speciali
FROM
    patients p
INNER JOIN
    doctors d
ON
    p.doctor_id = d.doctor_id
WHERE
    p.admission_date BETWEEN '2024-01-01' AND '2024-01-31';

```

**Output:**

<img width="677" height="448" alt="image" src="https://github.com/user-attachments/assets/f0f5d1f2-f0e8-4e4f-8d74-f5ca5beb84c5" />


## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
