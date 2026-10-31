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
-- Create a table named Invoices with the following constraints:
InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
Amount as REAL should be greater than 0.
DueDate as DATE should be greater than the InvoiceDate.
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).


```sql
-- create table Invoices
(
    InvoiceID int PRIMARY KEY,
    InvoiceDate DATE,
    Amount REAL CHECK(Amount > 0),
    DueDate DATE CHECK(DueDate > InvoiceDate),
    OrderID INT,
    Foreign key (OrderID) REFERENCES Orders(OrderID)
);
```

**Output:**
<img width="1225" height="98" alt="image" src="https://github.com/user-attachments/assets/9f2777b6-a98c-490a-9294-4d120b0abb73" />




**Question 2**
---
-- Create a table named Reviews with the following columns:

ReviewID as INTEGER
ProductID as INTEGER
Rating as REAL
ReviewText as TEXT



```sql
--  create table Reviews
(
    ReviewID INTEGER,
    ProductID INTEGER,
    Rating REAL,
    ReviewText TEXT
);
```

**Output:**

<img width="1048" height="161" alt="image" src="https://github.com/user-attachments/assets/2e0b1ad5-3327-48d0-a5bd-594c7974f86e" />


**Question 3**
---
-- Create a table named Products with the following constraints:
ProductID as INTEGER should be the primary key.
ProductName as TEXT should be unique and not NULL.
Price as REAL should be greater than 0.
StockQuantity as INTEGER should be non-negative.


```sql
-- CREATE TABLE Products
(
    ProductID INTEGER PRIMARY KEY,
    ProductName TEXT UNIQUE NOT NULL,
    Price REAL CHECK(PRICE>0),
    StockQuantity INTEGER CHECK(StockQuantity>0)
);
```

**Output:**

<img width="1216" height="102" alt="image" src="https://github.com/user-attachments/assets/46e192d0-8c19-4f86-a980-8671dd415555" />


**Question 4**
---
-- Insert a book with ISBN 978-1234567890, Title Data Science Essentials, Author Jane Doe, Publisher TechBooks, and Year 2024 into the Books table.

```sql
-- insert into Books
Values('978-1234567890','Data Science Essentials','Jane Doe','TechBooks',2024);
```

**Output:**

<img width="1418" height="115" alt="image" src="https://github.com/user-attachments/assets/ae91c271-6fa3-4e6e-95a2-255027f56fe9" />


**Question 5**
---
-- Write an SQL query to change the name of the column id to employee_id in the table employee.

```sql
-- alter table employee
rename column id to employee_id;
```

**Output:**

<img width="1433" height="139" alt="image" src="https://github.com/user-attachments/assets/23a78db8-df4a-4aeb-ac4c-b5b9d9f901d3" />


**Question 6**
---
-- Insert the following employees into the Employee table:

EmployeeID  Name        Position    Department  Salary
----------  ----------  ----------  ----------  ----------
2           John Smith  Developer   IT          75000
3           Anna Bell   Designer    Marketing   68000

```sql
--insert into Employee
Values(2,'John Smith','Developer','IT',75000),(3,'Anna Bell','Designer','Marketing',68000);
```

**Output:**

<img width="1528" height="213" alt="image" src="https://github.com/user-attachments/assets/7310f69a-2f14-4f5b-9f91-c1f8563ab5db" />


**Question 7**
---
-- Insert all products from Discontinued_products into Products.
Table attributes are ProductID, ProductName, Price, Stock

```sql
-- Insert into ProductS
select * from Discontinued_products;
```

**Output:**

<img width="1059" height="155" alt="image" src="https://github.com/user-attachments/assets/a08c2bba-5076-459a-aee6-4721f3a21aa2" />


**Question 8**
---
-- Create a new table named contacts with the following specifications:
contact_id as INTEGER and primary key.
first_name as TEXT and not NULL.
last_name as TEXT and not NULL.
email as TEXT.
phone as TEXT and not NULL with a check constraint to ensure the length of phone is at least 10 characters.

```sql
--create table contacts
(
    contact_id INTEGER PRIMARY KEY,
    first_name TEXT NOT NULL,
    last_name TEXT NOT NULL,
    email TEXT,
    phone TEXT NOT NULL CHECK(LENGTH(phone)==10)
);
```

**Output:**

<img width="1641" height="148" alt="image" src="https://github.com/user-attachments/assets/47111451-27e2-4db0-a5d0-cd5f514f70c8" />


**Question 9**
---
-- Write a SQL query to Add a new column Mobilenumber as number in the Student_details table.

Sample table: Student_details

 cid              name             type             notnu  dflt_value  pk
---------------  ---------------  ---------------  -----  ----------  ----------
0                RollNo           int              0                  1
1                Name             VARCHAR(100)     1                  0
2                Gender           TEXT             1                  0
3                Subject          VARCHAR(30)      0                  0
4                MARKS            INT (3)          0                  0

```sql
-- ALTER TABLE Student_details
ADD COLUMN Mobilenumber number;
```

**Output:**

<img width="1107" height="168" alt="image" src="https://github.com/user-attachments/assets/953d898c-147c-4de1-89de-8d539672635c" />


**Question 10**
---
-- Create a new table named item with the following specifications and constraints:
item_id as TEXT and as primary key.
item_desc as TEXT.
rate as INTEGER.
icom_id as TEXT with a length of 4.
icom_id is a foreign key referencing com_id in the company table.
The foreign key should set NULL on updates and deletes.
item_desc and rate should not accept NULL.

```sql
-- create table item
(
    item_id TEXT PRIMARY KEY,
    item_desc TEXT NOT NULL,
    rate INTEGER NOT NULL,
    icom_id INTEGER,
    foreign key (icom_id) references company(com_id) ON UPDATE SET NULL ON DELETE SET NULL
    
)
```

**Output:**

<img width="987" height="170" alt="image" src="https://github.com/user-attachments/assets/f20e2731-1c8f-428f-b615-830f1e988061" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
