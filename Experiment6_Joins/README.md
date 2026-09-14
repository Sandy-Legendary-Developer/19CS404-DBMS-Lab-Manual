# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**
![image](https://github.com/user-attachments/assets/a0ec420f-54ff-43d4-b3e5-8278822f43fb)

-- Paste Question 1 here

```sql
SELECT 
    c.cust_name,
    o.ord_no,
    o.ord_date,
    o.purch_amt
FROM 
    customer c
LEFT JOIN 
    orders o
ON 
    c.customer_id = o.customer_id;
```

**Output:**

![image](https://github.com/user-attachments/assets/f8354d9d-88a0-438e-9868-416112875650)


**Question 2**
---
![image](https://github.com/user-attachments/assets/2514d0ac-b414-498f-83f4-7a647c84b5ad)


```sql
SELECT 
    s.name AS Salesman,
    c.cust_name,
    s.city
FROM 
    salesman s
JOIN 
    customer c
ON 
    s.city = c.city;
```

**Output:**

![image](https://github.com/user-attachments/assets/795e1278-085e-468f-8874-cbdf74d318db)


**Question 3**
---
![image](https://github.com/user-attachments/assets/1efbcc3d-781e-4bf4-9b89-b752af010504)


```sql
SELECT 
    p.first_name AS patient_name,
    d.first_name AS doctor_name
FROM 
    patients p
INNER JOIN 
    doctors d
ON 
    p.doctor_id = d.doctor_id
WHERE 
    p.discharge_date IS NOT NULL;
```

**Output:**
![image](https://github.com/user-attachments/assets/63fc74eb-48f2-469a-9ecc-60bb41249f07)


**Question 4**
---
![image](https://github.com/user-attachments/assets/c001a184-a5ca-4cca-bcb9-998e00530528)

```sql
SELECT 
    o.ord_no,
    o.purch_amt,
    o.ord_date,
    c.cust_name,
    c.city AS customer_city,
    c.grade,
    s.name AS salesman_name,
    s.city AS salesman_city,
    s.commission
FROM 
    orders o
JOIN 
    customer c ON o.customer_id = c.customer_id
JOIN 
    salesman s ON o.salesman_id = s.salesman_id;

```

**Output:**

![image](https://github.com/user-attachments/assets/9b378e5a-d55e-4b7e-944f-9b49f4000890)


**Question 5**
---
![image](https://github.com/user-attachments/assets/26ad2708-4cb4-4514-a3a7-ea3470b9a8f7)


```sql
SELECT 
    p.first_name AS patient_name,
    t.*
FROM 
    patients p
INNER JOIN 
    test_results t ON p.patient_id = t.patient_id
WHERE 
    p.admission_date BETWEEN '2024-01-01' AND '2024-01-31';

```

**Output:**

![image](https://github.com/user-attachments/assets/57f78e2a-fa88-4fd9-8cc4-7381ae81ca64)


**Question 6**
---
![image](https://github.com/user-attachments/assets/6fb576f3-b78b-400b-83e4-b51c3c5b9915)


```sql
SELECT 
    p.first_name AS patient_name,
    d.first_name AS doctor_name
FROM 
    patients p
INNER JOIN 
    doctors d ON p.doctor_id = d.doctor_id
WHERE 
    p.discharge_date IS NULL;
```

**Output:**

![image](https://github.com/user-attachments/assets/0767e033-da72-4cb6-8bd9-34a2a230f462)


**Question 7**
---
![image](https://github.com/user-attachments/assets/e32fb9f7-1a9d-4efb-9563-972622a84673)



```sql
SELECT
    c.cust_name AS "Customer Name",
    c.city AS "city",
    s.name AS "Salesman",
    s.commission AS "commission"
FROM
    customer c
JOIN
    salesman s ON c.salesman_id = s.salesman_id
WHERE
    s.commission > 0.12;
```

**Output:**

![image](https://github.com/user-attachments/assets/b0d59161-d1ed-4ce9-8cd6-8619a59b5955)


**Question 8**
---
![image](https://github.com/user-attachments/assets/38e93225-dd69-474d-bbac-ae70575af086)


```sql
SELECT
    c.cust_name AS "Customer Name",
    c.city AS "city",
    s.name AS "Salesman",
    s.commission AS "commission"
FROM
    customer c
JOIN
    salesman s ON c.salesman_id = s.salesman_id;
```

**Output:**
![image](https://github.com/user-attachments/assets/f9aa5d4b-9df0-4116-ade8-3a36123b9668)


**Question 9**
---
![image](https://github.com/user-attachments/assets/462953f0-4ce9-495e-b288-063fcc5070f2)


```sql
SELECT 
    s.name,
    c.cust_name,
    c.city,
    c.grade,
    c.salesman_id
FROM 
    salesman s
LEFT JOIN 
    customer c ON s.salesman_id = c.salesman_id
WHERE 
    s.salesman_id IN (
        SELECT salesman_id
        FROM customer
        GROUP BY salesman_id
        HAVING COUNT(*) > 1
    );
```

**Output:**

![image](https://github.com/user-attachments/assets/3350ccd4-6a5c-4123-99c7-c8c55baf3b7b)


**Question 10**
---
![image](https://github.com/user-attachments/assets/4f927340-3f6e-4a84-bd85-13a859864430)


```sql

SELECT 
    n.nurse_id,
    d.department_name
FROM 
    nurses n
INNER JOIN 
    departments d ON n.department_id = d.department_id
WHERE 
    n.first_name = 'David'
    AND n.last_name = 'Moore';

```

**Output:**

![image](https://github.com/user-attachments/assets/a89dfd1f-b8db-405b-8466-9a09e8e38c1a)



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
