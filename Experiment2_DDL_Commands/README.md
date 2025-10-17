# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
--
<img width="948" height="306" alt="image" src="https://github.com/user-attachments/assets/64c73088-c8de-47df-bdcd-a49d8d62c6c4" /><img width="355" height="306" alt="image" src="https://github.com/user-attachments/assets/e14c0541-6949-40fa-ac35-7556e4d90099" />



```
CREATE TABLE Shipments(
ShipmentID INTEGER PRIMARY KEY,
ShipmentDate DATE,
SupplierID INTEGER,
OrderID INTEGER,
FOREIGN KEY(SupplierId) REFERENCES  Suppliers(SupplierID),
FOREIGN KEY(OrderId) REFERENCES  Orders(OrderID) );

```

**Output:**
<img width="994" height="304" alt="image" src="https://github.com/user-attachments/assets/8495809d-de8e-4251-aeb8-5c75b2b94abf" /><img width="740" height="297" alt="image" src="https://github.com/user-attachments/assets/f0c31c02-de2b-4e92-b9da-80915256c266" />



**Question 2**
---
<img width="852" height="383" alt="image" src="https://github.com/user-attachments/assets/2c38aeed-b0ee-4518-83e9-6374e6a0c4f9" />


```
CREATE TABLE Orders(
OrderID INTEGER,
OrderDate TEXT,
CustomerID INTEGER);
```

**Output:**

<img width="528" height="433" alt="image" src="https://github.com/user-attachments/assets/7bdda796-62e2-4303-9bb7-ae709806b03e" /><img width="585" height="445" alt="image" src="https://github.com/user-attachments/assets/cfb2e5c5-c88b-4900-ae1e-ed19f77e6eb7" /><img width="645" height="435" alt="image" src="https://github.com/user-attachments/assets/fbd6f242-4819-48f2-87f2-54ef576f8bae" />




**Question 3**
---
<img width="823" height="330" alt="image" src="https://github.com/user-attachments/assets/694975b7-033f-4925-a48d-664c3b7fa8ae" />
<img width="604" height="150" alt="image" src="https://github.com/user-attachments/assets/5da4eb69-a932-4325-8273-c14b67adf909" />



```
CREATE TABLE Orders(
OrderID INTEGER PRIMARY KEY,
OrderDate DATE NOT NULL,
CustomerID INTEGER,
FOREIGN KEY(CustomerID) REFERENCES Customers(CustomerID));
```

**Output:**

<img width="814" height="350" alt="image" src="https://github.com/user-attachments/assets/25c2f1e3-71b2-4e40-b38a-04923a2cac99" /><img width="734" height="349" alt="image" src="https://github.com/user-attachments/assets/ba96a88b-1f92-40ba-86dd-bd2d058eff96" />



**Question 4**
---
<img width="848" height="464" alt="image" src="https://github.com/user-attachments/assets/37ce07b2-8f06-47bd-9c32-b01b8f093903" />


```
INSERT INTO Customers(CustomerID ,Name,Address)
VALUES(304,'Peter Parker','Spider St');
```

**Output:**

<img width="824" height="409" alt="image" src="https://github.com/user-attachments/assets/39e80476-54b4-4e4c-a800-ac6ddb92f782" />


**Question 5**
---
<img width="827" height="383" alt="image" src="https://github.com/user-attachments/assets/648aa033-dd26-4483-8b50-31b15a44af19" />


```
CREATE TABLE Bonuses(
BonusID INTEGER PRIMARY KEY,
EmployeeID INTEGER,
BonusAmount REAL,
BonusDate DATE,
Reason TEXT NOT NULL,
FOREIGN KEY(EmployeeID) REFERENCES Employees(EmployeeID),
CHECK(BonusAmount>0));
```

**Output:**

<img width="672" height="349" alt="image" src="https://github.com/user-attachments/assets/9dcd78a8-f61d-41d5-b6ea-a4a68f6b30e1" /><img width="719" height="342" alt="image" src="https://github.com/user-attachments/assets/b8b4b5e3-3118-4368-a3a7-ee0efdbd1965" />



**Question 6**
---
<img width="844" height="477" alt="image" src="https://github.com/user-attachments/assets/82e21a14-07bb-4de9-b700-c26b905460a5" />


```
INSERT INTO Books(ISBN,Title,Author,Publisher,Year)
VALUES('978-1234567890',   'Introduction to AI',         'John Doe',NULL,NULL); 
INSERT INTO Books(ISBN,Title,Author,Publisher,Year) 
VALUES('978-9876543210',   'Deep Learning',              'Jane Doe',         'TechPress',   '2022');
INSERT INTO Books(ISBN,Title,Author,Publisher,Year)  
VALUES('978-1122334455',   'Cybersecurity Essentials',   'Alice Smith',NULL,'2021');
```

**Output:**

<img width="779" height="364" alt="image" src="https://github.com/user-attachments/assets/4d16854e-ba57-48cd-806a-b79051fba884" /><img width="819" height="364" alt="image" src="https://github.com/user-attachments/assets/027b80a1-2225-49d1-b0cb-075d3b9bdd80" />



**Question 7**
---
<img width="837" height="259" alt="image" src="https://github.com/user-attachments/assets/0d9d309c-8100-45fc-9f14-9d7551f76874" />


```
ALTER TABLE Student_details
ADD COLUMN Email VARCHAR(50);
ALTER TABLE Student_details 
ADD COLUMN MARKS INTEGER DEFAULT 0;
UPDATE Student_details SET MARKS=0
WHERE MARKS IS NULL;
```

**Output:**

<img width="741" height="302" alt="image" src="https://github.com/user-attachments/assets/277e94fe-aaae-47d0-bf58-1e8368ccd52b" /><img width="831" height="299" alt="image" src="https://github.com/user-attachments/assets/2ace2f9a-2e3a-4b86-9422-0f910e55698f" />



**Question 8**
---
<img width="1196" height="514" alt="image" src="https://github.com/user-attachments/assets/07b57801-9eb4-444c-affa-b2504c9ac642" />



```
ALTER TABLE employee
ADD department_id INTEGER;
ALTER TABLE employee 
ADD manager_id INTEGER DEFAULT NULL;
```

**Output:**

<img width="656" height="388" alt="image" src="https://github.com/user-attachments/assets/f95afa46-157f-43a8-8d76-d944a2129a0c" /><img width="707" height="375" alt="image" src="https://github.com/user-attachments/assets/7d743294-42e3-4908-93fd-b1bced053d10" />



**Question 9**
---
<img width="920" height="477" alt="image" src="https://github.com/user-attachments/assets/faf5e910-ab75-4f0b-aeed-e5bca5873f43" />


```
INSERT INTO student_details(RollNo,Name,Gender,Subject,MARKS)
SELECT RollNo,Name,Gender,Subject,MARKS 
FROM archived_students;
```

**Output:**

<img width="1195" height="378" alt="image" src="https://github.com/user-attachments/assets/e54130dd-648a-40d3-a234-a5840f113d77" />


**Question 10**
---
<img width="770" height="348" alt="image" src="https://github.com/user-attachments/assets/da5aa2f0-7ae4-43de-950c-35174dd27b2f" />


```
CREATE TABLE Products(
ProductID PRIMARY KEY,
ProductName NOT NULL,
Price REAL DATE,
Stock INTEGER,
CHECK(Price>0),
CHECK(Stock>=0));
```

**Output:**

<img width="1193" height="349" alt="image" src="https://github.com/user-attachments/assets/4c38e97b-692a-4b84-b96f-2fb9eeed5950" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
