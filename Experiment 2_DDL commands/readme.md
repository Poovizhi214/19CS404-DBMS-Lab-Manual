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
-- Create a table named Employees with the following constraints:
EmployeeID should be the primary key.
FirstName and LastName should be NOT NULL.
Email should be unique.
Salary should be greater than 0.
DepartmentID should be a foreign key referencing the Departments table.

```sql
---
create table Employees(
EmployeeID PRIMARY KEY,
FirstName NOT NULL,
LastName NOT NULL,
Email UNIQUE,
Salary check(Salary>0),
DepartmentID int,
Foreign key (DepartmentID) REFERENCES Departments(DepartmentID));
```

**Output:**
![Output1](output.png)![image](https://github.com/user-attachments/assets/69aaf62e-0fe3-4b4d-9ef1-f2d1ceb35e10)


**Question 2**
---
-- Create a table named Products with the following constraints:
ProductID should be the primary key.
ProductName should be NOT NULL.
Price is of real datatype and should be greater than 0.
Stock is of integer datatype and should be greater than or equal to 0.

```sql
--
create table Products(
ProductID int primary key,
ProductName NOT NULL,
Price real check(Price>0),
Stock int check(Stock>=0));
```

**Output:**

![Output2](output.png)![image](https://github.com/user-attachments/assets/de734b58-1d46-44c6-ae8e-47457be86ef4)


**Question 3**
---
-- Create a new table named contacts with the following specifications:
contact_id as INTEGER and primary key.
first_name as TEXT and not NULL.
last_name as TEXT and not NULL.
email as TEXT.
phone as TEXT and not NULL with a check constraint to ensure the length of phone is at least 10 characters.

```sql
-- I
create table contacts(
contact_id INTEGER PRIMARY KEY,
first_name TEXT NOT NULL,
last_name TEXT NOT NULL,
email TEXT,
phone TEXT NOT NULL check(LENGTH(phone)>=10));
```

**Output:**

![Output3](output.png)![image](https://github.com/user-attachments/assets/26d98290-7851-4687-b701-04bc38b1cc89)


**Question 4**
---
-- Insert all students from Archived_students table into the Student_details table.
cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           RollNo      INT           0                       1
1           Name        VARCHAR(100)  0                       0
2           Gender      VARCHAR(10)   0                       0
3           Subject     VARCHAR(50)   0                       0
4           MARKS       INT           0                       0

```sql
--
insert into Student_details(RollNo,Name,Gender,Subject,Marks)
Select RollNo,Name,Gender,Subject,Marks
from Archived_students;
```

**Output:**

![Output4](output.png)![image](https://github.com/user-attachments/assets/6cc9a978-d1b0-4f1d-8e1c-b4725a3afa2b)


**Question 5**
---
-- Insert the below data into the Student_details table, allowing the Subject and MARKS columns to take their default values.
RollNo      Name          Gender      
----------  ------------  ----------  
204         Samuel Black  M          
Note: The Subject and MARKS columns will use their default values.
 
```sql
--
insert into Student_details(RollNo,Name,Gender)
VALUES (204,'Samuel Black','M');
```

**Output:**

![Output5](output.png)![image](https://github.com/user-attachments/assets/e9fc0ad0-507f-45ff-b404-0fc6738200ed)


**Question 6**
---
--Write a SQL query to Rename the "city" column to "location" in the "customer" table.
Sample table: customer
 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002

```sql
--
alter table customer rename column city to location;
```

**Output:**

![Output6](output.png)![image](https://github.com/user-attachments/assets/7eeafe97-fe98-4455-9086-d882183e51d3)

**Question 7**
---
--Insert the following products into the Products table:
Name        Category     Price       Stock
----------  -----------  ----------  ----------
Smartphone  Electronics  800         150
Headphones  Accessories  200         300

```sql
--
insert into Products(Name,Category,Price,Stock)
VALUES('Smartphone','Electronics',800,150),
('Headphones','Accessories',200,300);
```

**Output:**

![Output7](output.png)![image](https://github.com/user-attachments/assets/707daeea-174c-4374-8e87-7bf6367a09bc)


**Question 8**
---
-- Create a table named ProjectAssignments with the following constraints:
AssignmentID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
ProjectID as INTEGER should be a foreign key referencing Projects(ProjectID).
AssignmentDate as DATE should be NOT NULL.

```sql
--
create table ProjectAssignments(
AssignmentID INTEGER PRIMARY KEY,
EmployeeID INTEGER,
ProjectID INTEGER,
AssignmentDate Date NOT NULL,
Foreign key (EmployeeID) REFERENCES Employees(EmployeeID),
Foreign key (ProjectID) REFERENCES Projects(ProjectID));
```

**Output:**

![Output8](output.png)![image](https://github.com/user-attachments/assets/d5b5bbbe-8a57-439c-8e5a-b7fba7167197)


**Question 9**
---
-- Write a SQL Query  to add attribute Date_of_joining as Date and rename the attribute job_title as Designation in the table 'Employees'

```sql
--
Alter table Employees
ADD Date_of_joining Date;
Alter table Employees
Rename column job_title to Designation;
```

**Output:**

![Output9](output.png)![image](https://github.com/user-attachments/assets/d07655d8-8eff-4a39-8a33-b183b023bc94)


**Question 10**
---
-- Create a table named Members with the following columns:
MemberID as INTEGER
MemberName as TEXT
JoinDate as DATE

```sql
--
create table Members(
MemberID INTEGER,
MemberName TEXT,
JoinDate DATE);
```

**Output:**

![Output10](output.png)![image](https://github.com/user-attachments/assets/b1e0e30e-ebc1-4493-adf9-eb52786b61e6)


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
