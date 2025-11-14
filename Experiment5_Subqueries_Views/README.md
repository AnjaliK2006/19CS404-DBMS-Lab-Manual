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
<img width="1154" height="673" alt="image" src="https://github.com/user-attachments/assets/c081fb1b-91f2-4d4c-aa48-6db07c732d3d" />


```sql
select *
from CUSTOMERS
where SALARY IN(
       select SALARY
       FROM CUSTOMERS
       WHERE SALARY<2500
       );
```

**Output:**

<img width="1211" height="521" alt="image" src="https://github.com/user-attachments/assets/4c3b42b9-a75f-4802-8ee9-ef1b2cb93762" />


**Question 2**
---
<img width="1253" height="544" alt="image" src="https://github.com/user-attachments/assets/f680c296-6bfa-4846-ac14-b2351ae4d2d5" />


```sql
select name,city
from customer
where city in(
       select city
       from customer
       where id in (3,7)
       );
```

**Output:**

<img width="603" height="523" alt="image" src="https://github.com/user-attachments/assets/70d354d9-fddb-46b2-ac4b-cb7a063f06d7" />


**Question 3**
---
<img width="1352" height="761" alt="image" src="https://github.com/user-attachments/assets/fdb7d9fc-3fb2-48a3-a287-562a20845438" />


```sql
select *
from orders
where salesman_id in(
      select salesman_id
      from salesman
      where city='London'
      );
```

**Output:**

<img width="1240" height="480" alt="image" src="https://github.com/user-attachments/assets/441c4267-e684-402d-8c45-ca4ebb7c77dc" />


**Question 4**
---
<img width="1352" height="764" alt="image" src="https://github.com/user-attachments/assets/699cf4fe-063f-4ccf-8caa-765e8901aa35" />


```sql
select *
from orders
where salesman_id in(
        select salesman_id
        from salesman
        where name='Paul Adam'
        );
```

**Output:**

<img width="1250" height="462" alt="image" src="https://github.com/user-attachments/assets/f1afa08a-e305-4db1-b3d9-ea96f835c21f" />


**Question 5**
---
<img width="1343" height="729" alt="image" src="https://github.com/user-attachments/assets/170e5770-d9cc-426b-81a6-35ea1f5654bc" />

```sql
select salesman_id,name
from salesman
where salesman_id in(
        select salesman_id
        from customer
        group by salesman_id
        having count(customer_id)>1
        );
```

**Output:**

<img width="674" height="555" alt="image" src="https://github.com/user-attachments/assets/15751606-8128-4dab-85ae-6308d1a0884e" />


**Question 6**
---
<img width="1436" height="631" alt="image" src="https://github.com/user-attachments/assets/f5a4f654-46e0-4fc9-8b46-c44e2ab37af1" />


```sql
select *
from GRADES
where grade=(
      select min(grade)
      from GRADES as g2
      where g2.subject=GRADES.subject
      );
```

**Output:**

<img width="1265" height="520" alt="image" src="https://github.com/user-attachments/assets/debf1ee4-8bc7-4a7f-9076-98f52a2461de" />


**Question 7**
---
<img width="1426" height="652" alt="image" src="https://github.com/user-attachments/assets/0e2b54d6-6b60-4017-8da3-ea67676f3084" />


```sql
select student_name,grade
from GRADES
where grade=(
      select min(grade)
      from GRADES as g2
      where g2.subject=GRADES.subject
      );
```

**Output:**

<img width="762" height="503" alt="image" src="https://github.com/user-attachments/assets/83b2a6b1-723e-4d84-b916-ba80f9009b14" />


**Question 8**
---
<img width="1164" height="775" alt="image" src="https://github.com/user-attachments/assets/1bed3693-cdcd-46db-a755-b2c944509062" />

```sql
select *
from CUSTOMERS
WHERE SALARY IN(
     SELECT SALARY
     FROM CUSTOMERS
     WHERE SALARY>1500
     );
```

**Output:**

<img width="1209" height="690" alt="image" src="https://github.com/user-attachments/assets/06d6c484-923d-459c-bafe-4b971fc6fb99" />


**Question 9**
---
<img width="1381" height="619" alt="image" src="https://github.com/user-attachments/assets/8a8016a5-130d-4f89-a5da-6de327b40a50" />


```sql
SELECT *
FROM ORDERS
WHERE purch_amt>(
       select avg(purch_amt)
       from ORDERS
       where ord_date='2012-10-10'
       );
```

**Output:**

<img width="1265" height="527" alt="image" src="https://github.com/user-attachments/assets/4b8db7fe-ee66-442c-90f3-8b5099b0c297" />

**Question 10**
---
<img width="1213" height="559" alt="image" src="https://github.com/user-attachments/assets/7ba6199e-6fa6-45fe-823b-97494839ba0a" />


```sql
select *
from customer
where city <> (
        select city 
        from customer
        where id=(select max(id) from customer)
        );
```

**Output:**

<img width="1267" height="570" alt="image" src="https://github.com/user-attachments/assets/90140362-9e49-4601-9a75-ade9808f5ce8" />



## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
