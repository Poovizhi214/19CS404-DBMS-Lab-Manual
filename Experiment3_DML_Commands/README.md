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
-- Write a SQL query to reduce the reorder level by 30% where cost price is more than 50 and quantity in stock is less than 100 in the products table.
Products Table 
name          type       
----------    ---------- 
product_id     INT PRIMARY KEY        
product_name   VARCHAR(10) 
category       VARCHAR(50) 
cost_price     DECIMAL(10) 
sell_price     DECIMAL(10) 
reorder_lvl    INT        
quantity       INT        
supplier_id    INT              

```sql
--
update Products set reorder_lvl=reorder_lvl-(0.3*reorder_lvl)
where cost_price>50 and quantity<100;
```

**Output:**<img width="563" alt="DML 1" src="https://github.com/user-attachments/assets/c15dd22e-e295-489c-81a1-f7dbd34f735b" />


![Output1](output.png)

**Question 2**
---
-- Write a SQL statement to update the product_name as 'Grapefruit' whose product_id is 4 in the products table.
products table
---------------
product_id
product_name
category_id
availability

```sql
--
update Products set product_name="Grapefruit"
where product_id=4;
```

**Output:**

![Output2](output.png)<img width="557" alt="image" src="https://github.com/user-attachments/assets/e64e20c7-2c1b-4144-b0e4-130a583b65f3" />


**Question 3**
---
-- Update the reorder level to 40 pieces for all products belonging to the 'Grocery' category in the products table.
PRODUCTS TABLE
name               type
-----------------  ---------------
product_id         INT
product_name       VARCHAR(100)
category           VARCHAR(50)
cost_price         DECIMAL(10,2)
sell_price         DECIMAL(10,2)
reorder_lvl        INT
quantity           INT
supplier_id        INT

```sql
--
update Products set reorder_lvl=40
where category='Grocery';
```

**Output:**

![Output3](output.png)<img width="568" alt="image" src="https://github.com/user-attachments/assets/4a5a207d-c514-4da1-b93a-b69cbed55d56" />


**Question 4**
---
-- Write a SQL query to delete a doctor from Doctors table whose Specialization is 'Pediatrics' and First name is 'Michael'.
Sample table: Doctors
attributes : doctor_id, first_name, last_name, specialization

```sql
--
Delete from Doctors
where Specialization = "Pediatrics"
and first_name like "Michael";
```

**Output:**

![Output4](output.png)![image](https://github.com/user-attachments/assets/9861bb38-550f-4847-b9de-c100c860139f)


**Question 5**
---
-- Write a SQL query to Delete customers from 'customer' table where 'GRADE' is odd.
Sample table: Customer

```sql
--
Delete from customer
where (grade%2!=0);
```

**Output:**

![Output5](output.png)![image](https://github.com/user-attachments/assets/cf49c0a6-7348-41c3-a110-7e49e337c300)


**Question 6**
---
-- Write a query to find all the employees whose salary is between 50000 to 100000 from employeeposition table.

EmpID    EmpPosition   DateOfJoining   Salary
1      Manager        01/05/2024      500000
2      Executive      02/05/2024      75000

```sql
--
select * from Employeeposition
where salary between 50000 and 100000;
```

**Output:**

![Output6](output.png)![image](https://github.com/user-attachments/assets/a9eeb394-70d5-433a-b4a4-e9f9f6df1215)


**Question 7**
---
--Write a SQL statement to Find all those customers with all information whose names are ending with the letter 'n'.
customer table
cid           name             type      notnu  dflt_value    pk
------------  ---------------  --------  -----  ------------  ----------
0             customer_id      int       0                    0
1             cust_name        text      0                    0
2             city             text      0                    0
3             grade            int       0                    0
4             salesman_id      int       0                    0

```sql
--
select * from customer
where cust_name like "%n";
```

**Output:**

![Output7](output.png)![image](https://github.com/user-attachments/assets/8fef9099-15b0-4377-a2d2-eb297ff567f1)


**Question 8**
---
-- Write a SQL query to classify base in the Calculations table as 'Provided' if it is not NULL, otherwise 'Not Provided'.
cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           id          INTEGER     0                       1
1           value1      REAL        0                       0
2           value2      REAL        0                       0
3           base        INTEGER     0                       0
4           exponent    INTEGER     0                       0
5           number      REAL        0                       0
6           decimal     REAL        0                       0

```sql
--
select id,base,
CASE
when base is not null then 'Provided'
else 'Not Provided'
end as base_status
from Calculations;

```

**Output:**

![Output8](output.png)![image](https://github.com/user-attachments/assets/a89b2976-7b60-478b-97a7-3d6400e6138c)


**Question 9**
---
-- Write a SQL query to calculate the final price after applying both the discount and the tax. Return product_id, original_price, discount_percentage, tax_rate, and final_price.
Sample table: Products
product_id | original_price | discount_percentage | tax_rate
 ------------+----------------+---------------------+--------- 
101 | 50.00 | 0.10 | 0.08 

102 | 75.00 | 0.15 | 0.05 

103 | 100.00 | 0.20 | 0.10

```sql
--
select product_id,
original_price,
discount_percentage,
tax_rate,
original_price*(1-discount_percentage)*(1+tax_rate) as final_price
from Products;
```

**Output:**

![Output9](output.png)![image](https://github.com/user-attachments/assets/e907d74a-0a4c-4e2e-a068-cfc717ed80e7)


**Question 10**
---
-- Write a SQL query to Select all patients who was admitted in hospital for more than 3 days.
Table: Patients
name                  type
--------------------  ----------
patient_id            INT
first_name            VARCHAR(50)
last_name             VARCHAR(50)
date_of_birth         DATE
admission_date        DATE
discharge_date        DATE
doctor_id             INT

```sql
--
select first_name,
last_name,
JULIANDAY(discharge_date)-JULIANDAY(admission_date)+1 as no_of_days
from Patients
where JULIANDAY(discharge_date)-JULIANDAY(admission_date) > 3;
```

**Output:**

![Output10](output.png)![image](https://github.com/user-attachments/assets/c1f7f440-650e-4d31-9177-13471ed1fdd7)


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
