# Experiment 2: DDL Commands

**Question 4**
---
Write an SQL query to add two new columns, designation and net_salary, to the table Companies. The designation column should have a data type of varchar(50), and the net_salary column should have a data type of number.

 

```sql
ALTER TABLE Companies
ADD COLUMN designation varchar(50);

ALTER TABLE Companies
ADD COLUMN net_salary number;

```

**Output:**

<img width="802" height="382" alt="image" src="https://github.com/user-attachments/assets/cb2e4c21-6b28-4c72-b65b-bcfe980ac5d0" />


**Question 5**
---
Create a table named Orders with the following constraints:

    OrderID as INTEGER should be the primary key.
    OrderDate as DATE should be not NULL.
    CustomerID as INTEGER should be a foreign key referencing Customers(CustomerID).


```sql
CREATE TABLE Orders (
    OrderID INTEGER PRIMARY KEY,
    OrderDate DATE NOT NULL,
    CustomerID INTEGER,
    FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID)
);

```

**Output:**

<img width="825" height="333" alt="image" src="https://github.com/user-attachments/assets/cc7ccd5f-ee7a-4a8a-ac00-d5700ac82b0d" />


**Question 6**
---
Write a SQL query to Rename the "city" column to "location" in the "customer" table.

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002

 

```sql
ALTER TABLE customer
RENAME COLUMN city TO location;

```

**Output:**

<img width="829" height="398" alt="image" src="https://github.com/user-attachments/assets/3c988350-a12f-4cc8-8270-8f34aae1df60" />


**Question 7**
---
Create a table named Attendance with the following constraints:

    AttendanceID as INTEGER should be the primary key.
    EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
    AttendanceDate as DATE.
    Status as TEXT should be one of 'Present', 'Absent', 'Leave'.


```sql
CREATE TABLE Attendance (
    AttendanceID INTEGER PRIMARY KEY,
    EmployeeID INTEGER,
    AttendanceDate DATE,
    Status TEXT CHECK (Status IN ('Present', 'Absent', 'Leave')),
    FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID)
);

```

**Output:**

<img width="825" height="345" alt="image" src="https://github.com/user-attachments/assets/fb22e868-9318-48bc-84c3-3914d2585f5d" />


**Question 8**
---
Create a table named Products with the following columns:

    ProductID as INTEGER
    ProductName as TEXT
    Price as REAL
    Stock as INTEGER


```sql
CREATE TABLE Products (
    ProductID INTEGER,
    ProductName TEXT,
    Price REAL,
    Stock INTEGER
);

```

**Output:**

<img width="815" height="374" alt="image" src="https://github.com/user-attachments/assets/3d598e5c-93e1-4a8c-ac8c-89c7a4857f8e" />


**Question 9**
---
Create a table named ProjectAssignments with the following constraints:

    AssignmentID as INTEGER should be the primary key.
    EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
    ProjectID as INTEGER should be a foreign key referencing Projects(ProjectID).
    AssignmentDate as DATE should be NOT NULL.


```sql

CREATE TABLE ProjectAssignments (
    AssignmentID INTEGER PRIMARY KEY,
    EmployeeID INTEGER,
    ProjectID INTEGER,
    AssignmentDate DATE NOT NULL,
    FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID),
    FOREIGN KEY (ProjectID) REFERENCES Projects(ProjectID)
);

```

**Output:**

<img width="832" height="354" alt="image" src="https://github.com/user-attachments/assets/1a1b06b4-67b0-4fa0-a74d-985005725cda" />


**Question 10**
---
Create a table named Invoices with the following constraints:

    InvoiceID as INTEGER should be the primary key.
    InvoiceDate as DATE.
    DueDate as DATE should be greater than the InvoiceDate.
    Amount as REAL should be greater than 0.

For example:

```sql
CREATE TABLE Invoices (
    InvoiceID INTEGER PRIMARY KEY,
    InvoiceDate DATE,
    DueDate DATE CHECK (DueDate > InvoiceDate),
    Amount REAL CHECK (Amount > 0)
);
```

**Output:**
<img width="833" height="375" alt="image" src="https://github.com/user-attachments/assets/856bdc1e-8c98-4393-845e-5502064b3a4e" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
