# DBMS-Expt06

## Aim
To study and implement different types of joins.

## Theory
The SQL Joins clause is used to combine records from two or more tables in a database. A JOIN is a means for combining fields from two tables by using values common to each.The join is actually performed by the ‘where’ clause which combines specified rows of tables.


Syntax: 
SELECT column 1, column 2, column 3... 
FROM table_name1, table_name2 
WHERE table_name1.column name = table_name2.columnname;


Types of Joins:
Inner Join
Left (Outer) Join
Right (Outer) Join
Full (Outer) Join


INNER JOIN
The INNER JOIN keyword selects records that have matching values in both tables.


Syntax:
SELECT column_name(s)
FROM table1
INNER JOIN table2
ON table1.column_name = table2.column_name;
LEFT JOIN 
The LEFT JOIN keyword returns all records from the left table (table1), and the matching records from the right table (table2). The result is 0 records from the right side, if there is no match.
Syntax:
SELECT column_name(s)
FROM table1
LEFT JOIN table2
ON table1.column_name = table2.column_name;
RIGHT JOIN 
The RIGHT JOIN keyword returns all records from the right table (table2), and the matching records from the left table (table1). The result is 0 records from the left side, if there is no match.
Syntax:
SELECT column_name(s)
FROM table1
RIGHT JOIN table2
ON table1.column_name = table2.column_name;
FULL OUTER JOIN 
The FULL OUTER JOIN keyword returns all records when there is a match in left (table1) or right (table2) table records.
FULL OUTER JOIN and FULL JOIN are the same.
Syntax:
SELECT column_name(s)
FROM table1
FULL OUTER JOIN table2
ON table1.column_name = table2.column_name
WHERE condition;


### 1.From the following tables write a SQL query to display the customer name, customer city, grade, salesman, salesman city. The results should be sorted by ascending customer_id.  
![Screenshot 2024-04-24 205759](https://github.com/Harsayazheni/DBMS-Expt06/assets/118708467/056de56b-e231-4acd-9e95-85fd8a141b0a)

#### Query
```SELECT c.cust_name, c.city AS city, c.grade, s.name AS Salesman, s.city AS city
FROM customer c
JOIN salesman s ON c.salesman_id = s.salesman_id
ORDER BY c.customer_id ASC;

```
#### Output
![Screenshot 2024-04-24 205808](https://github.com/Harsayazheni/DBMS-Expt06/assets/118708467/70016e2e-0221-4aa0-ad3b-4d42f890c25d)

### 2. From the following tables write a SQL query to find salespeople who received commissions of more than 12 percent from the company. Return Customer Name, customer city, Salesman, commission.  
![Screenshot 2024-04-24 205819](https://github.com/Harsayazheni/DBMS-Expt06/assets/118708467/95aa1f72-9783-41c7-a979-a894e0d3b7a2)

#### Query
```SELECT 
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
#### Output
![Screenshot 2024-04-24 205829](https://github.com/Harsayazheni/DBMS-Expt06/assets/118708467/8d3f7f1d-4a11-465a-b0f1-3a0c3e311266)

### 3.write a SQL query to find the salesperson and customer who reside in the same city. Return Salesman, cust_name and city.
![Screenshot 2024-04-24 205839](https://github.com/Harsayazheni/DBMS-Expt06/assets/118708467/5f1284e1-7b72-43ea-aecc-c7ab0c888a35)

#### Query
```SELECT 
    s.name AS "Salesman",
    c.cust_name,
    c.city
FROM 
    salesman s
JOIN 
    customer c ON s.city = c.city;

```
#### Output
![Screenshot 2024-04-24 205849](https://github.com/Harsayazheni/DBMS-Expt06/assets/118708467/c2d3844e-140f-4e0a-adc4-ea978f3a8ab9)

### 4.Write the SQL query that achieves the selection of the "cust_name" column from the "customer" table (aliased as "c"), and the "ord_no," "ord_date," and "purch_amt" columns from the "orders" table (aliased as "o"), with a left join on the "customer_id" column.
![Screenshot 2024-04-24 205902](https://github.com/Harsayazheni/DBMS-Expt06/assets/118708467/2b34ff1d-6b3a-477f-b5b4-a879be9f64d6)

#### Query
```SELECT 
    c.cust_name,
    o.ord_no,
    o.ord_date,
    o.purch_amt
FROM 
    customer c
LEFT JOIN 
    orders o ON c.customer_id = o.customer_id;

```
#### Output
![Screenshot 2024-04-24 205916](https://github.com/Harsayazheni/DBMS-Expt06/assets/118708467/8b190873-45aa-47e6-93c2-418b43a33ccb)

### 5.Write the SQL query that achieves the selection of all columns from the "nurses" table (aliased as "n") and the "department_name" column from the "departments" table, with an inner join on the "department_id" column.
![Screenshot 2024-04-24 205931](https://github.com/Harsayazheni/DBMS-Expt06/assets/118708467/d24c9917-f7fd-41d0-8564-815a7b0fb9db)

#### Query
```SELECT 
    n.*,
    d.department_name
FROM 
    nurses n
INNER JOIN 
    departments d ON n.department_id = d.department_id;

```
#### Output
![Screenshot 2024-04-24 205939](https://github.com/Harsayazheni/DBMS-Expt06/assets/118708467/0889eb95-473e-4d29-b79c-91fca96cde55)

### 6.Write the SQL query that achieves the selection of the "cust_name" column from the "customer" table (aliased as "c"), with a left join on the "customer_id" column.
![Screenshot 2024-04-24 205948](https://github.com/Harsayazheni/DBMS-Expt06/assets/118708467/646303c0-660d-40db-96a9-c2187947c15b)

#### Query
```SELECT 
    c.cust_name
FROM 
    customer c
LEFT JOIN 
    orders o ON c.customer_id = o.customer_id;

```
#### Output
![Screenshot 2024-04-24 210000](https://github.com/Harsayazheni/DBMS-Expt06/assets/118708467/497763eb-a79b-4c70-82d4-60e8158d1ec9)

### 7.Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name"), with an inner join on the "patient_id" column and a condition filtering for test results with the test name 'Blood Pressure'.
![Screenshot 2024-04-24 210014](https://github.com/Harsayazheni/DBMS-Expt06/assets/118708467/a2992c7d-51b2-4754-80f0-6e253788bbd5)

#### Query
```SELECT 
    p.first_name AS patient_name
FROM 
    patients p
INNER JOIN 
    test_results tr ON p.patient_id = tr.patient_id
WHERE 
    tr.test_name = 'Blood Pressure';

```
#### Output
![Screenshot 2024-04-24 210023](https://github.com/Harsayazheni/DBMS-Expt06/assets/118708467/8d940842-8c40-408a-b441-1d0a0479ce96)

### 8.From the following tables write a SQL query to locate those salespeople who do not live in the same city where their customers live and have received a commission of more than 12% from the company. Return Customer Name, customer city, Salesman, salesman city, commission.  
![Screenshot 2024-04-24 210034](https://github.com/Harsayazheni/DBMS-Expt06/assets/118708467/9215ad18-1a82-4e16-9e91-4a5453834aa4)

#### Query
```SELECT 
    c.cust_name AS "Customer Name",
    c.city AS "city",
    s.name AS "Salesman",
    s.city AS "city",
    s.commission AS "commission"
FROM 
    customer c
INNER JOIN 
    salesman s ON c.salesman_id = s.salesman_id
WHERE 
    c.city <> s.city
    AND s.commission > 0.12;

```
#### Output
![Screenshot 2024-04-24 210047](https://github.com/Harsayazheni/DBMS-Expt06/assets/118708467/35796e20-50e7-4ba0-9358-eecc060fea88)

### 9.Write the SQL query that achieves the selection of the first name from the "patients" table and all columns from the "surgeries" table, with an inner join on the "patient_id" column and a condition filtering for patients with a date of birth after '1990-01-01'.
![Screenshot 2024-04-24 210056](https://github.com/Harsayazheni/DBMS-Expt06/assets/118708467/7ce9e400-1097-4bed-966e-269941053138)

#### Query
```SELECT 
    p.first_name,
    s.surgery_id,
    s.patient_id,
    s.surgeon_id,
    s.surgery_date
FROM 
    patients p
INNER JOIN 
    surgeries s ON p.patient_id = s.patient_id
WHERE 
    p.date_of_birth > '1990-01-01';
```
#### Output
![Screenshot 2024-04-24 210105](https://github.com/Harsayazheni/DBMS-Expt06/assets/118708467/099ba780-074d-4477-8b60-e938f0d85c49)

### 10.Write the SQL query that achieves the selection of the "cust_name" column from the "customer" table (aliased as "c"), and the "ord_no," "ord_date," and "purch_amt" columns from the "orders" table (aliased as "o"), with a left join on the "customer_id" column.
![Screenshot 2024-04-24 205902](https://github.com/Harsayazheni/DBMS-Expt06/assets/118708467/2b34ff1d-6b3a-477f-b5b4-a879be9f64d6)

#### Query
```SELECT 
    c.cust_name,
    o.ord_no,
    o.ord_date,
    o.purch_amt
FROM 
    customer c
LEFT JOIN 
    orders o ON c.customer_id = o.customer_id;

```
#### Output
![Screenshot 2024-04-24 205916](https://github.com/Harsayazheni/DBMS-Expt06/assets/118708467/8b190873-45aa-47e6-93c2-418b43a33ccb)


## Result
Thus , To study and implement different types of joins is done successfully.
