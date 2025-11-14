g# Experiment 4: Aggregate Functions, Group By and Having Clause

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
<img width="1249" height="480" alt="image" src="https://github.com/user-attachments/assets/d5a2e2fe-a9a1-448c-95ae-03a96563e386" />


```sql
select Gender, count(*) as TotalPatients
from Patients
group by Gender;
```

**Output:**

<img width="686" height="441" alt="image" src="https://github.com/user-attachments/assets/6bd37989-587b-4bf1-be52-5e8d5c7c91ce" />


**Question 2**
---
<img width="1202" height="544" alt="image" src="https://github.com/user-attachments/assets/8e7a6748-d3fe-4c79-97c2-773cf47ea93e" />


```sql
select DoctorID, count(*) as TotalRecords
from MedicalRecords
group by DoctorID;
```

**Output:**

<img width="712" height="711" alt="image" src="https://github.com/user-attachments/assets/baf8a445-2cbd-4255-85fa-e9da57dde541" />


**Question 3**
---
<img width="1171" height="659" alt="image" src="https://github.com/user-attachments/assets/1a395a9a-3d24-437a-b56a-b30db325dab9" />


```sql
select Medication, count(*) as TotalPrescriptions
from Prescriptions
group by Medication;
```

**Output:**

<img width="768" height="823" alt="image" src="https://github.com/user-attachments/assets/604d2590-a81b-4251-9335-a983d752e3bd" />


**Question 4**
---
<img width="1198" height="468" alt="image" src="https://github.com/user-attachments/assets/94bafd07-67bd-47f3-af37-893675fcd26e" />


```sql
select max(age) - min(age) as age_difference
from employee;
```

**Output:**

<img width="537" height="394" alt="image" src="https://github.com/user-attachments/assets/605271ae-9813-4e6d-91ad-afecc3e135a8" />


**Question 5**
---
<img width="981" height="482" alt="image" src="https://github.com/user-attachments/assets/0c76a8ff-6420-437b-9b1e-c0bdfb42f242" />

```sql
select count(*) as 'COUNT'
from employee
where age>32;
```

**Output:**

<img width="619" height="391" alt="image" src="https://github.com/user-attachments/assets/5dab0778-7e6c-4dcc-a65d-7c6e73966df8" />


**Question 6**
---
<img width="1109" height="524" alt="image" src="https://github.com/user-attachments/assets/9774866f-20e6-4576-a50e-0ef1820c5e50" />


```sql
select avg(purch_amt) as AVERAGE
from orders;

```

**Output:**

<img width="440" height="388" alt="image" src="https://github.com/user-attachments/assets/5d8ca148-0ece-45a7-b8de-827d3f2631de" />


**Question 7**
---
<img width="971" height="490" alt="image" src="https://github.com/user-attachments/assets/c8c2a1d4-4d6d-49e6-9826-d558149bc656" />


```sql
select avg(length(email)) as avg_email_length
from customer;
```

**Output:**

<img width="525" height="396" alt="image" src="https://github.com/user-attachments/assets/bbfd6950-1f65-4422-9f8f-a9b3f664d867" />


**Question 8**
---
<img width="1374" height="589" alt="image" src="https://github.com/user-attachments/assets/5a7fd5b8-6fa1-48a3-b69d-bf1fccf1a582" />


```sql
select (age/5)*5 as age_group,
max(salary) as 'MAX(salary)'
from customer1
group by age_group
having max(salary)>8000;
```

**Output:**

<img width="613" height="455" alt="image" src="https://github.com/user-attachments/assets/e8789969-518b-4e55-9cb8-dcd6198a603f" />


**Question 9**
---
<img width="1384" height="546" alt="image" src="https://github.com/user-attachments/assets/ca94731a-15a2-4636-bca6-e4a7b8a4f98a" />

```sql
select category_id, sum(price*category_id) as Revenue
from products
group by category_id
having sum(price*category_id)>25;
```

**Output:**

<img width="649" height="518" alt="image" src="https://github.com/user-attachments/assets/aebdb1cf-48dd-41c9-a8fe-3d44b82e2faf" />


**Question 10**
---
<img width="1382" height="519" alt="image" src="https://github.com/user-attachments/assets/c4e930cd-2679-4eb8-aaaf-8838749a63fb" />

```sql
select age, sum(income) as 'SUM(income)'
from employee
group by age
having sum(income) >1000000;
```

**Output:**

<img width="618" height="483" alt="image" src="https://github.com/user-attachments/assets/e7fec9d1-0e8f-4e57-aa30-d0f30118cc22" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
