# Experiment 7: PL/SQL – Variables, Control Structures and Loops

## AIM
To write and execute simple PL/SQL programs using variables, loops, and conditional statements.


## THEORY

PL/SQL, which stands for Procedural Language extensions to the Structured Query Language (SQL). It is a combination of SQL along with the procedural features of programming languages.

**Syntax:**
```sql
DECLARE 
   <declarations section> 
BEGIN 
   <executable command(s)>
EXCEPTION 
   <exception handling> 
END;
```

### Basic Components of PL/SQL Block:
- DECLARE: Section to declare variables and constants.
- BEGIN: The execution section that contains PL/SQL statements.
- EXCEPTION: Handles errors or exceptions that occur in the program.
- END: Marks the end of the PL/SQL block.

# PL/SQL Programs – Steps and Expected Output

## 1. Write a PL/SQL program to find the Greatest of Two Numbers

### Steps:
- Declare two numeric variables and initialize them.
- Use an `IF` statement to compare the values.
- Display the greater number using `DBMS_OUTPUT.PUT_LINE`.

PL/SQL query
```
DECLARE
  num1 NUMBER := 70;
  num2 NUMBER := 80;
  greater_number NUMBER;
BEGIN
  IF num1 > num2 THEN
    greater_number := num1;
  ELSE
    greater_number := num2;
  END IF;
  DBMS_OUTPUT.PUT_LINE('The greater number is: ' || greater_number);
END;
/
```
**Expected Output:**  
Greater number is: 80
![image](https://github.com/user-attachments/assets/3cd38138-34ca-4fa7-a4c4-049b5906fb0a)

---

## 2. Write a PL/SQL program to Calculate Sum of First N Natural Numbers

### Steps:
- Declare a variable `n` and assign a value (e.g., 10).
- Initialize a `sum` variable to 0.
- Use a `WHILE` loop to iterate from 1 to `n`, adding each number to the sum.
- Display the result using `DBMS_OUTPUT.PUT_LINE`.
  PL/SQL query
  ```
  DECLARE
  n NUMBER := 10; -- Change this to your desired value
  sum_of_numbers NUMBER;
BEGIN
  sum_of_numbers := n * (n + 1) / 2; -- Using the formula for the sum of the first n natural numbers
  dbms_output.put_line('Sum of first ' || n || ' natural numbers: ' || sum_of_numbers);
END;
/
**Expected Output:**  
Sum of first 10 natural numbers is: 55
![image](https://github.com/user-attachments/assets/ce10d85f-67da-451d-a38e-f4fa1c9c386d)

## 3. Write a PL/SQL program to generate Fibonacci series

### Steps:
- Declare the variable `n` to indicate how many terms to generate.
- Initialize the first two Fibonacci numbers (0 and 1).
- Use a loop to generate the next terms using the formula `c = a + b`.
- Print each term in the series.
PL/SQL query
```
declare

-- declare variable first = 0,
-- second = 1 and temp of datatype number
first number := 0;
second number := 1;
temp number;

n number := 7;
i number;

begin

    dbms_output.put_line('Series:');

--print first two term first and second
    dbms_output.put_line(first);
    dbms_output.put_line(second);

-- loop i = 2 to n
    for i in 2..n
    loop
        temp:=first+second;

first := second;
second := temp;

--print terms of fibonacci series
    dbms_output.put_line(temp);
end loop;

end;
/
```
**Expected Output:**  
n = 7  
Fibonacci sequence: 0, 1, 1, 2, 3, 5, 8
![image](https://github.com/user-attachments/assets/477c7cd2-2b84-4964-a9b8-01dc5e21d7c3)

---

## 4. Write a PL/SQL Program to display the number in Reverse Order

### Steps:
- Declare a variable `n` and assign a value (e.g., 1535).
- Use a loop to extract each digit using modulo and reverse the number.
- Display the reversed number.

PL/SQL query
```
declare
no number;
rev number:=0;
remainder number;
begin
no:=&no;
while (no>0)
loop
  remainder := mod(no,10);
  rev := rev * 10 + remainder;
  no := floor(no/10);
end loop;
dbms_output.put_line('reverse of number is '||rev);
end;
/
```
**Expected Output:**  
n = 1535  
Reversed number is 5351
![image](https://github.com/user-attachments/assets/7113ef9e-1384-44a6-876e-23d9b7db3bdb)

---

## 5. Write a PL/SQL program to find the largest of three numbers

### Steps:
- Declare three numeric variables `a`, `b`, and `c`.
- Use nested `IF-ELSIF-ELSE` conditions to find the largest among the three.
- Display the largest number.
PL/SQL query
```
DECLARE
   a INTEGER := 10;
   b INTEGER := 9;
   c INTEGER := 15;
BEGIN
   IF a >= b AND a >= c THEN
      DBMS_OUTPUT.PUT_LINE('Largest of three number is ' || a);
   ELSIF b >= a AND b >= c THEN
      DBMS_OUTPUT.PUT_LINE('Largest of three number is ' || b);
   ELSE
      DBMS_OUTPUT.PUT_LINE('Largest of three number is ' || c);
   END IF;
END;
/
```
**Expected Output:**  
a = 10, b = 9, c = 15  
Largest of three number is 15
![image](https://github.com/user-attachments/assets/a397f261-1079-42ea-ad20-d956eaa220b9)


## RESULT
Thus, the PL/SQL programs using variables, conditionals, and loops were executed successfully.
