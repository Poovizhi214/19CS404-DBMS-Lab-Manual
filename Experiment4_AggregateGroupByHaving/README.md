# Experiment 4: Aggregate Functions, Group By and Having Clause

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
-- What is the most common diagnosis among patients?
Sample table:MedicalRecords Table

```sql
-- select Diagnosis,count(*) as DiagnosisCount from MedicalRecords group by Diagnosis order by DiagnosisCount desc limit 1;
```

**Output:**

![Output1](output.png)![image](https://github.com/user-attachments/assets/ba81ebce-4737-474c-bd85-57989eb097e9)


**Question 2**
---
-- How many prescriptions were written for each medication?
Sample tablePrescriptions Table

```sql
--
select Medication,count(*) as TotalPrescriptions from Prescriptions group by Medication;
```

**Output:**

![Output2](output.png)![image](https://github.com/user-attachments/assets/e29b4222-16d5-4b46-afce-9ddf4b97eb39)


**Question 3**
---
-- Write a SQL query to calculate total purchase amount of all orders. Return total purchase amount.
Sample table: orders
ord_no      purch_amt   ord_date    customer_id  salesman_id
----------  ----------  ----------  -----------  -----------
70001       150.5       2012-10-05  3005         5002

70009       270.65      2012-09-10  3001         5005

70002       65.26       2012-10-05  3002         5001

```sql
--
select sum(purch_amt) as TOTAL from orders;
```

**Output:**

![Output3](output.png)![image](https://github.com/user-attachments/assets/07a29714-a818-446d-acf3-1e2be7d3fcd8)


**Question 4**
---
-- Write a SQL query to find the average length of email addresses (in characters):
Table: customer
name        type
----------  ----------
id          INTEGER
name        TEXT
city        TEXT
email       TEXT
phone       INTEGER

```sql
--
select avg(length(email)) as avg_email_length from customer;
```

**Output:**

![Output4](output.png)![image](https://github.com/user-attachments/assets/8c62979f-98f2-43b0-8552-7b9770e270bc)


**Question 5**
---
-- Write a SQL query to find the minimum purchase amount.
Sample table: orders
ord_no      purch_amt   ord_date    customer_id  salesman_id
----------  ----------  ----------  -----------  -----------
70001       150.5       2012-10-05  3005         5002

70009       270.65      2012-09-10  3001         5005

70002       65.26       2012-10-05  3002         5001

```sql
--
select min(purch_amt) as MINIMUM from orders;
```

**Output:**

![Output5](output.png)![image](https://github.com/user-attachments/assets/38b0e561-6c79-4314-a53a-b231141bf351)


**Question 6**
---
-- Write a SQL query to Calculate the average email length (in characters) for people who lives in Mumbai city
Table: customer
name        type
----------  ----------
id          INTEGER
name        TEXT   
city        TEXT
email       TEXT
phone       INTEGER

```sql
--
select avg(length(email)) as avg_email_length_below_30 from customer where city='Mumbai'
```

**Output:**

![Output6](output.png)![image](https://github.com/user-attachments/assets/a6019264-db19-4520-a7bf-2503b8cb70af)


**Question 7**
---
-- Write the SQL query that achieves the grouping of data by city, calculates the average income for each city, and includes only those cities where the average income is greater than 500,000.
Sample table: employee

```sql
--
select city,avg(income) as 'AVG(income)' from employee group by city having avg(income)>500000;
```

**Output:**

![Output7](output.png)

**Question 8**
---
-- Write the SQL query that achieves the selection of product names and the maximum price for each category from the "products" table, and includes only those products where the maximum price is greater than 15.
Sample table: products

```sql
--
select category_id,product_name,max(price) as Price from products group by category_id having max(price)>15
```

**Output:**

![Output8](output.png)![image](https://github.com/user-attachments/assets/652ab4ca-07fe-48fc-930c-7b57052896d4)


**Question 9**
---
-- How many patients are covered by each insurance company?
Sample table:Insurance Table
name               type
-----------------  ----------
InsuranceID        INTEGER
PatientID          INTEGER
InsuranceCompany   TEXT
PolicyNumber       TEXT
PolicyHolder       TEXT
ValidityPeriod     TEXT

```sql
--
select InsuranceCompany,count(*) as TotalPatients
from Insurance
group by InsuranceCompany;
```

**Output:**

![Output9](output.png)![image](https://github.com/user-attachments/assets/b34272be-5f9d-4081-8b52-e95c242214a4)


**Question 10**
---
-- What is the total number of appointments scheduled by each doctor?
Sample table:Appointments Table

```sql
--
select DoctorID,count(*) as TotalAppointments
from Appointments
group by DoctorID;
```

**Output:**

![Output10](output.png)![Uploading image.png…]()



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
