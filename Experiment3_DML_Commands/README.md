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
<img width="1412" height="750" alt="image" src="https://github.com/user-attachments/assets/df757325-2fac-4458-8066-cba2eb92bf0e" />


```sql
update Employees
set salary = salary+500,
email='updated'
where job_id='SA_REP'
AND commission_pct>0.15;
```

**Output:**

<img width="1216" height="604" alt="image" src="https://github.com/user-attachments/assets/2c8d42d1-d58d-427e-b5fe-721bde3d1699" />


**Question 2**
---<img width="1428" height="572" alt="image" src="https://github.com/user-attachments/assets/d5c23b24-48d0-4485-b40a-e040cf253ee2" />


```sql
update Products
set category='Household'
where product_name like '%Detergent%';
```

**Output:**

<img width="988" height="565" alt="image" src="https://github.com/user-attachments/assets/a99c7ebf-3481-493b-80a5-eadd01aed097" /><img width="1002" height="577" alt="image" src="https://github.com/user-attachments/assets/0d5586f4-3d9e-429c-b242-670c4c4e8cac" />



**Question 3**
---
<img width="1424" height="520" alt="image" src="https://github.com/user-attachments/assets/9ae9316b-7196-4e0e-aa53-4f63b0afd367" />


```sql
update SALES 
set total_sell_price=quantity*sell_price
where product_id=10;
```

**Output:**

<img width="1220" height="575" alt="image" src="https://github.com/user-attachments/assets/aeffeefe-dc50-46b2-ac27-dc64ee19a1a7" />


**Question 4**
---
<img width="1187" height="514" alt="image" src="https://github.com/user-attachments/assets/079c76ef-2b68-4aad-881a-fa63486cc5d8" />


```sql
update Suppliers
set address='58 Lakeview, Magnolia'
where supplier_id=5;
```

**Output:**

<img width="1072" height="470" alt="image" src="https://github.com/user-attachments/assets/ed0b6dda-f15e-4e78-90aa-4ff34d0d14cd" /><img width="1113" height="476" alt="image" src="https://github.com/user-attachments/assets/eb8d339f-0d7b-4851-88c5-88263cf4bc60" />



**Question 5**
---
<img width="1039" height="483" alt="image" src="https://github.com/user-attachments/assets/1f4eaaa3-da00-4465-8c6c-b4f97c6c6be3" />


```sql
update suppliers 
set supplier_name=UPPER(supplier_name)
where contact_person like '%Singh%';
```

**Output:**

<img width="1043" height="432" alt="image" src="https://github.com/user-attachments/assets/548b0523-acc1-48a3-b398-867d599de929" /><img width="1085" height="425" alt="image" src="https://github.com/user-attachments/assets/735c9e77-9271-4c45-9b35-1a8ed445922e" />



**Question 6**
---
<img width="977" height="570" alt="image" src="https://github.com/user-attachments/assets/250247f5-60da-49c8-9566-803838742486" />


```sql
delete from Doctors
where last_name is NULL;
```

**Output:**

<img width="1218" height="789" alt="image" src="https://github.com/user-attachments/assets/a46ff6a7-68e6-4153-8611-7bd81b35a60a" />


**Question 7**
---
<img width="1426" height="590" alt="image" src="https://github.com/user-attachments/assets/805df5d8-2083-4771-9247-d185aa8cc694" />


```sql
delete FROM Customer
where CUST_COUNTRY NOT IN('UK', 'USA', 'Canada')
AND GRADE>=3;
```

**Output:**

<img width="1188" height="517" alt="image" src="https://github.com/user-attachments/assets/85a373bb-9e02-426e-93bc-9dbd727e1cf1" /><img width="1177" height="508" alt="image" src="https://github.com/user-attachments/assets/a7d854d2-de26-4e03-86da-591fe5399444" />


**Question 8**
---
<img width="1416" height="522" alt="image" src="https://github.com/user-attachments/assets/5679fdcc-d450-41c0-ae75-91c81a0efaf3" />


```sql
delete from Customer
where GRADE=3
and CUST_NAME like '%BBB%'
and PAYMENT_AMT>2000;
```

**Output:**

<img width="1210" height="581" alt="image" src="https://github.com/user-attachments/assets/5ad67f05-1c95-45b7-b7cd-47195135a310" /><img width="1144" height="570" alt="image" src="https://github.com/user-attachments/assets/d0275738-e41f-433d-8e6b-eb295194a863" />


**Question 9**
---
<img width="1401" height="543" alt="image" src="https://github.com/user-attachments/assets/d2a7159d-e364-4d9a-9546-26cc028a5f01" />


```sql
delete from Customer
where CUST_CITY is not 'New York'
and OUTSTANDING_AMT>5000;
```

**Output:**

<img width="1207" height="675" alt="image" src="https://github.com/user-attachments/assets/ea615912-a1c7-42b3-9047-fc939978eee2" /><img width="1173" height="672" alt="image" src="https://github.com/user-attachments/assets/39a4c43d-f254-44a1-9408-51e7d4bb61af" />


**Question 10**
---
<img width="1418" height="513" alt="image" src="https://github.com/user-attachments/assets/bf440103-761f-4c20-b389-10a0c48cd62a" />


```sql
delete from Customer
where (GRADE=3 or AGENT_CODE='A008')
and OUTSTANDING_AMT<5000;
```

**Output:**

<img width="1217" height="478" alt="image" src="https://github.com/user-attachments/assets/447dce43-2941-45ab-bde6-c32881a8d3aa" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
