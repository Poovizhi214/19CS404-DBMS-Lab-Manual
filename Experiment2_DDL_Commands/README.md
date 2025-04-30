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
-- Create a table named Department with the following constraints: 
 DepartmentID as INTEGER should be the primary key. 
 DepartmentName as TEXT should be unique and not NULL. 
 Location as TEXT

```sql
---CREATE TABLE Department(DepartmentID INTEGER PRIMARY KEY,
DepartmentName TEXT UNIQUE NOT NULL, Location TEXT);
```

**Output:**
![Output2](output.png)

**Question 2**
---
-- Write a SQL Query to add attribute Date_of_joining as Date and rename the attribute 
job_title as Designation in the table 'Employees'.

```sql
-- ALTER TABLE Employees ADD COLUMN Date_of_joining Date;
ALTER TABLE Employees RENAME job_title to Designation;
```

**Output:**

![Output2](output.png)

**Question 3**
---
-- Insert the following customers into the Customers table:
CustomerID   Name         Address       City      ZipCode
----------  ----------- ----------    ---------- ----------
302       Laura Croft    456 Elm St    Seattle    98101
303       Bruce Wayne    789 Oak St    Gotham     10001

```sql
-- INSERT INTO Customers (CustomerID,Name,Address,City,ZipCode) VALUES(302, "Laura Croft", "456 Elm St", "Seattle", 98101);
    INSERT INTO Customers VALUES(303, "Bruce Wayne", "789 Oak St", "Gotham", 10001);
```

**Output:**

![Output3](output.png)

**Question 4**
---
-- Create a table named Bonuses with the following constraints:
 BonusID as INTEGER should be the primary key.
 EmployeeID as INTEGER should be a foreign key 
referencing Employees(EmployeeID).
 BonusAmount as REAL should be greater than 0.
 BonusDate as DATE.
 Reason as TEXT should not be NULL.

```sql
-- CREATE TABLE Bonuses(BonusID INTEGER PRIMARY KEY,
EmployeeID INTEGER, BonusAmount REAL CHECK(BonusAmount>0),
BonusDate DATE,
Reason TEXT NOT NULL,
FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID));
```

**Output:**

![Output4](output.png)

**Question 5**
---
-- Insert all employees from Former_employees into Employee
Table attributes are EmployeeID, Name, Department, Salary
 
```sql
-- INSERT INTO Employee
    SELECT * FROM Former_employees
```

**Output:**

![Output5](output.png)

**Question 6**
---
--Create a table named Shipments with the following constraints:
 ShipmentID as INTEGER should be the primary key.
 ShipmentDate as DATE.
 SupplierID as INTEGER should be a foreign key 
referencing Suppliers(SupplierID).
 OrderID as INTEGER should be a foreign key referencing Orders(OrderID).

```sql
-- CREATE TABLE Shipments(ShipmentID INTEGER PRIMARY KEY,
ShipmentDate DATE, SupplierID INTEGER, OrderID INTEGER,
FOREIGN KEY (SupplierID) REFERENCES Suppliers(SupplierID),
FOREIGN KEY (OrderID) REFERENCES Orders(OrderID));
```

**Output:**

![Output6](output.png)

**Question 7**
---
-- Create a table named Invoices with the following constraints:
 InvoiceID as INTEGER should be the primary key.
 InvoiceDate as DATE.
 Amount as REAL should be greater than 0.
 DueDate as DATE should be greater than the InvoiceDate.
 OrderID as INTEGER should be a foreign key referencing Orders(OrderID).

```sql
-- CREATE TABLE Invoices(InvoiceID INTEGER PRIMARY KEY,
InvoiceDate DATE, Amount REAL CHECK(Amount>0),
DueDate DATE CHECK(DueDate>InvoiceDate), OrderID INTEGER,
FOREIGN KEY (OrderID) REFERENCES Orders(OrderID));
```

**Output:**

![Output7](output.png)

**Question 8**
---
-- Write an SQL query to add two new columns, first_name and last_name, to the 
table employee. Both columns should have a data type of varchar(50).

```sql
--ALTER TABLE employee ADD COLUMN first_name varchar(50);
ALTER TABLE employee ADD COLUMN last_name varchar(50);
```

**Output:**

![Output8](output.png)

**Question 9**
---
-- Write a SQL query to Add a new column mobilenumber as number in the Student_details table.
Sample table: Student_details
 cid              name             type   notnull     dflt_value  pk
---------------  ---------------  -----  ----------  ----------  ----------
0                RollNo           int    0                       1
1                Name             VARCH  1                       0
2                Gender           TEXT   1                       0
3                Subject          VARCH  0                       0
4                MARKS            INT (  0                       0

```sql
-- ALTER table Student_details
ADD column mobilenumber number;
```

**Output:**

![Output9](output.png)

**Question 10**
---
-- Insert a student with RollNo 201, Name David Lee, Gender M, Subject Physics, and 
MARKS 92 into the Student_details table.

```sql
--INSERT INTO Student_details(RollNo,Name,Gender,Subject,MARKS)
VALUES(201, "David Lee", "M", "Physics", 92);
```

**Output:**

![Output10](output.png)https://github.com/Poovizhi214/Images-file/blob/df74c34004946b2de13ae79ea4fd12715a80622c/DDL%2010.png


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
