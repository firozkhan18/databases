Prepare Sample Data To Practice SQL Skills
Sample Table – Worker
|WORKER_ID	|FIRST_NAME|	LAST_NAME|	SALARY|	JOINING_DATE	|DEPARTMENT|
|-----|----------|----------|----------|----------|----------|
|001	|Monika	|Arora	|100000	|2021-02-20 09:00:00|	HR|
|002	|Niharika	|Verma	|80000	|2021-06-11 09:00:00|	Admin|
|003	|Vishal	|Singhal	|300000	|2021-02-20 09:00:00|	HR|
|004	|Amitabh	|Singh	|500000	|2021-02-20 09:00:00|	Admin|
|005	|Vivek	|Bhati	|500000	|2021-06-11 09:00:00|	Admin|
|006	|Vipul	|Diwan	|200000	|2021-06-11 09:00:00|	Account|
|007	|Satish	|Kumar	|75000	|2021-01-20 09:00:00|	Account|
|008	|Geetika	|Chauhan	|90000	|2021-04-11 09:00:00|	Admin|

Worker Table
Sample Table – Bonus
|WORKER_REF_ID	|BONUS_DATE	|BONUS_AMOUNT|
|-----|----------|----------|
|1	|2023-02-20 00:00:00	|5000|
|2	|2023-06-11 00:00:00	|3000|
|3	|2023-02-20 00:00:00	|4000|
|1	|2023-02-20 00:00:00	|4500|
|2	|2023-06-11 00:00:00	|3500|

Bonus Table
Sample Table – Title
|WORKER_REF_ID	|WORKER_TITLE	|AFFECTED_FROM|
|-----|----------|----------|
|1	|Manager	|2023-02-20 00:00:00|
|2	|Executive	|2023-06-11 00:00:00|
|8	|Executive	|2023-06-11 00:00:00|
|5	|Manager	|2023-06-11 00:00:00|
|4	|Asst. Manager	|2023-06-11 00:00:00|
|7	|Executive	|2023-06-11 00:00:00|
|6	|Lead	|2023-06-11 00:00:00|
|3	|Lead	|2023-06-11 00:00:00|

Title Table
To prepare the sample data, run the following queries in your database query executor or SQL command line. We’ve tested them with the latest version of MySQL Server and MySQL Workbench query browser. You can download these tools and install them to execute the SQL queries. However, these queries will run fine in any online MySQL compiler, you may use them.

SQL Script to Seed Sample Data.
Initialize Test Data
Run the following script to create test tables and insert data.
Run

```sql
CREATE TABLE Worker (
    WORKER_ID INT NOT NULL PRIMARY KEY,
    FIRST_NAME CHAR(25),
    LAST_NAME CHAR(25),
    SALARY INT,
    JOINING_DATE DATETIME,
    DEPARTMENT CHAR(25)
);
```
```sql
INSERT INTO Worker (WORKER_ID, FIRST_NAME, LAST_NAME, SALARY, JOINING_DATE, DEPARTMENT) VALUES
    (1, 'Monika', 'Arora', 100000, '2021-02-20 09:00:00', 'HR'),
    (2, 'Niharika', 'Verma', 80000, '2021-06-11 09:00:00', 'Admin'),
    (3, 'Vishal', 'Singhal', 300000, '2021-02-20 09:00:00', 'HR'),
    (4, 'Amitabh', 'Singh', 500000, '2021-02-20 09:00:00', 'Admin'),
    (5, 'Vivek', 'Bhati', 500000, '2021-06-11 09:00:00', 'Admin'),
    (6, 'Vipul', 'Diwan', 200000, '2021-06-11 09:00:00', 'Account'),
    (7, 'Satish', 'Kumar', 75000, '2021-01-20 09:00:00', 'Account'),
    (8, 'Geetika', 'Chauhan', 90000, '2021-04-11 09:00:00', 'Admin');
```
```sql
CREATE TABLE Bonus (
    WORKER_REF_ID INT,
    BONUS_AMOUNT INT,
    BONUS_DATE DATETIME,
    FOREIGN KEY (WORKER_REF_ID) REFERENCES Worker(WORKER_ID) ON DELETE CASCADE
);
```
```sql
INSERT INTO Bonus (WORKER_REF_ID, BONUS_AMOUNT, BONUS_DATE) VALUES
    (1, 5000, '2023-02-20'),
    (2, 3000, '2023-06-11'),
    (3, 4000, '2023-02-20'),
    (1, 4500, '2023-02-20'),
    (2, 3500, '2023-06-11');
```
```sql
CREATE TABLE Title (
    WORKER_REF_ID INT,
    WORKER_TITLE CHAR(25),
    AFFECTED_FROM DATETIME,
    FOREIGN KEY (WORKER_REF_ID) REFERENCES Worker(WORKER_ID) ON DELETE CASCADE
);
```
```sql
INSERT INTO Title (WORKER_REF_ID, WORKER_TITLE, AFFECTED_FROM) VALUES
    (1, 'Manager', '2023-02-20 00:00:00'),
    (2, 'Executive', '2023-06-11 00:00:00'),
    (8, 'Executive', '2023-06-11 00:00:00'),
    (5, 'Manager', '2023-06-11 00:00:00'),
    (4, 'Asst. Manager', '2023-06-11 00:00:00'),
    (7, 'Executive', '2023-06-11 00:00:00'),
    (6, 'Lead', '2023-06-11 00:00:00'),
    (3, 'Lead', '2023-06-11 00:00:00');
``` 
Tables and data initialized successfully!
Running the above SQL on any MySQL instance will show a result similar to the one below.

SQL Query Questions - Creating Sample Data
Creating Sample Data to Practice SQL Skill.
Start with 20 Basic SQL Questions for Practice
Below are some of the most commonly asked SQL query questions and answers for practice. Get a timer to track your progress and start practicing.

### Q-1. Write an SQL query to fetch “FIRST_NAME” from the Worker table using the alias name <WORKER_NAME>.
Ans.

The required query is:

### Query #1
RunShow Solution
```sql
Select FIRST_NAME AS WORKER_NAME from Worker;
```
SQL query executed successfully!
Details
|WORKER_NAME|
|-----|
|Monika|
|Niharika|
|Vishal|
|Amitabh|
|Vivek|
|Vipul|
|Satish|
|Geetika|

### Q-2. Write an SQL query to fetch “FIRST_NAME” from the Worker table in upper case.
Ans.

The required query is:

### Query #2
RunShow Solution
```sql
Select upper(FIRST_NAME) from Worker;
```
SQL query executed successfully!
Details
|upper(FIRST_NAME)
|-----|
|MONIKA|
|NIHARIKA|
|VISHAL|
|AMITABH|
|VIVEK|
|VIPUL|
|SATISH|
|GEETIKA|

### Q-3. Write an SQL query to fetch unique values of DEPARTMENT from the Worker table.
Ans.

The required query is:

### Query #3
RunShow Solution
```sql
Select distinct DEPARTMENT from Worker;
```
SQL query executed successfully!
Details
|DEPARTMENT|
|-----|
|HR|
|Admin|
|Account|

### Q-4. Write an SQL query to print the first three characters of  FIRST_NAME from the Worker table.
Ans.

The required query is:

### Query #4
RunShow Solution
```sql
Select substring(FIRST_NAME,1,3) from Worker;
```
SQL query executed successfully!
Details
|substring(FIRST_NAME,1,3)|
|-----|
|Mon|
|Nih|
|Vis|
|Ami|
|Viv|
|Vip|
|Sat|
|Gee|

### Q-5. Write an SQL query to find the position of the alphabet (‘a’) in the first name column ‘Amitabh’ from the Worker table.
Ans.

The required query is:

### Query #5
RunShow Solution
```sql
SELECT INSTR(FIRST_NAME, 'a') FROM Worker WHERE FIRST_NAME = 'Amitabh';
```
SQL query executed successfully!
Details
|INSTR(FIRST_NAME, 'a')|
|-----|
|5|

### Q-6. Write an SQL query to print the FIRST_NAME from the Worker table after removing white spaces from the right side.
Ans.

The required query is:

### Query #6
RunShow Solution
```sql
Select RTRIM(FIRST_NAME) from Worker;
```
SQL query executed successfully!
Details
RTRIM(FIRST_NAME)
|-----|
Monika
Niharika
Vishal
Amitabh
Vivek
Vipul
Satish
Geetika
### Q-7. Write an SQL query to print the DEPARTMENT from the Worker table after removing white spaces from the left side.
Ans.

The required query is:

### Query #7
RunShow Solution
```sql
Select LTRIM(DEPARTMENT) from Worker;
```
SQL query executed successfully!
Details
LTRIM(DEPARTMENT)
|-----|
HR
Admin
HR
Admin
Admin
Account
Account
Admin
### Q-8. Write an SQL query that fetches the unique values of DEPARTMENT from the Worker table and prints its length.
Ans.

The required query is:

### Query #8
RunShow Solution
```sql
SELECT DISTINCT DEPARTMENT, LENGTH(DEPARTMENT) AS Department_Length FROM Worker;
```
SQL query executed successfully!
Details
DEPARTMENT	Department_Length
HR	2
Admin	5
Account	7
### Q-9. Write an SQL query to print the FIRST_NAME from the Worker table after replacing ‘a’ with ‘A’.
Ans.

The required query is:

### Query #9
RunShow Solution
```sql
Select REPLACE(FIRST_NAME,'a','A') from Worker;
```
SQL query executed successfully!
Details
REPLACE(FIRST_NAME,'a','A')
|-----|
MonikA
NihArikA
VishAl
AmitAbh
Vivek
Vipul
SAtish
GeetikA
### Q-10. Write an SQL query to print the FIRST_NAME and LAST_NAME from the Worker table into a single column COMPLETE_NAME. A space char should separate them.
Ans.

The required query is:

### Query #10
RunShow Solution
```sql
SELECT FIRST_NAME || ' ' || LAST_NAME AS COMPLETE_NAME FROM Worker;
```
SQL query executed successfully!
Details
COMPLETE_NAME
|-----|
Monika Arora
Niharika Verma
Vishal Singhal
Amitabh Singh
Vivek Bhati
Vipul Diwan
Satish Kumar
Geetika Chauhan
### Q-11. Write an SQL query to print all Worker details from the Worker table order by FIRST_NAME Ascending.
Ans.

The required query is:

### Query #11
RunShow Solution
```sql
Select * from Worker order by FIRST_NAME asc;
```
SQL query executed successfully!
Details
|WORKER_ID	|FIRST_NAME|	LAST_NAME|	SALARY|	JOINING_DATE|	DEPARTMENT|
|-----|-----|-----|-----|-----|-----|
|4	|Amitabh	|Singh	|500000	|2021-02-20 09:00:00	|Admin|
|8	|Geetika	|Chauhan	|90000	|2021-04-11 09:00:00	|Admin|
|1	|Monika	|Arora	|100000	|2021-02-20 09:00:00	|HR|
|2	|Niharika	|Verma	|80000	|2021-06-11 09:00:00	|Admin|
|7	|Satish	|Kumar	|75000	|2021-01-20 09:00:00	|Account|
|6	|Vipul	|Diwan	|200000	|2021-06-11 09:00:00	|Account|
|3	|Vishal	|Singhal	|300000	|2021-02-20 09:00:00	|HR|
|5	|Vivek	|Bhati	|500000	|2021-06-11 09:00:00	|Admin|
### Q-12. Write an SQL query to print all Worker details from the Worker table order by FIRST_NAME Ascending and DEPARTMENT Descending.
Ans.


The required query is:

### Query #12
RunShow Solution
```sql
Select * from Worker order by FIRST_NAME asc, DEPARTMENT desc;
```
SQL query executed successfully!
Details

|WORKER_ID	|FIRST_NAME|	LAST_NAME|	SALARY|	JOINING_DATE|	DEPARTMENT|
|-----|-----|-----|-----|-----|-----|
|4	|Amitabh	|Singh	|500000	|2021-02-20 09:00:00|	Admin|
|8	|Geetika	|Chauhan	|90000	|2021-04-11 09:00:00|	Admin|
|1	|Monika	|Arora	|100000	|2021-02-20 09:00:00|	HR|
|2	|Niharika	|Verma	|80000	|2021-06-11 09:00:00|	Admin|
|7	|Satish	|Kumar	|75000	|2021-01-20 09:00:00|	Account|
|6	|Vipul	|Diwan	|200000	|2021-06-11 09:00:00|	Account|
|3	|Vishal	|Singhal	|300000	|2021-02-20 09:00:00|	HR|
|5	|Vivek	|Bhati	|500000	|2021-06-11 09:00:00|	Admin|

### Q-13. Write an SQL query to print details for Workers with the first names “Vipul” and “Satish” from the Worker table.
Ans.

The required query is:

### Query #13
RunShow Solution
```sql
Select * from Worker where FIRST_NAME in ('Vipul','Satish');
```
SQL query executed successfully!
Details
|WORKER_ID	|FIRST_NAME|	LAST_NAME|	SALARY|	JOINING_DATE|	DEPARTMENT|
|-----|-----|-----|-----|-----|-----|
|6	|Vipul	|Diwan|	200000|	2021-06-11 09:00:00|	Account|
|7	|Satish	|Kumar|	75000|	2021-01-20 09:00:00|	Account|

### Q-14. Write an SQL query to print details of workers excluding first names, “Vipul” and “Satish” from the Worker table.
Ans.

The required query is:

### Query #14
RunShow Solution
Select * from Worker where FIRST_NAME not in ('Vipul','Satish');
```
SQL query executed successfully!
Details
|WORKER_ID	|FIRST_NAME|	LAST_NAME|	SALARY|	JOINING_DATE|	DEPARTMENT|
|-----|-----|-----|-----|-----|-----|
1	Monika	Arora	100000	2021-02-20 09:00:00	HR
2	Niharika	Verma	80000	2021-06-11 09:00:00	Admin
3	Vishal	Singhal	300000	2021-02-20 09:00:00	HR
4	Amitabh	Singh	500000	2021-02-20 09:00:00	Admin
5	Vivek	Bhati	500000	2021-06-11 09:00:00	Admin
8	Geetika	Chauhan	90000	2021-04-11 09:00:00	Admin
### Q-15. Write an SQL query to print details of Workers with DEPARTMENT name as “Admin”.
Ans.


The required query is:

### Query #15
RunShow Solution
```sql
Select * from Worker where DEPARTMENT like 'Admin%';
```
SQL query executed successfully!
Details
|WORKER_ID	|FIRST_NAME|	LAST_NAME|	SALARY|	JOINING_DATE|	DEPARTMENT|
|-----|-----|-----|-----|-----|-----|
2	Niharika	Verma	80000	2021-06-11 09:00:00	Admin
4	Amitabh	Singh	500000	2021-02-20 09:00:00	Admin
5	Vivek	Bhati	500000	2021-06-11 09:00:00	Admin
8	Geetika	Chauhan	90000	2021-04-11 09:00:00	Admin
### Q-16. Write an SQL query to print details of the Workers whose FIRST_NAME contains ‘a’.
Ans.

The required query is:


### Query #16
RunShow Solution
```sql
Select * from Worker where FIRST_NAME like '%a%';
```
SQL query executed successfully!
Details
|WORKER_ID	|FIRST_NAME|	LAST_NAME|	SALARY|	JOINING_DATE|	DEPARTMENT|
|-----|-----|-----|-----|-----|-----|
1	Monika	Arora	100000	2021-02-20 09:00:00	HR
2	Niharika	Verma	80000	2021-06-11 09:00:00	Admin
3	Vishal	Singhal	300000	2021-02-20 09:00:00	HR
4	Amitabh	Singh	500000	2021-02-20 09:00:00	Admin
7	Satish	Kumar	75000	2021-01-20 09:00:00	Account
8	Geetika	Chauhan	90000	2021-04-11 09:00:00	Admin
### Q-17. Write an SQL query to print details of the Workers whose FIRST_NAME ends with ‘a’.
Ans.

The required query is:

### Query #17
RunShow Solution
```sql
Select * from Worker where FIRST_NAME like '%a';
```
SQL query executed successfully!
Details
|WORKER_ID	|FIRST_NAME|	LAST_NAME|	SALARY|	JOINING_DATE|	DEPARTMENT|
|-----|-----|-----|-----|-----|-----|
1	Monika	Arora	100000	2021-02-20 09:00:00	HR
2	Niharika	Verma	80000	2021-06-11 09:00:00	Admin
8	Geetika	Chauhan	90000	2021-04-11 09:00:00	Admin
### Q-18. Write an SQL query to print details of the Workers whose FIRST_NAME ends with ‘h’ and contains six alphabets.
Ans.

The required query is:

### Query #18
RunShow Solution
```sql
Select * from Worker where FIRST_NAME like '_____h';
```
SQL query executed successfully!
Details
|WORKER_ID	|FIRST_NAME|	LAST_NAME|	SALARY|	JOINING_DATE|	DEPARTMENT|
|-----|-----|-----|-----|-----|-----|
7	Satish	Kumar	75000	2021-01-20 09:00:00	Account
### Q-19. Write an SQL query to print details of the Workers whose SALARY lies between 100000 and 500000.
Ans.

The required query is:

### Query #19
RunShow Solution
```sql
Select * from Worker where SALARY between 100000 and 500000;
```
SQL query executed successfully!
Details
|WORKER_ID	|FIRST_NAME|	LAST_NAME|	SALARY|	JOINING_DATE|	DEPARTMENT|
|-----|-----|-----|-----|-----|-----|
1	Monika	Arora	100000	2021-02-20 09:00:00	HR
3	Vishal	Singhal	300000	2021-02-20 09:00:00	HR
4	Amitabh	Singh	500000	2021-02-20 09:00:00	Admin
5	Vivek	Bhati	500000	2021-06-11 09:00:00	Admin
6	Vipul	Diwan	200000	2021-06-11 09:00:00	Account
### Q-20. Write an SQL query to print details of the Workers who joined in Feb 2021.
Ans.

The required query is:

### Query #20
RunShow Solution
```sql
SELECT * FROM Worker WHERE strftime('%Y', JOINING_DATE) = '2021' AND strftime('%m', JOINING_DATE) = '02';
```
SQL query executed successfully!
Details
|WORKER_ID	|FIRST_NAME|	LAST_NAME|	SALARY|	JOINING_DATE|	DEPARTMENT|
|-----|-----|-----|-----|-----|-----|
1	Monika	Arora	100000	2021-02-20 09:00:00	HR
3	Vishal	Singhal	300000	2021-02-20 09:00:00	HR
4	Amitabh	Singh	500000	2021-02-20 09:00:00	Admin
12 Medium SQL Query Interview Questions / Answers for Practice
At this point, you have acquired a good understanding of the basics of SQL, let’s move on to some more intermediate-level SQL query interview questions. These questions will require us to use more advanced SQL syntax and concepts, such as GROUP BY, HAVING, and ORDER BY.


### Q-21. Write an SQL query to fetch the count of employees working in the department ‘Admin’.
Ans.

The required query is:

### Query #21
RunShow Solution
```sql
SELECT COUNT(*) FROM Worker WHERE DEPARTMENT = 'Admin';
```
SQL query executed successfully!
Details
COUNT(*)
4
### Q-22. Write an SQL query to fetch worker names with salaries >= 50000 and <= 100000.
Ans.


The required query is:

### Query #22
RunShow Solution
```sql
SELECT FIRST_NAME || ' ' || LAST_NAME AS Worker_Name, Salary FROM Worker WHERE Salary BETWEEN 50000 AND 100000;
```
SQL query executed successfully!
Details
Worker_Name	SALARY
Monika Arora	100000
Niharika Verma	80000
Satish Kumar	75000
Geetika Chauhan	90000
### Q-23. Write an SQL query to fetch the number of workers for each department in descending order.
Ans.

The required query is:


### Query #23
RunShow Solution
```sql
SELECT DEPARTMENT, count(WORKER_ID) No_Of_Workers FROM Worker GROUP BY DEPARTMENT ORDER BY No_Of_Workers DESC;
```
SQL query executed successfully!
Details
DEPARTMENT	No_Of_Workers
Admin	4
HR	2
Account	2
### Q-24. Write an SQL query to print details of the Workers who are also Managers.
Ans.

The required query is:

### Query #24
RunShow Solution
```sql
SELECT DISTINCT W.FIRST_NAME, T.WORKER_TITLE FROM Worker W INNER JOIN Title T ON W.WORKER_ID = T.WORKER_REF_ID AND T.WORKER_TITLE in ('Manager');
```
SQL query executed successfully!
Details
FIRST_NAME	WORKER_TITLE
Monika	Manager
Vivek	Manager
### Q-25. Write an SQL query to fetch duplicate records having matching data in some fields of a table.
Ans.


The required query is:

### Query #25
RunShow Solution
```sql
SELECT WORKER_TITLE, AFFECTED_FROM, COUNT(*) FROM Title GROUP BY WORKER_TITLE, AFFECTED_FROM HAVING COUNT(*) > 1;
```
SQL query executed successfully!
Details
WORKER_TITLE	AFFECTED_FROM	COUNT(*)
Executive	2023-06-11 00:00:00	3
Lead	2023-06-11 00:00:00	2
### Q-26. Write an SQL query to show only odd rows from a table.
Ans.

The required query is:


### Query #26
RunShow Solution
```sql
SELECT * FROM Worker WHERE WORKER_ID % 2 <> 0;
```
SQL query executed successfully!
Details
|WORKER_ID	|FIRST_NAME|	LAST_NAME|	SALARY|	JOINING_DATE|	DEPARTMENT|
|-----|-----|-----|-----|-----|-----|
1	Monika	Arora	100000	2021-02-20 09:00:00	HR
3	Vishal	Singhal	300000	2021-02-20 09:00:00	HR
5	Vivek	Bhati	500000	2021-06-11 09:00:00	Admin
7	Satish	Kumar	75000	2021-01-20 09:00:00	Account
### Q-27. Write an SQL query to show only even rows from a table.
Ans.

The required query is:

### Query #27
RunShow Solution
```sql
SELECT * FROM Worker WHERE WORKER_ID % 2 = 0;
```
SQL query executed successfully!
Details
|WORKER_ID	|FIRST_NAME|	LAST_NAME|	SALARY|	JOINING_DATE|	DEPARTMENT|
|-----|-----|-----|-----|-----|-----|
2	Niharika	Verma	80000	2021-06-11 09:00:00	Admin
4	Amitabh	Singh	500000	2021-02-20 09:00:00	Admin
6	Vipul	Diwan	200000	2021-06-11 09:00:00	Account
8	Geetika	Chauhan	90000	2021-04-11 09:00:00	Admin
### Q-28. Write an SQL query to clone a new table from another table.
Ans.

The general query to clone a table with data is:

### Query #28
RunShow Solution
```sql
CREATE TABLE WorkerClone AS SELECT * FROM Worker;
```
SQL query executed successfully!
Details
No records found.

### Q-29. Write an SQL query to fetch intersecting records of two tables.
Ans.

The required query is:

### Query #29
RunShow Solution
```sql
SELECT * FROM Worker INTERSECT SELECT * FROM WorkerClone;
```
SQL query executed successfully!
Details
|WORKER_ID	|FIRST_NAME|	LAST_NAME|	SALARY|	JOINING_DATE|	DEPARTMENT|
|-----|-----|-----|-----|-----|-----|
1	Monika	Arora	100000	2021-02-20 09:00:00	HR
2	Niharika	Verma	80000	2021-06-11 09:00:00	Admin
3	Vishal	Singhal	300000	2021-02-20 09:00:00	HR
4	Amitabh	Singh	500000	2021-02-20 09:00:00	Admin
5	Vivek	Bhati	500000	2021-06-11 09:00:00	Admin
6	Vipul	Diwan	200000	2021-06-11 09:00:00	Account
7	Satish	Kumar	75000	2021-01-20 09:00:00	Account
8	Geetika	Chauhan	90000	2021-04-11 09:00:00	Admin
### Q-30. Write an SQL query to show records from one table that another table does not have.
Ans.

The required query is:

### Query #30
RunShow Solution
```sql
SELECT * FROM Worker EXCEPT SELECT * FROM WorkerClone;
```
SQL query executed successfully!
Details
No records found.

### Q-31. Write an SQL query to show the current date and time.
Ans.

The following MySQL query returns the current date:

### Query #31
RunShow Solution
```sql
SELECT CURRENT_TIMESTAMP;
```
SQL query executed successfully!
Details
CURRENT_TIMESTAMP
2024-08-01 14:24:05
### Q-32. Write an SQL query to show the top n (say 10) records of a table.
Ans.

Specify the SQL query in the below code box:

### Query #32
RunShow Solution
```sql
SELECT *
FROM Worker
ORDER BY SALARY DESC  -- Order by salary in descending order to get the highest salaries first
LIMIT 10;             -- Limit the result to the top 10 records
```
SQL query executed successfully!
Details
|WORKER_ID	|FIRST_NAME|	LAST_NAME|	SALARY|	JOINING_DATE|	DEPARTMENT|
|-----|-----|-----|-----|-----|-----|
4	Amitabh	Singh	500000	2021-02-20 09:00:00	Admin
5	Vivek	Bhati	500000	2021-06-11 09:00:00	Admin
3	Vishal	Singhal	300000	2021-02-20 09:00:00	HR
6	Vipul	Diwan	200000	2021-06-11 09:00:00	Account
1	Monika	Arora	100000	2021-02-20 09:00:00	HR
8	Geetika	Chauhan	90000	2021-04-11 09:00:00	Admin
2	Niharika	Verma	80000	2021-06-11 09:00:00	Admin
7	Satish	Kumar	75000	2021-01-20 09:00:00	Account
18 Complex SQL Queries for Practice
Now, that you have built a solid foundation in intermediate SQL, It’s time to practice with some advanced SQL query questions with answers. These interview questions involve queries with more complex SQL syntax and concepts, such as nested queries, joins, unions, and intersects.

### Q-33. Write an SQL query to determine the nth (say n=5) highest salary from a table.
Ans.

MySQL query to find the nth highest salary:


### Query #33
RunShow Solution
```sql
SELECT DISTINCT SALARY
FROM Worker
ORDER BY SALARY DESC
LIMIT 1 OFFSET 4;
```
SQL query executed successfully!
Details
SALARY
90000
SQL Server query to find the nth highest salary:
```sql
SELECT TOP 1 Salary
FROM (
 SELECT DISTINCT TOP n Salary
 FROM Worker 
 ORDER BY Salary DESC
 )
ORDER BY Salary ASC;
```
Copy
### Q-34. Write an SQL query to determine the 5th highest salary without using the TOP or limit method.
Ans.

The following query is using the correlated subquery to return the 5th highest salary:

### Query #34
RunShow Solution
```sql
SELECT Salary FROM Worker W1 WHERE 4 = (SELECT COUNT(DISTINCT W2.Salary) FROM Worker W2 WHERE W2.Salary >= W1.Salary);
```
SQL query executed successfully!
Details
SALARY
100000
Use the following generic method to find the nth highest salary without using TOP or limit.
```sql
SELECT Salary
FROM Worker W1
WHERE n-1 = (
 SELECT COUNT( DISTINCT ( W2.Salary ) )
 FROM Worker W2
 WHERE W2.Salary >= W1.Salary
 );
```
### Q-35. Write an SQL query to fetch the list of employees with the same salary.
Ans.

The required query is:


### Query #35
RunShow Solution
```sql
SELECT distinct W.WORKER_ID, W.FIRST_NAME, W.Salary from Worker W, Worker W1 where W.Salary = W1.Salary and W.WORKER_ID != W1.WORKER_ID;
```
SQL query executed successfully!
Details
WORKER_ID	FIRST_NAME	SALARY
4	Amitabh	500000
5	Vivek	500000
### Q-36. Write an SQL query to show the second-highest salary from a table.
Ans.

The required query is:

### Query #36
RunShow Solution
```sql
SELECT max(Salary) from Worker where Salary not in (Select max(Salary) from Worker);
```
SQL query executed successfully!
Details
max(Salary)
300000
### Q-37. Write an SQL query to show one row twice in the results from a table.
Ans.


The required query is:

### Query #37
RunShow Solution
```sql
SELECT FIRST_NAME, DEPARTMENT from Worker W where W.DEPARTMENT='HR' union all select FIRST_NAME, DEPARTMENT from Worker W1 where W1.DEPARTMENT='HR';
```
SQL query executed successfully!
Details
FIRST_NAME	DEPARTMENT
Monika	HR
Vishal	HR
Monika	HR
Vishal	HR
### Q-38. Write an SQL query to fetch intersecting records of two tables.
Ans.

The required query is:

### Query #38
RunShow Solution
-- Note:
--       You Must Run ### Query #28
--       Both Tables Must Have Same Structure.

-- SQLite and MySQL compatible syntax
```sql
SELECT * FROM Worker
INTERSECT
SELECT * FROM WorkerClone;
```
-- SQLite and MySQL compatible syntax
```sql
SELECT w.*
FROM Worker w
INNER JOIN WorkerClone wc ON w.WORKER_ID = wc.WORKER_ID;
```
SQL query executed successfully!
Details
|WORKER_ID	|FIRST_NAME|	LAST_NAME|	SALARY|	JOINING_DATE|	DEPARTMENT|
|-----|-----|-----|-----|-----|-----|
1	Monika	Arora	100000	2021-02-20 09:00:00	HR
2	Niharika	Verma	80000	2021-06-11 09:00:00	Admin
3	Vishal	Singhal	300000	2021-02-20 09:00:00	HR
4	Amitabh	Singh	500000	2021-02-20 09:00:00	Admin
5	Vivek	Bhati	500000	2021-06-11 09:00:00	Admin
6	Vipul	Diwan	200000	2021-06-11 09:00:00	Account
7	Satish	Kumar	75000	2021-01-20 09:00:00	Account
8	Geetika	Chauhan	90000	2021-04-11 09:00:00	Admin

|WORKER_ID	|FIRST_NAME|	LAST_NAME|	SALARY|	JOINING_DATE|	DEPARTMENT|
|-----|-----|-----|-----|-----|-----|
1	Monika	Arora	100000	2021-02-20 09:00:00	HR
2	Niharika	Verma	80000	2021-06-11 09:00:00	Admin
3	Vishal	Singhal	300000	2021-02-20 09:00:00	HR
4	Amitabh	Singh	500000	2021-02-20 09:00:00	Admin
5	Vivek	Bhati	500000	2021-06-11 09:00:00	Admin
6	Vipul	Diwan	200000	2021-06-11 09:00:00	Account
7	Satish	Kumar	75000	2021-01-20 09:00:00	Account
8	Geetika	Chauhan	90000	2021-04-11 09:00:00	Admin
### Q-39. Write an SQL query to fetch the first 50% of records from a table.
Ans.

The required query is:

### Query #39
RunShow Solution
```sql
SELECT * FROM WORKER WHERE WORKER_ID <= (SELECT count(WORKER_ID)/2 from Worker);
```
SQL query executed successfully!
Details
|WORKER_ID	|FIRST_NAME|	LAST_NAME|	SALARY|	JOINING_DATE|	DEPARTMENT|
|-----|-----|-----|-----|-----|-----|
1	Monika	Arora	100000	2021-02-20 09:00:00	HR
2	Niharika	Verma	80000	2021-06-11 09:00:00	Admin
3	Vishal	Singhal	300000	2021-02-20 09:00:00	HR
4	Amitabh	Singh	500000	2021-02-20 09:00:00	Admin
Practicing SQL query interview questions is a great way to improve your understanding of the language and become more proficient in SQL. In addition to improving your technical skills, practicing SQL query questions can help you advance your career. Many employers seek candidates with strong SQL skills, so demonstrating your proficiency can get you a competitive edge.


### Q-40. Write an SQL query to fetch the departments that have less than five people in them.
Ans.

The required query is:

### Query #40
RunShow Solution
```sql
SELECT DEPARTMENT, COUNT(WORKER_ID) as 'Number of Workers' FROM Worker GROUP BY DEPARTMENT HAVING COUNT(WORKER_ID) < 5;
```
SQL query executed successfully!
Details
DEPARTMENT	Number of Workers
Account	2
Admin	4
HR	2
### Q-41. Write an SQL query to show all departments along with the number of people in there.
Ans.


The following query returns the expected result:

### Query #41
RunShow Solution
```sql
SELECT DEPARTMENT, COUNT(DEPARTMENT) as 'Number of Workers' FROM Worker GROUP BY DEPARTMENT;
```
SQL query executed successfully!
Details
DEPARTMENT	Number of Workers
Account	2
Admin	4
HR	2
### Q-42. Write an SQL query to show the last record from a table.
Ans.

The following query will return the last record from the Worker table:

### Query #42
RunShow Solution
```sql
Select * from Worker where WORKER_ID = (SELECT max(WORKER_ID) from Worker);
```
SQL query executed successfully!
Details
WORKER_ID	FIRST_NAME	LAST_NAME	SALARY	JOINING_DATE	DEPARTMENT
8	Geetika	Chauhan	90000	2021-04-11 09:00:00	Admin
### Q-43. Write an SQL query to fetch the first row of a table.
Ans.

The required query is:

### Query #43
RunShow Solution
```sql
Select * from Worker where WORKER_ID = (SELECT min(WORKER_ID) from Worker);
```
SQL query executed successfully!
Details
WORKER_ID	FIRST_NAME	LAST_NAME	SALARY	JOINING_DATE	DEPARTMENT
1	Monika	Arora	100000	2021-02-20 09:00:00	HR
### Q-44. Write an SQL query to fetch the last five records from a table.
Ans.

The required query is:

### Query #44
RunShow Solution
-- Solution 1
```sql
SELECT * FROM Worker WHERE WORKER_ID <= 5 UNION SELECT * FROM (SELECT * FROM Worker W ORDER BY W.WORKER_ID DESC) AS W1 WHERE W1.WORKER_ID <= 5;
```
-- Solution 2
```sql
SELECT * FROM Worker ORDER BY WORKER_ID DESC LIMIT 5;
```
SQL query executed successfully!


Details
|WORKER_ID	|FIRST_NAME|	LAST_NAME|	SALARY|	JOINING_DATE|	DEPARTMENT|
|-----|-----|-----|-----|-----|-----|
1	Monika	Arora	100000	2021-02-20 09:00:00	HR
2	Niharika	Verma	80000	2021-06-11 09:00:00	Admin
3	Vishal	Singhal	300000	2021-02-20 09:00:00	HR
4	Amitabh	Singh	500000	2021-02-20 09:00:00	Admin
5	Vivek	Bhati	500000	2021-06-11 09:00:00	Admin

|WORKER_ID	|FIRST_NAME|	LAST_NAME|	SALARY|	JOINING_DATE|	DEPARTMENT|
|-----|-----|-----|-----|-----|-----|
8	Geetika	Chauhan	90000	2021-04-11 09:00:00	Admin
7	Satish	Kumar	75000	2021-01-20 09:00:00	Account
6	Vipul	Diwan	200000	2021-06-11 09:00:00	Account
5	Vivek	Bhati	500000	2021-06-11 09:00:00	Admin
4	Amitabh	Singh	500000	2021-02-20 09:00:00	Admin
### Q-45. Write an SQL query to print the names of employees having the highest salary in each department.
Ans.

The required query is:

### Query #45
RunShow Solution
```sql
SELECT t.DEPARTMENT, t.FIRST_NAME, t.Salary from (SELECT max(Salary) as TotalSalary, DEPARTMENT from Worker group by DEPARTMENT) as TempNew Inner Join Worker t on TempNew.DEPARTMENT = t.DEPARTMENT and TempNew.TotalSalary = t.Salary;
```
SQL query executed successfully!
Details
DEPARTMENT	FIRST_NAME	SALARY
HR	Vishal	300000
Admin	Amitabh	500000
Admin	Vivek	500000
Account	Vipul	200000
### Q-46. Write an SQL query to fetch three max salaries from a table.
Ans.

The required query is:

### Query #46
RunShow Solution
```sql
SELECT distinct Salary from Worker a WHERE 3 >= (SELECT count(distinct Salary) from Worker b WHERE a.Salary <= b.Salary) order by a.Salary desc;
```
SQL query executed successfully!
Details
SALARY
500000
300000
200000


### Q-47. Write an SQL query to fetch three min salaries from a table.
Ans.

The required query is:

### Query #47
RunShow Solution
```sql
SELECT distinct Salary from Worker a WHERE 3 >= (SELECT count(distinct Salary) from Worker b WHERE a.Salary >= b.Salary) order by a.Salary desc;
```
SQL query executed successfully!
Details
SALARY
90000
80000
75000
### Q-48. Write an SQL query to fetch nth max salaries from a table.
Ans.

The required query is:

### Query #48
RunShow Solution
```sql
-- Set the value of n
WITH vars AS (SELECT 5 AS n)
-- Use the variable in a query
SELECT DISTINCT Salary FROM Worker a WHERE (SELECT n FROM vars) >= (SELECT COUNT(DISTINCT Salary) FROM Worker b WHERE a.Salary <= b.Salary) ORDER BY a.Salary DESC;
```
SQL query executed successfully!
Details
SALARY
500000
300000
200000
100000
90000
### Q-49. Write an SQL query to fetch departments along with the total salaries paid for each of them.
Ans.


The required query is:

### Query #49
RunShow Solution
```sql
SELECT DEPARTMENT, sum(Salary) from Worker group by DEPARTMENT;
```
SQL query executed successfully!
Details
DEPARTMENT	sum(Salary)
Account	275000
Admin	1170000
HR	400000
### Q-50. Write an SQL query to fetch the names of workers who earn the highest salary.
Ans.

The required query is:

### Query #50
RunShow Solution
```sql
SELECT FIRST_NAME, SALARY from Worker WHERE SALARY=(SELECT max(SALARY) from Worker);
```
SQL query executed successfully!
Details
FIRST_NAME	SALARY
Amitabh	500000
Vivek	500000


We have created three sample tables: Student Table, Program Table, and Scholarship Table. We will be using these tables to perform various query operations.

Student Table
STUDENT_ID

FIRST_NAME

LAST_NAME

GPA

ENROLLMENT_DATE

MAJOR

201

Shivansh

Mahajan

8.79

2021-09-01 09:30:00

Computer Science

202

Umesh

Sharma

8.44

2021-09-01 08:30:00

Mathematics

203

Rakesh

Kumar

5.60

2021-09-01 10:00:00

Biology

204

Radha

Sharma

9.20

2021-09-01 12:45:00

Chemistry

205

Kush

Kumar

7.85

2021-09-01 08:30:00

Physics

206

Prem

Chopra

9.56

2021-09-01 09:24:00

History

207

Pankaj

Vats

9.78

2021-09-01 02:30:00

English

208

Navleen

Kaur

7.00

2021-09-01 06:30:00

Mathematics

Program Table
STUDENT_REF_ID

PROGRAM_NAME

PROGRAM_START_DATE

201

Computer Science

2021-09-01 00:00:00

202

Mathematics

2021-09-01 00:00:00

208

Mathematics

2021-09-01 00:00:00

205

Physics

2021-09-01 00:00:00

204

Chemistry

2021-09-01 00:00:00

207

Psychology

2021-09-01 00:00:00

206

History

2021-09-01 00:00:00

203

Biology

2021-09-01 00:00:00

Scholarship Table
STUDENT_REF_ID

SCHOLARSHIP_AMOUNT

SCHOLARSHIP_DATE

201

5000

2021-10-15 00:00:00

202

4500

2022-08-18 00:00:00

203

3000

2022-01-25 00:00:00

201

4000

2021-10-15 00:00:00

Let us start by taking a look at some of the most asked SQL Query interview questions:

1. Write a SQL query to fetch “FIRST_NAME” from the Student table in upper case and use ALIAS name as STUDENT_NAME.
SELECT upper(FIRST_NAME) as STUDENT_NAME from Student;
Output:

SHIVANSH
UMESH
RAKESH
RADHA
KUSH
PREM
PANKAJ
NAVLEEN
2. Write a SQL query to fetch unique values of MAJOR Subjects from Student table.
SELECT DISTINCT MAJOR from STUDENT; 
or
SELECT MAJOR FROM STUDENT GROUP BY(MAJOR);
Output:

Computer Science
Mathematics
Biology
Chemistry
Physics
History
English
3. Write a SQL query to print the first 3 characters of FIRST_NAME from Student table.
SELECT SUBSTRING(FIRST_NAME, 1, 3)  FROM Student;
Output:

Shi
Ume
Rak
Rad
Kus
Pre
Pan
Nav
4. Write a SQL query to find the position of alphabet (‘a’) int the first name column ‘Shivansh’ from Student table.
SELECT INSTR(FIRST_NAME, 'a') FROM Student WHERE FIRST_NAME = 'Shivansh'; 
Output:

5
5. Write a SQL query that fetches the unique values of MAJOR Subjects from Student table and print its length.
SELECT MAJOR,LENGTH(MAJOR) FROM Student GROUP BY(MAJOR);                                                         
or                                                                                                                                                                                                                 
SELECT DISTINCT MAJOR, LENGTH(MAJOR) FROM Student;    
Output:

MAJOR

LENGTH(MAJOR)

Computer Science

16

Mathematics

11

Biology

7

Chemistry

9

Physics

7

History

7

English

7

6. Write a SQL query to print FIRST_NAME from the Student table after replacing ‘a’ with ‘A’.
SELECT REPLACE(FIRST_NAME, 'a', 'A') FROM Student;
Output:

ShivAnsh
Umesh
RAkesh
RAdhA
Kush
Prem
PAnkAj
NAvleen
7. Write a SQL query to print the FIRST_NAME and LAST_NAME from Student table into single column COMPLETE_NAME.
SELECT CONCAT(FIRST_NAME, ' ', LAST_NAME) AS COMPLETE_NAME FROM Student;
Output:

Shivansh Mahajan
Umesh Sharma
Rakesh Kumar
Radha Sharma
Kush Kumar
Prem Chopra
Pankaj Vats
Navleen Kaur
8. Write a SQL query to print all Student details from Student table order by FIRST_NAME Ascending and MAJOR Subject descending .
SELECT * FROM Student ORDER BY FIRST_NAME , MAJOR DESC;
Output:

STUDENT_ID

FIRST_NAME

LAST_NAME

GPA

ENROLLMENT_DATE

MAJOR

205

Kush

Kumar

7.85

2021-09-01 08:30:00

Physics

208

Navleen

Kaur

7

2021-09-01 06:30:00

Mathematics

207

Pankaj

Vats

9.78

2021-09-01 02:30:00

English

206

Prem

Chopra

9.56

2021-09-01 09:24:00

History

204

Radha

Sharma

9.2

2021-09-01 12:45:00

Chemistry

203

Rakesh

Kumar

5.6

2021-09-01 10:00:00

Biology

201

Shivansh

Mahajan

8.79

2021-09-01 09:30:00

Computer Science

202

Umesh

Sharma

8.44

2021-09-01 08:30:00

Mathematics

9. Write a SQL query to print details of the Students with the FIRST_NAME as ‘Prem’ and ‘Shivansh’ from Student table.
SELECT * from Student WHERE FIRST_NAME IN ('Prem' , 'Shivansh');
Output:

STUDENT_ID

FIRST_NAME

LAST_NAME

GPA

ENROLLMENT_DATE

MAJOR

201

Shivansh

Mahajan

8.79

2021-09-01 09:30:00

Computer Science

206

Prem

Chopra

9.56

2021-09-01 09:24:00

History

10. Write a SQL query to print details of the Students excluding FIRST_NAME as ‘Prem’ and ‘Shivansh’ from Student table.
SELECT * from Student WHERE FIRST_NAME NOT IN ('Prem', 'Shivansh');
Output:

STUDENT_ID

FIRST_NAME

LAST_NAME

GPA

ENROLLMENT_DATE

MAJOR

202

Umesh

Sharma

8.44

2021-09-01 08:30:00

Mathematics

203

Rakesh

Kumar

5.6

2021-09-01 10:00:00

Biology

204

Radha

Sharma

9.2

2021-09-01 12:45:00

Chemistry

205

Kush

Kumar

7.85

2021-09-01 08:30:00

Physics

207

Pankaj

Vats

9.78

2021-09-01 02:30:00

English

208

Navleen

Kaur

7

2021-09-01 06:30:00

Mathematics

11. Write a SQL query to print details of the Students whose FIRST_NAME ends with ‘a’.
SELECT * FROM Student WHERE FIRST_NAME LIKE '%a';
Output:

STUDENT_ID

FIRST_NAME

LAST_NAME

GPA

ENROLLMENT_DATE

MAJOR

204

Radha

Sharma

9.2

2021-09-01 12:45:00

Chemistry

12. Write an SQL query to print details of the Students whose FIRST_NAME ends with ‘a’ and contains six alphabets.
SELECT * FROM Student WHERE FIRST_NAME LIKE '_____a';
13. Write an SQL query to print details of the Students whose GPA lies between 9.00 and 9.99.
SELECT * FROM Student WHERE GPA BETWEEN 9.00 AND 9.99;
Output:

STUDENT_ID

FIRST_NAME

LAST_NAME

GPA

ENROLLMENT_DATE

MAJOR

204

Radha

Sharma

9.2

2021-09-01 12:45:00

Chemistry

206

Prem

Chopra

9.56

2021-09-01 09:24:00

History

207

Pankaj

Vats

9.78

2021-09-01 02:30:00

English

14. Write an SQL query to fetch the count of Students having Major Subject ‘Computer Science’.
SELECT Major, COUNT(*) as TOTAL_COUNT FROM Student WHERE MAJOR = 'Computer Science';
Output:

MAJOR

TOTAL_COUNT

Computer Science

1

15. Write an SQL query to fetch Students full names with GPA >= 8.5 and <= 9.5.
SELECT CONCAT(FIRST_NAME, ' ', LAST_NAME) AS FULL_NAME FROM Student WHERE GPA BETWEEN 8.5 and 9.5;
Output:

Shivansh Mahajan
Radha Sharma
16. Write an SQL query to fetch the no. of Students for each MAJOR subject in the descending order.
SELECT MAJOR, COUNT(MAJOR) from Student group by MAJOR order by COUNT(MAJOR) DESC;
Output:

MAJOR	COUNT(MAJOR)
Mathematics	2
Physics	1
History	1
English	1
Computer Science	1
Chemistry	1
Biology	1
17. Display the details of students who have received scholarships, including their names, scholarship amounts, and scholarship dates.
SELECT 
    Student.FIRST_NAME,
    Student.LAST_NAME,
    Scholarship.SCHOLARSHIP_AMOUNT,
    Scholarship.SCHOLARSHIP_DATE
FROM 
    Student
INNER JOIN 
    Scholarship ON Student.STUDENT_ID = Scholarship.STUDENT_REF_ID;
Output:

FIRST_NAME	LAST_NAME	SCHOLARSHIP_AMOUNT	SCHOLARSHIP_DATE
Shivansh	Mahajan	5000	2021-10-15 00:00:00
Umesh	Sharma	4500	2022-08-18 00:00:00
Rakesh	Kumar	3000	2022-01-25 00:00:00
Shivansh	Mahajan	4000	2021-10-15 00:00:00
18. Write an SQL query to show only odd rows from Student table.
SELECT * FROM Student WHERE student_id % 2 != 0;
Output:

STUDENT_ID

FIRST_NAME

LAST_NAME

GPA

ENROLLMENT_DATE

MAJOR

201	Shivansh	Mahajan	8.79	2021-09-01 09:30:00	Computer Science
203	Rakesh	Kumar	5.6	2021-09-01 10:00:00	Biology
205	Kush	Kumar	7.85	2021-09-01 08:30:00	Physics
207	Pankaj	Vats	9.78	2021-09-01 02:30:00	English
19. Write an SQL query to show only even rows from Student table.
SELECT * FROM Student WHERE student_id % 2 = 0;
Output:

STUDENT_ID

FIRST_NAME

LAST_NAME

GPA

ENROLLMENT_DATE

MAJOR

202	Umesh	Sharma	8.44	2021-09-01 08:30:00	Mathematics
204	Radha	Sharma	9.2	2021-09-01 12:45:00	Chemistry
206	Prem	Chopra	9.56	2021-09-01 09:24:00	History
208	Navleen	Kaur	7	2021-09-01 06:30:00	Mathematics
20. List all students and their scholarship amounts if they have received any. If a student has not received a scholarship, display NULL for the scholarship details.
SELECT 
    Student.FIRST_NAME,
    Student.LAST_NAME,
    Scholarship.SCHOLARSHIP_AMOUNT,
    Scholarship.SCHOLARSHIP_DATE
FROM 
    Student
LEFT JOIN 
    Scholarship ON Student.STUDENT_ID = Scholarship.STUDENT_REF_ID;
21. Write an SQL query to show the top n (say 5) records of Student table order by descending GPA.
SELECT * from Student ORDER BY GPA DESC LIMIT 5;
Output:

STUDENT_ID

FIRST_NAME

LAST_NAME

GPA

ENROLLMENT_DATE

MAJOR

207	Pankaj	Vats	9.78	2021-09-01 02:30:00	English
206	Prem	Chopra	9.56	2021-09-01 09:24:00	History
204	Radha	Sharma	9.2	2021-09-01 12:45:00	Chemistry
201	Shivansh	Mahajan	8.79	2021-09-01 09:30:00	Computer Science
202	Umesh	Sharma	8.44	2021-09-01 08:30:00	Mathematics
22. Write an SQL query to determine the nth (say n=5) highest GPA from a table.
SELECT * FROM Student ORDER BY GPA DESC LIMIT 5, 1;
Output:

STUDENT_ID

FIRST_NAME

LAST_NAME

GPA

ENROLLMENT_DATE

MAJOR

205	Kush	Kumar	7.85	2021-09-01 08:30:00	Physics
SQL Query Interview Questions and Answers

23. Write an SQL query to determine the 5th highest GPA without using LIMIT keyword.
SELECT * FROM Student s1 
WHERE 4 = (
    SELECT COUNT(DISTINCT (s2.GPA)) 
    FROM Student s2
    WHERE s2.GPA >= s1.GPA
);
Output:

STUDENT_ID

FIRST_NAME

LAST_NAME

GPA

ENROLLMENT_DATE

MAJOR

201	Shivansh	Mahajan	8.79	2021-09-01 09:30:00	Computer Science
24. Write an SQL query to fetch the list of Students with the same GPA.
SELECT s1.* FROM Student s1, Student s2 WHERE s1.GPA = s2.GPA AND s1.Student_id != s2.Student_id;
25. Write an SQL query to show the second highest GPA from a Student table using sub-query.
SELECT MAX(GPA) FROM Student
WHERE GPA NOT IN(SELECT MAX(GPA) FROM Student);
Output:

9.56
26. Write an SQL query to show one row twice in results from a table.
SELECT * FROM Student 
UNION ALL
SELECT * FROM Student ORDER BY STUDENT_ID;
27. Write an SQL query to list STUDENT_ID who does not get Scholarship.
SELECT STUDENT_ID FROM Student 
WHERE STUDENT_ID NOT IN (SELECT STUDENT_REF_ID FROM Scholarship);
Output:

204
205
206
207
208
28. Write an SQL query to fetch the first 50% records from a table.
SELECT * FROM Student WHERE STUDENT_ID <= (SELECT COUNT(STUDENT_ID)/2 FROM Student);
29. Write an SQL query to fetch the MAJOR subject that have less than 4 people in it.
SELECT MAJOR, COUNT(MAJOR) AS MAJOR_COUNT FROM Student GROUP BY MAJOR HAVING COUNT(MAJOR) < 4;
Output:

MAJOR	MAJOR_COUNT
Biology	1
Chemistry	1
Computer Science	1
English	1
History	1
Mathematics	2
Physics	1
30. Write an SQL query to show all MAJOR subject along with the number of people in there.
SELECT MAJOR, COUNT(MAJOR) AS ALL_MAJOR FROM Student GROUP BY MAJOR;
Output:

MAJOR	ALL_MAJOR
Biology	1
Chemistry	1
Computer Science	1
English	1
History	1
Mathematics	2
Physics	1
31. Write an SQL query to show the last record from a table.
SELECT * FROM Student WHERE STUDENT_ID = (SELECT MAX(STUDENT_ID) FROM STUDENT);
Output:

STUDENT_ID	FIRST_NAME	LAST_NAME	GPA	ENROLLMENT_DATE	MAJOR
208	Navleen	Kaur	7	2021-09-01 06:30:00	Mathematics
32. Write an SQL query to fetch the first row of a table.
SELECT * FROM Student WHERE STUDENT_ID = (SELECT MIN(STUDENT_ID) FROM Student);
Output:

STUDENT_ID	FIRST_NAME	LAST_NAME	GPA	ENROLLMENT_DATE	MAJOR
201	Shivansh	Mahajan	8.79	2021-09-01 09:30:00	Computer Science
33. Write an SQL query to fetch the last five records from a table.
SELECT * 
FROM (
    SELECT * 
    FROM Student 
    ORDER BY STUDENT_ID DESC 
    LIMIT 5
) AS subquery
ORDER BY STUDENT_ID;
Output:

STUDENT_ID	FIRST_NAME	LAST_NAME	GPA	ENROLLMENT_DATE	MAJOR
204	Radha	Sharma	9.2	2021-09-01 12:45:00	Chemistry
205	Kush	Kumar	7.85	2021-09-01 08:30:00	Physics
206	Prem	Chopra	9.56	2021-09-01 09:24:00	History
207	Pankaj	Vats	9.78	2021-09-01 02:30:00	English
208	Navleen	Kaur	7	2021-09-01 06:30:00	Mathematics
34. Write an SQL query to fetch three max GPA from a table using co-related subquery.
SELECT DISTINCT GPA FROM Student S1 
WHERE 3 >= (SELECT COUNT(DISTINCT GPA) FROM Student S2 WHERE S1.GPA <= S2.GPA) ORDER BY S1.GPA DESC;
Output:

9.78
9.56
9.2
35. Write an SQL query to fetch three min GPA from a table using co-related subquery.
SELECT DISTINCT GPA FROM Student S1 
WHERE 3 >= (SELECT COUNT(DISTINCT GPA) FROM Student S2 WHERE S1.GPA >= S2.GPA) ORDER BY S1.GPA;
Output:

5.6
7
7.85
36. Write an SQL query to fetch nth max GPA from a table.
SELECT DISTINCT GPA FROM Student S1 
WHERE n >= (SELECT COUNT(DISTINCT GPA) FROM Student S2 WHERE S1.GPA <= S2.GPA) ORDER BY S1.GPA DESC;
37. Write an SQL query to fetch MAJOR subjects along with the max GPA in each of these MAJOR subjects.
SELECT MAJOR, MAX(GPA) as MAXGPA FROM Student GROUP BY MAJOR;
Output:

MAJOR	MAXGPA
Biology	5.6
Chemistry	9.2
Computer Science	8.79
English	9.78
History	9.56
Mathematics	8.44
Physics	7.85
38. Write an SQL query to fetch the names of Students who has highest GPA.
SELECT FIRST_NAME, GPA FROM Student WHERE GPA = (SELECT MAX(GPA) FROM Student);
Output:

FIRST_NAME	GPA
Pankaj	9.78
39. Write an SQL query to show the current date and time.
Query to get current date : 
SELECT CURDATE();
Query to get current date and time : 
SELECT NOW();
40. Write a query to create a new table which consists of data and structure copied from the other table (say Student) or clone the table named Student.
CREATE TABLE CloneTable AS SELECT * FROM Student;
41. Write an SQL query to update the GPA of all the students in ‘Computer Science’ MAJOR subject to 7.5.
UPDATE Student SET GPA = 4.0 WHERE MAJOR = 'Computer Science';
42. Write an SQL query to find the average GPA for each major.
SELECT MAJOR, AVG(GPA) AS AVERAGE_GPA FROM Student GROUP BY MAJOR;
Output:

MAJOR	AVERAGE_GPA
Biology	5.6
Chemistry	9.2
Computer Science	4
English	9.78
History	9.56
Mathematics	7.72
Physics	7.85
43. Write an SQL query to show the top 3 students with the highest GPA.
SELECT * FROM Student ORDER BY GPA DESC LIMIT 3;
Output:

STUDENT_ID	FIRST_NAME	LAST_NAME	GPA	ENROLLMENT_DATE	MAJOR
207	Pankaj	Vats	9.78	2021-09-01 02:30:00	English
206	Prem	Chopra	9.56	2021-09-01 09:24:00	History
204	Radha	Sharma	9.2	2021-09-01 12:45:00	Chemistry
44. Write an SQL query to find the number of students in each major who have a GPA greater than 7.5.
SELECT MAJOR, COUNT(STUDENT_ID) AS HIGH_GPA_COUNT FROM Student WHERE GPA > 3.5 GROUP BY MAJOR;
Output:

MAJOR	HIGH_GPA_COUNT
Biology	1
Chemistry	1
Computer Science	1
English	1
History	1
Mathematics	2
Physics	1
45. Write an SQL query to find the students who have the same GPA as ‘Shivansh Mahajan’.
SELECT * FROM Student WHERE GPA = (SELECT GPA FROM Student WHERE FIRST_NAME = 'Shivansh' 
AND LAST_NAME = 'Mahajan');
Output:

STUDENT_ID	FIRST_NAME	LAST_NAME	GPA	ENROLLMENT_DATE	MAJOR
201	Shivansh	Mahajan	4	2021-09-01 09:30:00	Computer Science


Consider the below two tables for reference while trying to solve the SQL queries for practice.

Table – EmployeeDetails

EmpId	FullName	ManagerId	DateOfJoining	City
121	John Snow	321	01/31/2019	Toronto
321	Walter White	986	01/30/2020	California
421	Kuldeep Rana	876	27/11/2021	New Delhi

Table – EmployeeSalary

EmpId	Project	Salary	Variable
121	P1	8000	500
321	P2	10000	1000
421	P1	12000	0

For your convenience, I have compiled the top 10 questions for you. You can try solving these questions and click on the links to go to their respective answers.

SQL Query to fetch records that are present in one table but not in another table.
SQL query to fetch all the employees who are not working on any project.
SQL query to fetch all the Employees from EmployeeDetails who joined in the Year 2020.
Fetch all employees from EmployeeDetails who have a salary record in EmployeeSalary.
Write an SQL query to fetch a project-wise count of employees.
Fetch employee names and salaries even if the salary value is not present for the employee.
Write an SQL query to fetch all the Employees who are also managers.
Write an SQL query to fetch duplicate records from EmployeeDetails.
Write an SQL query to fetch only odd rows from the table.
Write a query to find the 3rd highest salary from a table without top or limit keyword.

Or, you can also jump to our below two sections on SQL query interview questions for freshers and experienced professionals.

Content
SQL Query Interview Questions for Freshers
SQL Query Interview Questions for Experienced
Scenario-based SQL Query Interview Questions
SQL Query Interview Questions for Freshers
SQL Query Interview Questions for freshers
Here is a list of top SQL query interview questions and answers for fresher candidates that will help them in their interviews. In these queries, we will focus on the basic SQL commands only.


1. Write an SQL query to fetch the EmpId and FullName of all the employees working under the Manager with id – ‘986’.
We can use the EmployeeDetails table to fetch the employee details with a where clause for the manager-

SELECT  EmpId, FullName
FROM EmployeeDetails
WHERE ManagerId = 986;


2. Write an SQL query to fetch the different projects available from the EmployeeSalary table.
While referring to the EmployeeSalary table, we can see that this table contains project values corresponding to each employee, or we can say that we will have duplicate project values while selecting Project values from this table.

So, we will use the distinct clause to get the unique values of the Project.

SELECT DISTINCT(Project)
FROM EmployeeSalary;


3. Write an SQL query to fetch the count of employees working in project ‘P1’.
Here, we would be using aggregate function count() with the SQL where clause-

SELECT COUNT(*) 
FROM EmployeeSalary 
WHERE Project = 'P1';


4. Write an SQL query to find the maximum, minimum, and average salary of the employees.
We can use the aggregate function of SQL to fetch the max, min, and average values-

SELECT Max(Salary), 
Min(Salary), 
AVG(Salary) 
FROM EmployeeSalary;


5. Write an SQL query to find the employee id whose salary lies in the range of 9000 and 15000.
Here, we can use the ‘Between’ operator with a where clause.

SELECT EmpId, Salary
FROM EmployeeSalary
WHERE Salary BETWEEN 9000 AND 15000;


6. Write an SQL query to fetch those employees who live in Toronto and work under the manager with ManagerId – 321.
Since we have to satisfy both the conditions – employees living in ‘Toronto’ and working in Project ‘P2’. So, we will use the AND operator here-

SELECT EmpId, City, ManagerId
FROM EmployeeDetails
WHERE City='Toronto' AND ManagerId='321';


7. Write an SQL query to fetch all the employees who either live in California or work under a manager with ManagerId – 321.
This interview question requires us to satisfy either of the conditions – employees living in ‘California’ and working under Manager with ManagerId – 321. So, we will use the OR operator here-

SELECT EmpId, City, ManagerId
FROM EmployeeDetails
WHERE City='California' OR ManagerId='321';


8. Write an SQL query to fetch all those employees who work on Projects other than P1.
Here, we can use the NOT operator to fetch the rows which are not satisfying the given condition.

SELECT EmpId
FROM EmployeeSalary
WHERE NOT Project='P1';

Or using the ‘not equal to’ operator-

SELECT EmpId
FROM EmployeeSalary
WHERE Project <> 'P1';
For the difference between NOT and <> SQL operators, check this link – Difference between the NOT and != operators.



9. Write an SQL query to display the total salary of each employee adding the Salary with Variable value.
Here, we can simply use the ‘+’ operator in SQL.

SELECT EmpId,
Salary+Variable as TotalSalary 
FROM EmployeeSalary;


10. Write an SQL query to fetch the employees whose name begins with any two characters, followed by a text “hn” and ends with any sequence of characters.
For this question, we can create an SQL query using like operator with ‘_’ and ‘%’ wild card characters, where ‘_’ matches a single character and ‘%’ matches ‘0 or multiple characters.

SELECT FullName
FROM EmployeeDetails
WHERE FullName LIKE ‘__hn%’;


11. Write an SQL query to fetch all the EmpIds which are present in either of the tables – ‘EmployeeDetails’ and ‘EmployeeSalary’.
In order to get unique employee ids from both tables, we can use the Union clause which can combine the results of the two SQL queries and return unique rows.

SELECT EmpId FROM EmployeeDetails
UNION 
SELECT EmpId FROM EmployeeSalary;


12. Write an SQL query to fetch common records between two tables.
SQL Server – Using INTERSECT operator-

SELECT * FROM EmployeeSalary
INTERSECT
SELECT * FROM ManagerSalary;

MySQL – Since MySQL doesn’t have INTERSECT operator so we can use the subquery-

SELECT *
FROM EmployeeSalary
WHERE EmpId IN 
(SELECT EmpId from ManagerSalary);


13. Write an SQL query to fetch records that are present in one table but not in another table.
SQL Server – Using MINUS- operator-

SELECT * FROM EmployeeSalary
MINUS
SELECT * FROM ManagerSalary;

MySQL – Since MySQL doesn’t have a MINUS operator so we can use LEFT join-

SELECT EmployeeSalary.*
FROM EmployeeSalary
LEFT JOIN
ManagerSalary USING (EmpId)
WHERE ManagerSalary.EmpId IS NULL;


14. Write an SQL query to fetch the EmpIds that are present in both the tables –  ‘EmployeeDetails’ and ‘EmployeeSalary.
Using subquery-

SELECT EmpId FROM 
EmployeeDetails 
where EmpId IN 
(SELECT EmpId FROM EmployeeSalary);


15. Write an SQL query to fetch the EmpIds that are present in EmployeeDetails but not in EmployeeSalary.
Using subquery-

SELECT EmpId FROM 
EmployeeDetails 
where EmpId Not IN 
(SELECT EmpId FROM EmployeeSalary);


16. Write an SQL query to fetch the employee’s full names and replace the space with ‘-’.
Using the ‘Replace’ function-

SELECT REPLACE(FullName, ' ', '-') 
FROM EmployeeDetails;


17. Write an SQL query to fetch the position of a given character(s) in a field.
Using the ‘Instr’ function-

SELECT INSTR(FullName, 'Snow')
FROM EmployeeDetails;


18. Write an SQL query to display both the EmpId and ManagerId together.
Here we can use the CONCAT command.

SELECT CONCAT(EmpId, ManagerId) as NewId
FROM EmployeeDetails;


19. Write a query to fetch only the first name(string before space) from the FullName column of the EmployeeDetails table.
In this question, we are required to first fetch the location of the space character in the FullName field and then extract the first name out of the FullName field.

For finding the location we will use the LOCATE method in MySQL and CHARINDEX in SQL SERVER and for fetching the string before space, we will use the SUBSTRING OR MID method.

MySQL – using MID

SELECT MID(FullName, 1, LOCATE(' ',FullName)) 
FROM EmployeeDetails;

SQL Server – using SUBSTRING

SELECT SUBSTRING(FullName, 1, CHARINDEX(' ',FullName)) 
FROM EmployeeDetails;


20. Write an SQL query to uppercase the name of the employee and lowercase the city values.
We can use SQL Upper and Lower functions to achieve the intended results.

SELECT UPPER(FullName), LOWER(City) 
FROM EmployeeDetails;


21. Write an SQL query to find the count of the total occurrences of a particular character – ‘n’ in the FullName field.
Here, we can use the ‘Length’ function. We can subtract the total length of the FullName field from the length of the FullName after replacing the character – ‘n’.

SELECT FullName, 
LENGTH(FullName) - LENGTH(REPLACE(FullName, 'n', ''))
FROM EmployeeDetails;


22. Write an SQL query to update the employee names by removing leading and trailing spaces.
Using the ‘Update’ command with the ‘LTRIM’ and ‘RTRIM’ functions.

UPDATE EmployeeDetails 
SET FullName = LTRIM(RTRIM(FullName));


23. Fetch all the employees who are not working on any project.
This is one of the very basic interview questions in which the interviewer wants to see if the person knows about the commonly used – Is NULL operator.

SELECT EmpId 
FROM EmployeeSalary 
WHERE Project IS NULL;


24. Write an SQL query to fetch employee names having a salary greater than or equal to 5000 and less than or equal to 10000.
Here, we will use BETWEEN in the ‘where’ clause to return the EmpId of the employees with salary satisfying the required criteria and then use it as a subquery to find the fullName of the employee from the EmployeeDetails table.

SELECT FullName 
FROM EmployeeDetails 
WHERE EmpId IN 
(SELECT EmpId FROM EmployeeSalary 
WHERE Salary BETWEEN 5000 AND 10000);


25. Write an SQL query to find the current date-time.
MySQL-

SELECT NOW();

SQL Server-

SELECT getdate();

Oracle-

SELECT SYSDATE FROM DUAL;


26. Write an SQL query to fetch all the Employee details from the EmployeeDetails table who joined in the Year 2020.
Using BETWEEN for the date range ’01-01-2020′ AND ’31-12-2020′-

SELECT * FROM EmployeeDetails
WHERE DateOfJoining BETWEEN '2020/01/01'
AND '2020/12/31';

Also, we can extract the year part from the joining date (using YEAR in MySQL)-

SELECT * FROM EmployeeDetails 
WHERE YEAR(DateOfJoining) = '2020';


27. Write an SQL query to fetch all employee records from the EmployeeDetails table who have a salary record in the EmployeeSalary table.
Using ‘Exists’-

SELECT * FROM EmployeeDetails E
WHERE EXISTS
(SELECT * FROM EmployeeSalary S 
WHERE  E.EmpId = S.EmpId);


28. Write an SQL query to fetch the project-wise count of employees sorted by project’s count in descending order.
The query has two requirements – first to fetch the project-wise count and then to sort the result by that count.

For project-wise count, we will be using the GROUP BY clause and for sorting, we will use the ORDER BY clause on the alias of the project count.

SELECT Project, count(EmpId) EmpProjectCount
FROM EmployeeSalary
GROUP BY Project
ORDER BY EmpProjectCount DESC;


29. Write a query to fetch employee names and salary records. Display the employee details even if the salary record is not present for the employee.
This is again one of the very common interview questions in which the interviewer just wants to check the basic knowledge of SQL JOINS.

Here, we can use the left join with the EmployeeDetail table on the left side of the EmployeeSalary table.

SELECT E.FullName, S.Salary 
FROM EmployeeDetails E 
LEFT JOIN 
EmployeeSalary S
ON E.EmpId = S.EmpId;


30. Write an SQL query to join 3 tables.
Considering 3 tables TableA, TableB, and TableC, we can use 2 joins clauses like below-

sql query interview questions
SELECT column1, column2
FROM TableA
JOIN TableB ON TableA.Column3 = TableB.Column3
JOIN TableC ON TableA.Column4 = TableC.Column4;
For more questions on SQL Joins, you can also check our top SQL Joins Interview Questions.
SQL Query Interview Questions for Experienced
SQL Query Interview Questions for experienced
Here is a list of some of the most frequently asked SQL query interview questions for experienced professionals. These questions cover SQL queries on advanced SQL JOIN concepts, fetching duplicate rows, odd and even rows, nth highest salary, etc.

31. Write an SQL query to fetch all the Employees who are also managers from the EmployeeDetails table.
Here, we have to use Self-Join as the requirement wants us to analyze the EmployeeDetails table as two tables. We will use different aliases ‘E’ and ‘M’ for the same EmployeeDetails table.

SELECT DISTINCT E.FullName
FROM EmployeeDetails E
INNER JOIN EmployeeDetails M
ON E.EmpID = M.ManagerID;


32. Write an SQL query to fetch duplicate records from EmployeeDetails (without considering the primary key – EmpId).
In order to find duplicate records from the table, we can use GROUP BY on all the fields and then use the HAVING clause to return only those fields whose count is greater than 1 i.e. the rows having duplicate records.

SELECT FullName, ManagerId, DateOfJoining, City, COUNT(*)
FROM EmployeeDetails
GROUP BY FullName, ManagerId, DateOfJoining, City
HAVING COUNT(*) > 1;


33. Write an SQL query to remove duplicates from a table without using a temporary table.
Here, we can use delete with alias and inner join. We will check for the equality of all the matching records and then remove the row with a higher EmpId.

DELETE E1 FROM EmployeeDetails E1
INNER JOIN EmployeeDetails E2 
WHERE E1.EmpId > E2.EmpId 
AND E1.FullName = E2.FullName 
AND E1.ManagerId = E2.ManagerId
AND E1.DateOfJoining = E2.DateOfJoining
AND E1.City = E2.City;


34. Write an SQL query to fetch only odd rows from the table.
In case we have an auto-increment field e.g. EmpId then we can simply use the below query-

SELECT * FROM EmployeeDetails 
WHERE MOD (EmpId, 2) <> 0;

In case we don’t have such a field then we can use the below queries.

Using Row_number in SQL server and checking that the remainder when divided by 2 is 1-

SELECT E.EmpId, E.Project, E.Salary
FROM (
    SELECT *, Row_Number() OVER(ORDER BY EmpId) AS RowNumber
    FROM EmployeeSalary
) E
WHERE E.RowNumber % 2 = 1;

Using a user-defined variable in MySQL-

SELECT *
FROM (
      SELECT *, @rowNumber := @rowNumber+ 1 rn
      FROM EmployeeSalary
      JOIN (SELECT @rowNumber:= 0) r
     ) t 
WHERE rn % 2 = 1;


35. Write an SQL query to fetch only even rows from the table.
In case we have an auto-increment field e.g. EmpId then we can simply use the below query-

SELECT * FROM EmployeeDetails 
WHERE MOD (EmpId, 2) = 0;

In case we don’t have such a field then we can use the below queries.

Using Row_number in SQL server and checking that the remainder, when divided by 2, is 1-

SELECT E.EmpId, E.Project, E.Salary
FROM (
    SELECT *, Row_Number() OVER(ORDER BY EmpId) AS RowNumber
    FROM EmployeeSalary
) E
WHERE E.RowNumber % 2 = 0;

Using a user-defined variable in MySQL-

SELECT *
FROM (
      SELECT *, @rowNumber := @rowNumber+ 1 rn
      FROM EmployeeSalary
      JOIN (SELECT @rowNumber:= 0) r
     ) t 
WHERE rn % 2 = 0;


36. Write an SQL query to create a new table with data and structure copied from another table.

CREATE TABLE NewTable 
SELECT * FROM EmployeeSalary;


37. Write an SQL query to create an empty table with the same structure as some other table.
Here, we can use the same query as above with the False ‘WHERE’ condition-

CREATE TABLE NewTable 
SELECT * FROM EmployeeSalary where 1=0;


38. Write an SQL query to fetch top n records.
In MySQL using LIMIT-

SELECT *
FROM EmployeeSalary
ORDER BY Salary DESC LIMIT N;

In SQL server using TOP command-

SELECT TOP N *
FROM EmployeeSalary
ORDER BY Salary DESC;


39. Write an SQL query to find the nth highest salary from a table.
Using Top keyword (SQL Server)-

SELECT TOP 1 Salary
FROM (
      SELECT DISTINCT TOP N Salary
      FROM Employee
      ORDER BY Salary DESC
      )
ORDER BY Salary ASC;

Using limit clause(MySQL)-

SELECT Salary
FROM Employee
ORDER BY Salary DESC LIMIT N-1,1;


40. Write SQL query to find the 3rd highest salary from a table without using the TOP/limit keyword.
This is one of the most commonly asked interview questions. For this, we will use a correlated subquery.

In order to find the 3rd highest salary, we will find the salary value until the inner query returns a count of 2 rows having a salary greater than other distinct salaries.

SELECT Salary
FROM EmployeeSalary Emp1
WHERE 2 = (
                SELECT COUNT( DISTINCT ( Emp2.Salary ) )
                FROM EmployeeSalary Emp2
                WHERE Emp2.Salary > Emp1.Salary
            )

For the nth highest salary-

SELECT Salary
FROM EmployeeSalary Emp1
WHERE N-1 = (
                SELECT COUNT( DISTINCT ( Emp2.Salary ) )
                FROM EmployeeSalary Emp2
                WHERE Emp2.Salary > Emp1.Salary
            )
Scenario-based SQL Query Interview Questions
Let’s see some interview questions based on different scenarios. The questions are of varying difficulty levels and the goal is to prepare you for different real-time scenario-based questions.

41. Consider a SalesData with columns SaleID, ProductID, RegionID, SaleAmount. Write a query to find the total sales amount for each product in each region.
The below query sums up SaleAmount for each combination of ProductID and RegionID, giving an insight into the total sales per product per region.

SELECT ProductID, RegionID, SUM(SaleAmount) AS TotalSales 
FROM SalesData 
GROUP BY ProductID, RegionID;


42. Write a query to find employees who earn more than their managers.
Here, we will write a query that joins the EmployeeDetails table with itself to compare the salaries of employees with their respective managers.

SELECT E.Name AS EmployeeName, 
M.Name AS ManagerName, 
E.Salary AS EmployeeSalary, 
M.Salary AS ManagerSalary 
FROM EmployeeDetails E JOIN EmployeeDetails M 
ON E.ManagerID = M.EmployeeID 
WHERE E.Salary > M.Salary;


43. Consider a BookCheckout table with columns – CheckoutID, MemberID, BookID, CheckoutDate, ReturnDate. Write an SQL query to find the number of books checked out by each member.

SELECT MemberID, COUNT(*) AS NumberOfBooksCheckedOut 
FROM BookCheckout 
GROUP BY MemberID;


44. Consider a StudentGrades table with columns – StudentID, CourseID, Grade. Write a query to find students who have scored an ‘A’ in more than three courses.
Here we will write an SQL query that filters students who have received an ‘A’ grade and groups them by StudentID, counting the number of ‘A’ grades per student.

SELECT StudentID FROM StudentGrades 
WHERE Grade = 'A' 
GROUP BY StudentID 
HAVING COUNT(*) > 3;


45. Consider a table OrderDetails with columns – OrderID, CustomerID, ProductID, OrderDate, Quantity, Price. Write a query to find the average order value for each customer.
The below query calculates the average order value (quantity multiplied by price) for each customer.

SELECT CustomerID, AVG(Quantity * Price) AS AvgOrderValue 
FROM OrderDetails 
GROUP BY CustomerID;


46. Consider a table PatientVisits with Columns VisitID, PatientID, DoctorID, VisitDate, Diagnosis. Write a query to find the latest visit date for each patient.

SELECT PatientID, MAX(VisitDate) AS LatestVisitDate 
FROM PatientVisits 
GROUP BY PatientID;


47. For a table FlightBookings with columns – BookingID, FlightID, PassengerID, BookingDate, TravelDate, Class, write a query to count the number of bookings for each flight class.
Here, we will write an SQL query that groups the bookings by Class and counts the number of bookings in each class.

SELECT Class, COUNT(*) AS NumberOfBookings 
FROM FlightBookings 
GROUP BY Class;


48. Consider a table FoodOrders with columns – OrderID, TableID, MenuItemID, OrderTime, Quantity. Write a query to find the most ordered menu item.
For the desired output, we will group the orders by MenuItemID and then sort the results by the count in descending order, fetching the top result.

SELECT MenuItemID 
FROM FoodOrders 
GROUP BY MenuItemID 
ORDER BY COUNT(*) DESC 
LIMIT 1;


49. Consider a table Transactions with columns – TransactionID, CustomerID, ProductID, TransactionDate, Amount. Write a query to find the total transaction amount for each month.
The below query sums the Amount for each month, giving a monthly total transaction amount.

SELECT MONTH(TransactionDate) AS Month, 
SUM(Amount) AS TotalAmount 
FROM Transactions 
GROUP BY MONTH(TransactionDate);


50. Consider a table EmployeeAttendance with columns – AttendanceID, EmployeeID, Date, Status. Write a query to find employees with more than 5 absences in a month.
This query filters the records for absent status, groups them by EmployeeID and month, and counts absences, filtering for more than 5 absences.

SELECT EmployeeID, 
MONTH(Date) AS Month, 
COUNT(*) AS Absences 
FROM EmployeeAttendance 
WHERE Status = 'Absent' 
GROUP BY EmployeeID, MONTH(Date) 
HAVING COUNT(*) > 5;


SQL Practice Exercises with Solutions | SQL Queries Practical Exercise

SQL Practice Exercises with Solutions :
In my previous article i have given the different examples of SQL as well as most important complex sql queries for interview purpose.I would like to combine all those examples and want to make one best article on SQL Practice Exercises with solutions.My main purpose writing this article on SQL Practice Exercises with solution is to get idea about different SQL real world examples as well as user can easily implement it in day to day life.These are the scenarios which are useful for real world industry. I have already written article on real world industry examples of SQL.I want to add some queries from that article also.There are following SQL Practice Exercises with Solutions which are mostly used in day to day life in world of programming.

Important Queries for SQL Practice Exercises with Solutions :
Example 1 : How to create table with same structure with data?
Query :

Let us consider that user wants to create a replica of table named ‘Student’.

Create table Student_Replica as Select * from Student;

Explanation :

The above query will create the same table as student named ‘Student_Replica’ with its data.

Example 2 : How to create table with same structure without data?
Query :

Let us consider that user wants to create a replica of table named ‘Student’ without having data.

Create table Student_Replica as Select * from Student where 1=2;

Explanation :

The above query will create the same table as student named ‘Student_Replica’ without data.It is possible due to the condition 1=2. The condition 1=2 means True=False which is always False condition.So with using the above query user can create duplicate table structure without data.

Example 3 : How to display Last 10 records from Student table.

Query :

There are some situations where user needs to fetch some last records from the table.The following query will fetch the last records from the table.

Select * from Student S where rownum <=10

union

select * from (Select * from Student S order by rowid desc) where rownum <=10;

Explanation :

Here we are using simple logic of union and order by the 10 records from student table.

Example 4 : How to fetch first 5 highest marks with Student table.

Query :

There are so many examples where user needs to fetch the highest values from the specified table.Following query will fetch the first 5 highest marks from student table.

select min(marks)from(select distinct marks from Student order by marks desc)where rownum<=5;

Explanation:

In above example we are using the rownum concept as well as we are using inner view of descending marks from student table.

Example 5: How to display 1 to 100 numbers with using query.

Query :

There are scenarios where user wants to display 1 to 100 numbers with using the query.

Select level from dual connect by level <=100;

Explanation:

In this example user needs to use the concept of hierarchical queries.With using the level attribute of hierarchical query user can display first 100 numbers.

Example 6 : How to find the duplicate row count from specific table.

Query :

This example is most important example for real world scenarios.There are so many times where user needs to find out the duplicate row count from the table.

 

Select Employee_no, count (Employee_no) from Employee

Group by Employee_no

Having count (Employee_no)>1

Order by count (Employee_no) desc;

Explanation :

In this example we need to use the Count function as well as group by and having. You need to use order by clause as well.

Example 7 : How to delete duplicate rows from the table.

Query :

Using above query we find out the duplicate record count from the table. There are situations where user needs to find out the duplicate rows as well as delete those rows. Following query is useful in that case.

Delete FROM Employee WHERE ROWID <>

(Select max (rowid) from Employee b where Employee_num=b.Employee_num);

Explanation :

Here we are using the <> operator from SQL to delete duplicate rows from the table.

Example 8 : How user can display following structure with using single SQL Query.

$

$$

$$$

Query :

We can not use dual table to perform this operation. We need to use Employee table with data more than 4 to perform this.


SELECT lpad (‘$’, ROWNUM,’$’) FROM Employee WHERE ROWNUM <4;

Explanation :

Here we are using lpad() function to fetch dollar symbol.


Example 9 :How to check for Email is correct or wrong with using single query.

Query :

User needs to use regular expression function to check the Email validation with single query.

SELECT
Email
FROM
Employee
where NOT REGEXP_LIKE(Email, ‘[A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,4}’, ‘i’);

Explanation :

These are above some SQL Practice Exercises with Solutions which are highly used in real life scenarios.In out SQL Practice Exercises with Solutions we are using the Regular expression function named REGEXP_LIKE to check for Email validation.

SQL Practice Exercises with Solutions

FOR ANY SQL SUPPORT CONTACT : COMPLEXSQL@GMAIL.COM
Example 10 : How to fetch maximum salary of Employee and minimum salary of Employee together from Employee table.

Query :

This is bit tricky question.We can not use the 2 aggregate functions together.

Select max (salary) from Employee

Union

Select min (salary) from Employee;

Explanation :

The example is pretty simple where user needs to use the Set operators from SQL.Here user needs to use union set operator.

Example 11 :  List the Students whose name starts with P and surname starts with S.

Query :

The Like operator will help to achieve this,

Select * from Students where name like ‘P%’ and surname like ‘S%’;

Explanation :

The SQL Like special character is most used wildcard to fetch data with specific condition in the table.

Example 12 :How to fetch last record from Student table.

Query :

This is also most common SQL Practice Exercises with Solutions where user needs to fetch the last record from the table,

Select * from Student where rowid = select max(rowid) from Student;

Explanation :

The records are stored in to table according to the rowid of the table. So User needs to fetch the maximum of row id record from Student table.

FOR ANY SQL SUPPORT CONTACT : COMPLEXSQL@GMAIL.COM
Example 13 : How to fetch all the Student who took admission at 2016.

Query :

There are so many scenarios where user needs to fetch the record according to admission year or joining date.

select * from Student where To_char(Joining_date,’YYYY’)=’2016′;

Explanation :

The above example uses the To_Char function to fetch the specific year from the date.

Example 14 : What is query to display odd records from Student table.

Query :

This query is also most important and most used SQL Practice Exercises with Solutions to display odd as well as display Even records from the specific table,

Select * from(Select rownum as rno,S.* from Student S) where Mod(rno,2)=1;

Explanation :

In this example user needs to use the Rownum as well as Mod functions to check out the odd records from the table.

Example 15 : What is query to display even records from Student table.

Query :

This query is also most important and most used SQL Practice Exercises with Solutions to display even as well as display odd records from the specific table,

Select * from(Select rownum as rno,S.* from Student S) where Mod(rno,2)=0;

Explanation :

In this example user needs to use the Rownum as well as Mod functions to check out the even records from the table.

Example 16 : How to find out manager name and employee name from same table.

Query :

This is scenario with self join in SQL.Following query will find out the Manager name with Employee name from Employee table,

Select e.employee_name,m.employee name from Employee e,Employee m where e.Employee_id=m.Manager_id;

Explanation :

In this query user is using the self join to fetch the records from the table.

SQL or Structured Query Language is a standard language for dealing with relational databases. With the humongous amount of data present, it is very important for us to understand how to use queries to retrieve the required data. In this article on SQL Query Interview Questions, I will discuss a few queries which you must practice to become a Database Administrator and will also help you ace your interviews.  

Top SQL Query Interview Questions

SQL Logo - SQL Query Interview Questions - Edureka

For, your better understanding, I will be considering the following tables to write queries.

EmployeeInfo Table:
EmpID

EmpFname

EmpLname

Department

Project

Address

DOB

Gender

1

Sanjay

Mehra

HR

P1

Hyderabad(HYD)

01/12/1976

M

2

Ananya

Mishra

Admin

P2

Delhi(DEL)

02/05/1968

F

3

Rohan

Diwan

Account

P3

Mumbai(BOM)

01/01/1980

M

4

Sonia

Kulkarni

HR

P1

Hyderabad(HYD)

02/05/1992

F

5

Ankit

Kapoor

Admin

P2

Delhi(DEL)

03/07/1994

M

EmployeePosition Table:
EmpID

EmpPosition

DateOfJoining

Salary

1

Manager

01/05/2024

500000

2

Executive

02/05/2024

75000

3

Manager

01/05/2024

90000

2

Lead

02/05/2024

85000

1

Executive

01/05/2024

300000

Let us start by taking a look at some of the most frequently asked SQL Query interview questions,   

Write a query to fetch the EmpFname from the EmployeeInfo table in the upper case and use the ALIAS name as EmpName.
Write a query to fetch the number of employees working in the department ‘HR’.
Write a query to get the current date.
Write a query to retrieve the first four characters of  EmpLname from the EmployeeInfo table.
Write a query to fetch only the place name(string before brackets) from the Address column of EmployeeInfo table.
Write a query to create a new table that consists of data and structure copied from the other table.
Write q query to find all the employees whose salary is between 50000 to 100000.
Write a query to find the names of employees that begin with ‘S’
Write a query to fetch top N records.
Write a query to retrieve the EmpFname and EmpLname in a single column as “FullName”. The first name and the last name must be separated with space.
Q1. Write a query to fetch the EmpFname from the EmployeeInfo table in upper case and use the ALIAS name as EmpName.
1
SELECT UPPER(EmpFname) AS EmpName FROM EmployeeInfo;
Q2. Write a query to fetch the number of employees working in the department ‘HR’.
1
SELECT COUNT(*) FROM EmployeeInfo WHERE Department = 'HR';
Q3. Write a query to get the current date.
You can write a query as follows in SQL Server:

Course Curriculum
Microsoft SQL Server Certification Training Course
1
SELECT GETDATE();
You can write a query as follows in MySQL:

1
SELECT SYSTDATE();
Q4. Write a query to retrieve the first four characters of  EmpLname from the EmployeeInfo table.
1
SELECT SUBSTRING(EmpLname, 1, 4) FROM EmployeeInfo;
Q5. Write a query to fetch only the place name(string before brackets) from the Address column of EmployeeInfo table.
Using the MID function in MySQL

1
SELECT MID(Address, 0, LOCATE('(',Address)) FROM EmployeeInfo;
Using SUBSTRING
1
SELECT SUBSTRING(Address, 1, CHARINDEX('(',Address)) FROM EmployeeInfo;
Q6. Write a query to create a new table which consists of data and structure copied from the other table.
Using the SELECT INTO command:

1
SELECT * INTO NewTable FROM EmployeeInfo WHERE 1 = 0;
Using the CREATE command in MySQL:

1
CREATE TABLE NewTable AS SELECT * FROM EmployeeInfo;
Q7. Write q query to find all the employees whose salary is between 50000 to 100000.
1
SELECT * FROM EmployeePosition WHERE Salary BETWEEN '50000' AND '100000';
Q8. Write a query to find the names of employees that begin with ‘S’
1
SELECT * FROM EmployeeInfo WHERE EmpFname LIKE 'S%';
 

Databases Training
Q9. Write a query to fetch top N records.
By using the TOP command in SQL Server:

1
SELECT TOP N * FROM EmployeePosition ORDER BY Salary DESC;
By using the LIMIT command in MySQL:

1
SELECT * FROM EmpPosition ORDER BY Salary DESC LIMIT N;
Q10. Write a query to retrieve the EmpFname and EmpLname in a single column as “FullName”. The first name and the last name must be separated with space.
1
SELECT CONCAT(EmpFname, ' ', EmpLname) AS 'FullName' FROM EmployeeInfo;
Q11. Write a query find number of employees whose DOB is between 02/05/1970 to 31/12/1975 and are grouped according to gender
1
SELECT COUNT(*), Gender FROM EmployeeInfo WHERE DOB BETWEEN '02/05/1970 ' AND '31/12/1975' GROUP BY Gender;
Q12. Write a query to fetch all the records from the EmployeeInfo table ordered by EmpLname in descending order and Department in the ascending order.
To order the records in ascending and descnding order, you have to use the ORDER BY statement in SQL.

1
SELECT * FROM EmployeeInfo ORDER BY EmpFname desc, Department asc;
Q13. Write a query to fetch details of employees whose EmpLname ends with an alphabet ‘A’ and contains five alphabets.
To fetch details mathcing a certain value, you have to use the LIKE operator in SQL.

1
SELECT * FROM EmployeeInfo WHERE EmpLname LIKE '____a';
Q14. Write a query to fetch details of all employees excluding the employees with first names, “Sanjay” and “Sonia” from the EmployeeInfo table.
1
SELECT * FROM EmployeeInfo WHERE EmpFname NOT IN ('Sanjay','Sonia');
Want to upskill yourself to get ahead in your career? Check out this video
 

Top 10 Trending Technologies to Learn in 2024 | Edureka

This video talks about the Top 10 Trending Technologies in 2024 that you must learn.
 

Q15. Write a query to fetch details of employees with the address as “DELHI(DEL)”.
1
SELECT * FROM EmployeeInfo WHERE Address LIKE 'DELHI(DEL)%';
Q16. Write a query to fetch all employees who also hold the managerial position.
1
2
3
SELECT E.EmpFname, E.EmpLname, P.EmpPosition 
FROM EmployeeInfo E INNER JOIN EmployeePosition P ON
E.EmpID = P.EmpID AND P.EmpPosition IN ('Manager');
Q17. Write a query to fetch the department-wise count of employees sorted by department’s count in ascending order.
1
2
3
SELECT Department, count(EmpID) AS EmpDeptCount 
FROM EmployeeInfo GROUP BY Department 
ORDER BY EmpDeptCount ASC;
Q18. Write a query to calculate the even and odd records from a table.
To retrieve the even records from a table, you have to use the MOD() function as follows:

1
SELECT EmpID FROM (SELECT rowno, EmpID from EmployeeInfo) WHERE MOD(rowno,2)=0;
Similarly, to retrieve the odd records from a table, you can write a query as follows:

1
SELECT EmpID FROM (SELECT rowno, EmpID from EmployeeInfo) WHERE MOD(rowno,2)=1;
Q19. Write a SQL query to retrieve employee details from EmployeeInfo table who have a date of joining in the EmployeePosition table.
1
2
3
SELECT * FROM EmployeeInfo E 
WHERE EXISTS 
(SELECT * FROM EmployeePosition P WHERE E.EmpId = P.EmpId);
Q20. Write a query to retrieve two minimum and maximum salaries from the EmployeePosition table.
To retrieve two minimum salaries, you can write a query as below:

1
2
3
SELECT DISTINCT Salary FROM EmployeePosition E1 
 WHERE 2 >= (SELECTCOUNT(DISTINCT Salary)FROM EmployeePosition E2 
  WHERE E1.Salary >= E2.Salary) ORDER BY E1.Salary DESC;
To retrieve two maximum salaries, you can write a query as below: 
1
2
3
SELECT DISTINCT Salary FROM EmployeePosition E1 
 WHERE 2 >= (SELECTCOUNT(DISTINCT Salary) FROM EmployeePosition E2 
  WHERE E1.Salary <= E2.Salary) ORDER BY E1.Salary DESC;

Q21. Write a query to find the Nth highest salary from the table without using TOP/limit keyword.
1
2
3
4
5
6
SELECT Salary 
FROM EmployeePosition E1 
WHERE N-1 = ( 
      SELECT COUNT( DISTINCT ( E2.Salary ) ) 
      FROM EmployeePosition E2 
      WHERE E2.Salary >  E1.Salary );
Q22. Write a query to retrieve duplicate records from a table.
1
2
3
SELECT EmpID, EmpFname, Department COUNT(*) 
FROM EmployeeInfo GROUP BY EmpID, EmpFname, Department 
HAVING COUNT(*) > 1;
Q23. Write a query to retrieve the list of employees working in the same department.
1
2
3
Select DISTINCT E.EmpID, E.EmpFname, E.Department 
FROM EmployeeInfo E, Employee E1 
WHERE E.Department = E1.Department AND E.EmpID != E1.EmpID;
Q24. Write a query to retrieve the last 3 records from the EmployeeInfo table.
1
2
3
4
SELECT * FROM EmployeeInfo WHERE
EmpID <=3 UNION SELECT * FROM
(SELECT * FROM EmployeeInfo E ORDER BY E.EmpID DESC) 
AS E1 WHERE E1.EmpID <=3;
Q25. Write a query to find the third-highest salary from the EmpPosition table.
1
2
3
4
5
6
SELECT TOP 1 salary
FROM(
SELECT TOP 3 salary
FROM employee_table
ORDER BY salary DESC) AS emp
ORDER BY salary ASC;
Q26. Write a query to display the first and the last record from the EmployeeInfo table.
To display the first record from the EmployeeInfo table, you can write a query as follows:

1
SELECT * FROM EmployeeInfo WHERE EmpID = (SELECT MIN(EmpID) FROM EmployeeInfo);
To display the last record from the EmployeeInfo table, you can write a query as follows:

1
SELECT * FROM EmployeeInfo WHERE EmpID = (SELECT MAX(EmpID) FROM EmployeeInfo);
Q27. Write a query to add email validation to your database
1
SELECT Email FROM EmployeeInfo WHERE NOT REGEXP_LIKE(Email, ‘[A-Z0-9._%+-]+@[A-Z0-9.-]+.[A-Z]{2,4}’, ‘i’);
Q28. Write a query to retrieve Departments who have less than 2 employees working in it.
1
SELECT DEPARTMENT, COUNT(EmpID) as 'EmpNo' FROM EmployeeInfo GROUP BY DEPARTMENT HAVING COUNT(EmpD) < 2;
Q29. Write a query to retrieve EmpPostion along with total salaries paid for each of them.
1
SELECT EmpPosition, SUM(Salary) from EmployeePosition GROUP BY EmpPosition;
Q30. Write a query to fetch 50% records from the EmployeeInfo table.
1
SELECT * FROM EmployeeInfo WHERE EmpID <= (SELECT COUNT(EmpID)/2 from EmployeeInfo);
 Intermediate scenario-based SQL Interview questions

Q1. How do you read the last five records from a database using a SQL query?
To retrieve the last five records from a database using a SQL query, you can use the ORDER BY clause combined with LIMIT. Here’s an example query:

SELECT * 

FROM your_table

ORDER BY id DESC

LIMIT 5;

Replace your_table_name with the name of your table and your_primary_key_column with the primary key column that defines the order of records. The ORDER BY your_primary_key_column DESC part sorts the records in descending order based on the primary key column, and LIMIT 5 limits the result to the last five records.

Q2. Write a SQL query that will provide you with the 10th-highest employee salary from an Employee table.
Here’s an example SQL query:

SELECT salary

FROM (

    SELECT salary, ROW_NUMBER() OVER (ORDER BY salary DESC) AS row_num

    FROM Employee

) AS ranked_salary

WHERE row_num = 10;

In this query:

The inner subquery SELECT salary, ROW_NUMBER() OVER (ORDER BY salary DESC) AS row_num FROM Employee calculates the row number for each record based on the descending order of salaries.
The outer query then selects the salary where the row number is 10, which gives you the 10th highest employee salary.
Q3. Write a query to get the last record from a table.
To get the last record from a table, you can use a query like this:

SELECT * FROM your_table_name ORDER BY your_primary_key_column DESC LIMIT 1;

Replace your_table_name with the name of your table and your_primary_key_column with the primary key column that defines the order of records. The DESC keyword sorts the records in descending order, and LIMIT 1 ensures you only get the last record.

Oracle Basic Interview Questions
Q1. How will you differentiate between varchar & varchar2
Q2. What are the components of logical database structure in Oracle database?


Q3. Describe an Oracle table
Q4. Explain the relationship among database, tablespace and data file?
Q5. What are the various Oracle database objects?
Q6. Explain about the ANALYZE command in Oracle?
Q7. What types of joins are used in writing subqueries?
Q8. RAW datatype in Oracle
Q9. What is the use of Aggregate functions in Oracle?
Q10. Explain Temporal data types in Oracle

Q1. How will you differentiate between Varchar & Varchar2?

Both Varchar & Varchar2 are the Oracle data types which are used to store character strings of variable length. To point out the major differences between these,

Varchar	Varchar2
Can store characters up to 2000 bytes

Can store characters up to 4000 bytes.

It will hold the space for characters defined during declaration even if all of them are not used

It will release the unused space

Q2. What are the components of logical database structure in Oracle database?

The components of the logical database structure in Oracle database are:

Tablespaces: A database mainly contains the Logical Storage Unit called tablespaces. This tablespace is a set of related logical structures. To be precise, tablespace groups are related to logical structures together.

Database schema objects: A schema is a collection of database objects owned by a specific user. The objects include tables, indexes, views, stored procedures, etc. And in Oracle, the user is the account and the schema is the object. It is also possible in the database platforms to have a schema without a user specified.

Q3. Describe an Oracle table

A table is a basic unit of data storage in the Oracle database. A table basically contains all the accessible information of a user in rows and columns.

To create a new table in the database, use the “CREATE TABLE” statement. First, you have to name that table and define its columns and datatype for each column.

CREATE TABLE table_name
(
column1 datatype [ NULL | NOT NULL ],
column2 datatype [ NULL | NOT NULL ],
…
column_n datatype [ NULL | NOT NULL ]
);

Here,

table_name: This specifies the name of the table that you want to create.
column..n: It specifies the number of columns which you want to add in the table. Here, every column must have a datatype and should either be defined as “NULL” or “NOT NULL”. If in case, the value is left blank, it is treated as “NULL” as default.
Q4. Explain the relationship among database, tablespace and data file?

An Oracle database possesses one or more logical storage units called tablespaces. Each tablespace in Oracle database consists of one or more files called the datafiles. These tablespaces collectively store the entire data of databases. Talking about the datafiles, these are the physical structure that confirms with the operating system as to which Oracle program is running.

Q5. What are the various Oracle database objects?

These are the Oracle Database Objects:

Tables: This is a set of elements organized in a vertical and horizontal manner.
Tablespaces: It is a logical storage unit in Oracle.
Views: Views are a virtual table derived from one or more tables.
Indexes: This is a performance tuning method to process the records.
Synonyms: It is a name for tables.

Q6. Explain about the ANALYZE command in Oracle?

This “Analyze” command is used to perform various functions on index, table, or cluster. The following list specifies the usage of ANALYZE command in Oracle:

Analyze command is used to identify migrated and chained rows of the table or a cluster.
It is used to validate the structure of an object.
This helps in collecting the statistics about the object used by the user and are then stored on to the data dictionary.
It also helps in deleting statistics that are used by an object from the data dictionary.
Q7. What types of joins are used in writing subqueries?

A Join is used to compare and combine, this means literally join and return specific rows of data from two or more tables in a database.

There are three types of joins in SQL that are used to write the subqueries.

Self Join: This is a join in which a table is joined with itself, especially when the table has a foreign key which references its own primary key.
Outer Join: An outer join helps to find and returns matching data and some dissimilar data from tables.
Equi-join: An equijoin is a join with a join condition containing an equality operator. An equijoin returns only the rows that have equivalent values for the specified columns.
Q8. RAW datatype in Oracle

The RAW datatype in Oracle is used to store variable-length binary data or byte string values. The maximum size for a raw in a given table in 32767 bytes.

You might get confused as to when to use RAW, varchar, and varchar2. Let me point out the major differences between them. PL/SQL does not recognize the data type and hence, it cannot have any conversions when RAW data is transferred to different systems. This data type can only be queried or can be inserted in a table.

Q9. What is the use of Aggregate functions in Oracle?

An aggregate function in Oracle is a function where values of multiple rows or records are joined together to get a single value output. It performs the summary operations on a set of values in order to provide a single value. There are several aggregate functions that you can use in your code to perform calculations.
Some common Aggregate functions are:

Average
Count
Sum
Q10. Explain Temporal data types in Oracle

Oracle mainly provides these following temporal data types:

Date Data Type: Different formats of Dates.
TimeStamp Data Type: Has different formats of Time Stamp.
Interval Data Type: Interval between dates and time.
Q11. What is a View?

A view is a logical table based on one or more tables or views. A View is also referred as a user-defined database object that is used to store the results of a SQL query, that can be referenced later in the course of time. Views do not store the data physically but as a virtual table, hence it can be referred as a logical table. The corresponding tables upon which the views are signified are called Base Tables and this doesn’t contain data.

Q12. How to store pictures on to the database?

It is possible to store pictures on to the database by using Long Raw Data type. This data type is used to store binary data of length 2GB. Although, the table can have only on Long Raw data type.

Q13. Where do you use DECODE and CASE Statements?

Both these statements Decode and Case will work similar to the if-then-else statement and also they are the alternatives for each of them. These functions are used in Oracle for data value transformation.

Example:

Decode function

Select OrderNum,
DECODE (Status,’O’, ‘Ordered’,’P’, ‘Packed,’ S’,’ Shipped’, ’A’,’Arrived’)
FROM Orders;

Case function

Select OrderNum
, Case(When Status=’O’ then ‘Ordered’
When Status =’P’ then Packed
When Status=’ S’ then ’Shipped’
else ’Arrived’) end
FROM Orders;

Course Curriculum
MySQL DBA Certification Training
Both these commands will display Order Numbers with their respective Statuses like this,

Status O= Ordered
Status P= Packed
Status S= Shipped
Status A= Arrived

Q14. What do you mean by Merge in Oracle and how can you merge two tables?

Merge statement is used to merge the data from two tables subsequently. It selects the data from the source table and then inserts/updates it in the other table based on the condition provided in the query. It is also useful in data warehousing applications. 

Q15. What is the data type of DUAL table?

The Dual table is basically a one-column table that is present in the Oracle database. This table has a single Varchar2(1) column called Dummy which has a value of ‘X’.

SQL Interview Questions
Q16. Explain about integrity constraint?

An integrity constraint is actually a declaration that is defined as a business rule for a table column. They are used to ensure accuracy and consistency of data in the database. It can also be called as a declarative way to define a business rule for a table’s column. There are a few types, namely:

Domain Integrity
Referential Integrity
Domain Integrity
Q17. What is SQL and also describe types of SQL statements?

SQL stands for Structured Query Language. SQL is used to communicate with the server in order to access, manipulate and control data. There are 5 different types of SQL statements available. They are:

Select: Data Retrieval
Insert, Update, Delete, Merge: Data Manipulation Language (DML)
Create, Alter, Drop, Rename, Truncate: Data Definition Language (DDL)
Commit, Rollback, Savepoint: Transaction Control Statements
Grant, Revoke: Data Control Language (DCL)
Q18. Briefly explain what is Literal? Give an example where it can be used?

A Literal is a string that contains a character, a number, or a date that is included in the Select list and which is not a column name or a column alias.

Also note that, Date and character literals must be enclosed within single quotes (‘ ‘), whereas you don’t have to do that for the number literals.

For example: Select last_name||’is a’||job_id As “emp details” from employee;

In this case, “is a” is literal.

Q19. How to display row numbers with the records?

In order to display row numbers along with their records numbers you can do this:

1
Select rownum <fieldnames> from table;
This above query will display the row numbers and the field values from the given table.

This query will display row numbers and the field values from the given table.

Q20. What is the difference between SQL and iSQL*Plus?

SQL

iSQL*Plus

It is a language

It is an environment

Character and date columns heading are left-justified and number column headings are right-justified

Default heading justification is in Centre

Cannot be Abbreviated (short forms)

Can be Abbreviated

Does not have a continuation character

Has a dash (-) as a continuation character if the command is longer than one line

Use Functions to perform some formatting

Use commands to format data

Q21. What are SQL functions? Describe in brief different types of SQL functions?

SQL Functions are a very powerful feature of SQL. These functions can take arguments but always return some value. There are two distinct types of SQL functions available. They are:

Single-Row functions: These functions operate on a single row to give one result per row.
Types of Single-Row functions are:

Character
Number
Date
Conversion
General
Multiple-Row functions: These functions operate on groups of rows to give one result per group of rows.
Types of Multiple-Row functions:

avg
count
max
min
sum
stddev
variance
Q22. Describe different types of General Function used in SQL?

General functions are of following types:

NVL: Converts a null value to an actual value. NVL (exp1, exp2) .If exp1 is null then NVL function return value of exp2.
NVL2: If exp1 is not null, nvl2 returns exp2, if exp1 is null, nvl2 returns exp3. The argument exp1 can have any data type. NVL2 (exp1, exp2, exp3)
NULLIF: Compares two expressions and returns null if they are equal or the first expression if they are not equal. NULLIF (exp1, exp2)
COALESCE: Returns the first non-null expression in the expression list. COALESCE (exp1, exp2… expn). The advantage of the COALESCE function over NVL function is that the COALESCE function can take multiple alternative values.
Conditional Expressions: Provide the use of IF-THEN-ELSE logic within a SQL statement. Example: CASE Expression and DECODE Function.
Q23. What is a Sub Query? Describe its Types?

A subquery is a SELECT statement that is embedded in a clause of another SELECT statement. A subquery can be placed in where having and from clause.

Guidelines for using subqueries:

You should enclose the sub-queries within parenthesis.
Place these subqueries on the right side of the comparison condition.
Use Single-row operators with single-row subqueries.
Use Multiple-row operators with multiple-row subqueries.
Types of subqueries:

Single-Row Subquery: Queries that return only one row from the inner select statement. Single-row comparison operators are: =, >, >=, <, <=, <>
Multiple-Row Subquery: These are queries that return more than one row from the inner Select statement. You will also find multiple-column subqueries that return more than one column from the inner select statement. Operators include: IN, ANY, ALL.
Q24. What is the use of Double Ampersand (&&) in SQL Queries? Give an example

You can use && if you want to reuse the variable value without prompting the user each time.

For example: Select empno, ename, &&column_name from employee order by &column_name;

Q25. Describe VArray

VArray is basically an Oracle data type used to have columns containing multivalued attributes and it can hold a bounded array of values. All Varrays consist of contiguous memory locations. The lowest address corresponds to the first element and the highest address to the last element.

varrays-Oracle Interview Questions-Edureka

Each element in a Varray has an index associated with it. It has a maximum size (max_size) that can be changed dynamically.

Q26. What are the attributes of the Cursor?

Each Cursor in Oracle has a set of attributes that enables an application program to test the state of the Cursor. The attributes can be used to check whether the cursor is opened or closed, found or not found and also find row count.

Q27. Name the various constraints used in Oracle

These are the following constraints used:

NULL: It is to indicate that a particular column can contain NULL values.
NOT NULL: It is to indicate that particular column cannot contain NULL values.
CHECK: Validate that values in the given column to meet the specific criteria.
DEFAULT: It is to indicate the value is assigned to a default value.
Q28. What is the fastest query method to fetch data from the table?

The fastest query method to fetch data from the table is by using the Row ID. A row can be fetched from a table by using RowID.

Q29. Difference between Cartesian Join and Cross Join?

Databases Training
There are no such differences between these Joins. Cartesian and Cross join are the same.

Cross join gives a cartesian product of two tables i.e., the rows from the first table is multiplied with another table that is called cartesian product.

Cross join without the where clause gives a Cartesian product.

Q30. How does the ON-DELETE-CASCADE statement work?

Using this On Delete Cascade you can automatically delete a record in the child table when the same record is deleted from the parent table. This statement can be used with Foreign Keys as well.

You can add this On Delete Cascade option on an existing table.

Syntax:

Alter Table Child_T1 ADD Constraint Child_Parent_FK References
Parent_T1(Column1) ON DELETE CASCADE;

Now let’s move on to the next part of this Oracle Interview Questions article.

Oracle PL/SQL Interview Questions
Q31. What is PL SQL?

PL/SQL is an extension of Structured Query Language (SQL) that is used in Oracle. It combines the data manipulation power of SQL with the processing power of procedural language in order to create super-powerful SQL queries. PL SQL means instructing the compiler what to do through SQL and how to do it through its procedural way.

Q32. Enlist the characteristics of PL/SQL?

There are a lot of characteristics of PL/SQL. Some notable ones among them are:

PL/SQL is a block-structured language.
It is portable to all environments that support Oracle.
PL/SQL is integrated with the Oracle data dictionary.
Stored procedures help better sharing of application.
Q33. What are the data types available in PL/SQL?

There are two data types available in PL/SQL. They are namely:

Scalar data types
Example: Char, Varchar, Boolean, etc.

Composite datatypes
Example: Record, table etc.

Q34. What are the uses of a database trigger

Triggers are the programs which are automatically executed when some events occur:

Implement complex security authorizations.
Drive column values.
Maintain duplicate tables.
Implement complex business rules.
Bring transparency in log events. 
Q35. Show how functions and procedures are called in a PL SQL block

A Procedure can have a return statement to return the control to the calling block, but, it cannot return any values through the return statement. They cannot be called directly from Select statements but they can be called from another block or through EXEC keyword.

The procedure can be called in the following ways:
a) CALL <procedure name> direc
b) EXCECUTE <procedure name> from calling environment
c) <Procedure name> from other procedures or functions or packages

Functions can be called in the following ways
a) Execute<Function name> from calling environment. Always use a variable to get the return value.
b) As part of an SQL/PL SQL Expression

Q36. What are the two virtual tables available at the time of database trigger execution?

Columns are referred as Then.column_name and Now.column_name.

INSERT related triggers, Now.column_name values are available only.
DELETE related triggers, Then.column_name values are available only.
UPDATE related triggers, both Table columns are available.
Q37. What are the differences between Primary Key and Unique Key?

Unique key

Primary key

A table can have more than one Unique Key

 A table can have only one Primary Key

A unique key column can store NULL values

A primary key column cannot store NULL values

Uniquely identify each value in a column

Uniquely identify each row in a table

Q38. Explain the purpose of %TYPE and %ROWTYPE data types with the example?

%ROWTYPE and %TYPE are the attributes in PL/SQL which can inherit the datatypes of a table that are defined in a database. The main purpose of using these attributes in Oracle is to provide data independence and integrity. Also note that, if any of the datatypes gets changed in the database, PL/SQL code gets updated automatically including the change in the datatypes.

%TYPE: This is used for declaring a variable that needs to have the same data type as of a table column.
%ROWTYPE: This is used to define a complete row of record having a structure similar to the structure of a table.

Q39. Explain the difference between Triggers and Constraints?

Triggers are very different from Constraints in the following ways:

Triggers	Constraints
Only affect those rows added after the trigger is enabled	Affect all rows of the table including that already exist when the constraint is enabled
Triggers are used to implement complex business rules which cannot be implemented using integrity constraints	Constraints maintain the integrity of the database
Q40. Exception handling in PL/SQL

When an error occurs in PL/SQL, the corresponding exception is raised. This also means, to handle undesired situations where PL/SQL scripts gets terminated unexpectedly, error-handling code is included in the program. In PL/SQL, all exception handling code is placed in the Exception section.

There are 3 types of Exceptions:

Predefined Exceptions: Common errors with predefined names.
Undefined Exceptions: Less common errors with no predefined names.
User-defined Exceptions: Do not cause runtime error but violate business rules.
Comparison based Interview Questions 
Q41. What is the difference between COUNT (*), COUNT (expression), COUNT (distinct expression)?

COUNT (*): This returns a number of rows in a table including the duplicates rows and the rows containing null values in the columns.
COUNT (EXP): This returns the number of non-null values in the column identified by an expression.
COUNT (DISTINCT EXP): It returns the number of unique, non-null values in the column identified by an expression.

Q42. Difference between the “VERIFY” and “FEEDBACK” command?

The major differences between Verify and Feedback commands are:

Verify Command: You can use this command to confirm the changes in the SQL statement which can have old and new values that are defined with Set Verify On/OFF.
Feedback Command: It displays the number of records that are returned by a query.

Q43. List out the difference between Commit, Rollback, and Savepoint?

The major differences between these are listed below:

Commit: This ends the current transaction by ensuring that all pending data changes are made permanent.
Rollback: This ends the current transaction by discarding or deleting all pending data changes.
Savepoint: It divides a transaction into smaller parts. You can rollback the transaction until you find a particular named savepoint.
Q44. What is the difference between SUBSTR and INSTR?

SUBSTR returns a specific portion of a string whereas INSTR provides the character position in which a pattern is found in a string. SUBSTR returns string whereas INSTR returns numeric values.

Q45. Point out the difference between USER TABLES and DATA DICTIONARY?

Course Curriculum
MySQL DBA Certification Training
Weekday / Weekend Batches
User Tables: This is a collection of tables created and maintained by the user. It also contains user information.
Data dictionary: This is a collection of tables that are created and maintained by the Oracle Server. It contains database information. All data dictionary tables are owned by the SYS user.

Q46. Major difference between Truncate and Delete?

Truncate

Delete

Removes all rows from a table and releases storage space used by that table

Removes all rows from a table but does not release storage space used by that table

This command is faster

This command is slower

It is a DDL statement and cannot be Rollback

It is a DDL statement and can be Rollback

Database Triggers do not fire on TRUNCATE

Database Triggers fire on DELETE

Q47. Point the difference between TRANSLATE and REPLACE?

Translate is used for character by character substitution whereas Replace is used to substitute a single character with a word.

Q48. What is the difference between $ORACLE_BASE and $ORACLE_HOME?

$Oracle_base is the main or root directory of Oracle whereas Oracle_Home is located beneath the base folder in which all Oracle products reside.

Q49. What do you understand by Redo Log file mirroring?

Mirroring is a process of having a copy of Redo log files. This is done by creating a group of log files altogether. It ensures that the LGWR automatically writes it to all the members of the current on-line redo log group. If the group fails, the database automatically switches over to the next group and it diminishes the performance of the database.

Q50. What is the difference between a hot backup and a cold backup in Oracle? Explain about their benefits as well

Hot backup (Online Backup): A hot backup is also known as an online backup because it is done while the database is active. Some sites can’t shut down their database while making a backup copy and they are used 24*7.
Cold backup (Offline Backup): A cold backup is also known as an offline backup because it is done while the database has been shut down using the SHUTDOWN command. If the database is suddenly shutdown with an uncertain condition, it should be restarted with RESTRICT mode and then shutdown with the NORMAL option. For a complete cold backup, the corresponding files must be backed up i.e., all datafiles, All control files, All online redo log files and the init.ora file (you can recreate it manually).


1.Query to find Second Highest Salary of Employee?(Most important question in 20 SQL Queries for interview)

Answer:-
Select distinct Salary from Employee e1 where 2=Select count(distinct Salary) from Employee e2 where e1.salary<=e2.salary;

2.Query to find duplicate rows in table?(click here for explaination)

Answer :-
Select * from Employee a where row_id != select max(row_id) for Employee b where a.Employee_num=b.Employee_num;

3.How to fetch  monthly Salary of Employee if annual salary is given?(click here for Explaination)

Answer:-
   Select Employee_name,Salary/12 as ‘Monthly Salary’ from employee;

Click here to get information on ROW_ID

4.What is the Query to fetch first record from Employee table?

Answer:-
 Select * from Employee where Rownum =1;

Click here to get What is Rownum?

5.What is the Query to fetch last record from the table?

Answer:-
Select * from Employee where Rowid= select max(Rowid) from Employee;

20 SQL Queries for interview
Complex SQL Queries
6.What is Query to display first 5 Records from Employee table?

Answer:
Select * from Employee where Rownum <= 5;

6.What is Query to display last 5 Records from Employee table?

Answer:
Select * from Employee e where rownum <=5

union

select * from (Select * from Employee e order by rowid desc) where rownum <=5;


Click Here to get What is Union?

7.What is Query to display Nth Record from Employee table?

Select * from Employee  where rownum = &n;

For Any issues contact :complexsql@gmail.com
8.How to get 3 Highest salaries records from Employee table?

select distinct salary from employee a where 3 >= (select count(distinct salary) from emp loyee b where a.salary <= b.salary) order by a.salary desc;

9.How to Display Odd rows in Employee table?

Select * from(Select rownum as rno,E.* from Employee E) where Mod(rno,2)=1;

10.How to Display Even rows in Employee table?

Select * from(Select rownum as rno,E.* from Employee) where Mod(rno,2)=0;

11.How to fetch 3rd highest salary using Rank Function?


select * from (Select Dense_Rank() over ( order by  salary desc) as Rnk,E.* from Employee E) where Rnk=3;

Click Here to Get Information on Rank and Dense_Rank

12.How Can i create table with same structure of Employee table?

Create table Employee_1 as Select * from Employee where 1=2;

13.Display first 50% records from Employee table?

Select rownum,E.* from Employee E where rownum<=(Select count(*/2) from Employee);

14.Display last 50% records from Employee table?

Select rownum,E.* from Employee E

minus

Select rownum,E.* from Employee E where rownum<=(Select count(*/2) from Employee);

15.How Can i create table with same structure with data of Employee table?

Create table Employee1 as select * from Employee;

16.How do i fetch only common records between 2 tables.


Select * from Employee;

Intersect

Select * from Employee1;

For Any issues contact :complexsql@gmail.com
CLICK HERE TO GET INFORMATION ABOUT INTERSECT OPERATOR

17.Find Query to get information of Employee where Employee is not assigned to the department.

Select * from Employee where Dept_no Not in(Select Department_no from Employee);

18.How to get distinct records from the table without using distinct keyword.

select * from Employee a where  rowid = (select max(rowid) from Employee b where  a.Employee_no=b.Employee_no);

19.Select all records from Employee table whose name is ‘Amit’ and ‘Pradnya’

Select * from Employee where Name in(‘Amit’,’Pradnya’);

20.Select all records from Employee table where name not in ‘Amit’ and ‘Pradnya’

select * from Employee where name Not  in (‘Amit’,’Pradnya’);


1.What is SQL?[100 % asked  Latest SQL Interview Questions for freshers ]

Answer: 

SQL Stands for Structured Query Language which is specially designed to communicate with databases.SQL pronounced as Sequel is very widely used language in most of the database management systems like Oracle,MySQL,PostgreSQL etc.SQL provides us  a simple and efficient way of reading,writing,executing the data from the system.this is one of the SQL Interview Question ever asked in interviews

2.What is the use of NVL function in Oracle?[80% asked SQL Interview Question ]

Answer:

NVL function is most important function to replace null value with another value.

Example: select NVL(null,'Amit') from dual; 
which will give you output as Amit.
3.What is Unique Key? [  90% asked SQL Interview Questions for freshers ]

Answer:

Unique key is nothing but the columns which are uniquely identifies the values.There are more than one unique keys for each table.The Entry of Null value is allowed in Unique key.Oracle does not permit you to create primary key and unique key on same column.

Syntax: 
Create table Table_name
(Column_name1 Datatype[null/not null],
 Column_name Datatype[null/not null].......
Constraint constraint_name Unique(uc_col1,uc_col2..));
4.What is difference between Unique Key Constraint and Primary Key Constraint?[80% asked SQL Interview Questions for freshers]

Answer:

Primary Key constraint:

1.Primary key will not accept the null values in the table column.

2.Primary is  basically used to identify the unique records in the table.

3.We have only one primary key per table.

Unique Key Constraint:

1.Unique key accepts the null values in the table.

2.The main task of unique key is it is used to remove duplicate values from the table with exception of null entry.

3.We will have more than 1 unique keys on a single table.

SQL Interview Questions
SQL Interview Questions for freshers
5.What is difference between varchar and varchar2 datatype?

Answer:

 As an example ,Varchar can store up to 2000 bytes and varchar2 can store up to 4000 bytes of memory space.Varchar will occupy the space for null values whereas varchar2 can not occupy the space for null values.So varchar2 is good to use not to  face performace related problems.varchar2 is faster than varchar datatype.

6.How to represent comments in oracle?

Answer:

There are following 2 ways for commenting in oracle:

1.Single Line comment: Two dashes (–) before begining of the line


2.Multiline comment/Block comment:When user wants to comment multiple line /* */ operators are used.

7.What is raw datatype?[90% asked in SQL Interview Questions]

Answer:

The example for the same is below , Raw datatype is used to store values in binary data format.There are 2 types of RAW datatype.1.Raw 2.Long Raw. Long raw datatype is used to store graphics,sound documents.Raw datatype is variable length datatype like varchar2 but basically it only stores  data in 1 ‘s and 0’s means binary data format.

8.What is ROWID & ROWNUM?(90 % asked in SQL Interview Question)
Answer:

ROWID is nothing but the physical address given to that row which is in hexadecimal format.ROWNUM is nothing but the logical sequence given to the row of that column.

[click here for detailed description]

9.What are views in SQL?Explain types of Views in SQL?(Asked in almost every SQL Interview Questions)

Answer:

Views:

Views are nothing but the logical structure of the table where we can fetch the data from different tables or same table.

There are 2 types of views in Oracle:

1.Simple View:Simple view has been created on only a single table.

2.Complex view:Views which are created using more than 1 table which has joins clauses are known as complex views.

[Click here to get more information on views]

10.What is Materialized View in SQL?

Answer :

Materialized view is also logical structure of one or more table in which data is stored physically in the view.Data has been stored physically in materialized view so data retrieval is faster as compare to simple view.


[Click here to get more information on materialized view]

11.Why to use SQL? [90% asked SQL Interview Questions ]

Answer:

SQL is structured query language which is used for manipulation of data.There are following reasons why to use SQL:

Allows users to access data in relational database management systems.

Allows users to define the data in database and manipulate that data.

Allows users to create and drop databases and tables.

Allows users to create view, stored procedure, functions in a database.

Allows users to set permissions on tables, procedures, and views.

12.What is difference between Truncate ,Drop and DELETE?

Answer:


1.Drop:

1.Drop command is DDL command which is used to delete the object from the database.

2.We can not use the “ROLLBACK” after using drop command.

3.Drop command free’s the space of database object.

4.Drop table table_name;

2.Truncate:

1.Truncate command is DDL command which is used to truncate the data from the database table.

2.We can not use the “ROLLBACK” after using Truncate command.

3.It free’s the space of database object but the structure remains same and memory of structure also remains same.

4.Truncate table table_name;

3.Delete:

1.Delete command is DML command which is used to delete the records from table.

2.We can use Rollback to Rollback the records from the table.

3.Delete command not free’s the memory space.

4.Delete table table_name where condition;

13.Explain About DDL Statements of SQL?

DDL – DDL stands for Data Definition Language:

Statement 	Description
CREATE	Creates a new table, a view of a table, or other object in database
ALTER	Modifies an existing database object, such as a table.
DROP	Deletes an entire table, a view of a table or other object in the database.
‘10 Most important SQL Interview Questions for Fresher in PPT
14.What is DML in SQL.Explain DML Statements in Details?

Answer:

DML stands for Data Manipulation Language:

Statement	Description
INSERT	Creates a record
UPDATE	Modifies records
DELETE	Deletes records
15.What is Database?[90% asked SQL Interview Questions]

Answer:

It is a collection of Inter-Related data. Records the data in HDD (Permanent Memory).
Inter-Related data means relation among data values
Objective of DB is to record data & save it for future use.
16.What is RDBMS?

Answer:

RDBMS stands for Relational DataBase Management System. RDBMS is the basis for SQL, and for all modern database systems like MS SQL Server, IBM DB2, Oracle, MySQL, and Microsoft Access.

A Relational database management system (RDBMS) is a database management system (DBMS) that is based on the relational model as introduced by E. F. Codd.

17. What are tables and Fields?

Answer:

A table is set of data which is organized in to specific structured manner.Table is made up of combination of columns and rows.A table has specified number of column called fields but can have any number of rows which is called record.

Example:Table

Name(Field 1)	Salary(Field 2)
Amit S(Record1)	10000(Record1)
18.Explain me about SQL joins?

Answer:

CLICK HERE TO GET ANSWER IN DETAILS

Join is nothing but connecting 2 tables to fetch the records from 2 or more different tables.There are following types of joins in SQL:

1.Inner join:

Inner join retreives the records which are common between 2 or more tables.

2.Outer join:

Outer join retrieves the common records from the table as well as uncommon records from Left or right table.

2.1.Left outer join:

When user needs to fetch all data from left table and common records from left and right table then the join is called as left outer join.

2.2.Right outer join:

When user needs to fetch all data from right table and common records from left and right table then the join is called as right outer join.

2.3.Full Outer Join:

When user needs to fetch the data from both the tables and common records from both of the tables.

3.Cross join/Cartesian join:

When each and every record is connected to each and every record from other table then it is called as cross join or Cartesian join.

19.What is Views in SQL?(Asked in almost every SQL Interview Questions)

Answer:

View is nothing but the virtual structure which is been created from using single table or multiple tables.If the logical structure is created from single table then it is called as Simple view.If logical structure is created using  multiple tables using joins then it is called as Complex View.

Click here to get more information about views

20.What is index and what are types of indexes?[80% asked SQL Interview Questions ]

Answer:

Indexing is nothing but the performance tuning mechanism which allows the fast retrieval of the records from table.

Following are types of indexes:

1.Normal Indexes

2.Bit Map indexes

3.Unique indexes

4.Clustered Indexes

5.Non Clustered Indexes


SQL Joins: 12 Practice Questions with Detailed Answers
Author's photo
Tihomir Babic
JOIN
sql practice
Table of Contents

List of Exercises
INNER JOIN
Dataset 1
Exercise 1: List All Books and Their Authors
Exercise 2: List Authors and Books Published After 2005
Exercise 3: Show Books Adapted Within 4 Years and Rated Lower Than the Adaptation
LEFT JOIN
Exercise 4: Show All Books and Their Adaptations (If Any)
Exercise 5: Show All Books and Their Movie Adaptations
RIGHT JOIN
Exercise 6: Show All Books with Their Reviews (If Any)
FULL JOIN
Exercise 7: List All the Books and All the Authors
Joining 3 or More Tables
Dataset 2
Exercise 8: Show Products Under 150 Calories and Their Department
Exercise 9: List All Products with Their Producers, Departments, and Carbs
Exercise 10: Show All the Products, Prices, Producers, and Departments
Self-Join
Dataset 3
Exercise 11: List All Workers and Their Direct Supervisors
Non-Equi Joins
Dataset 4
Exercise 12: Show Cars with Higher Mileage Than a Specific Car
SQL JOINs Practice Makes Perfect. More Practice? Perfect-er!
In this article, we dig into our SQL JOINS course and give you 12 join exercises to solve. But don’t worry – all the exercises have solutions and explanations. If you get stuck, help is there! This is, after all, made for practicing and learning. 

SQL joins can be tricky. It’s not just the syntax, but also knowing what joins to use in what scenarios.

Joins are used when combining data from two or more tables in SQL. The tables can be joined in several ways, and, depending on the tables, each way of joining them can result in a completely different result.  There’s no other way to learn this than practice. Yes, you can read explanations and typical uses of SQL joins. That helps, for sure! But practice builds on that through problem-solving and repetition, which makes your knowledge stick. The more you practice, the greater the possibility that the real-life data problems you’ll have to solve will be similar or completely the same as what you’ve already done!

And practice is what we’ll do in this article! We’ll show you exercises for basic and more advanced SQL joins uses. If you like them, you’ll enjoy our SQL JOINs course even more, as all the exercises are taken from there. In total, the course offers you 93 SQL joins exercises. They cover topics ranging from the types of joins in SQL, to filtering data, joining more than two tables, self-joining a table, and using non-equi joins.

OK, so let’s introduce the datasets and start exercising, shall we? Feel free to help yourself with the SQL JOIN Cheat Sheet as you go.

List of Exercises
Here's a list of all exercises in the article:

Exercise 1: List All Books and Their Authors
Exercise 2: List Authors and Books Published After 2005
Exercise 3: Show Books Adapted Within 4 Years and Rated Lower Than the Adaptation
Exercise 4: Show All Books and Their Adaptations (If Any)
Exercise 5: Show All Books and Their Movie Adaptations
Exercise 6: Show All Books with Their Reviews (If Any)
Exercise 7: List All the Books and All the Authors
Exercise 8: Show Products Under 150 Calories and Their Department
Exercise 9: List All Products with Their Producers, Departments, and Carbs
Exercise 10: Show All the Products, Prices, Producers, and Departments
Exercise 11: List All Workers and Their Direct Supervisors
Exercise 12: Show Cars with Higher Mileage Than a Specific Car

INNER JOIN
INNER JOIN is a type of SQL join that returns only the matching rows from the joined tables.

To show you how this works, we’ll use Dataset 1 from the course.

Dataset 1
The dataset consists of four tables: author, book, adaptation, and book_review.

The first table shows the author data in the following columns:

id – The author’s unique ID within the database.
name – The author’s name.
birth_year – The year when that author was born.
death_year – The year when that author died (the field is empty if they are still alive).
Here are the table’s first few rows:

id	name	birth_year	death_year
1	Marcella Cole	1983	NULL
2	Lisa Mullins	1891	1950
3	Dennis Stokes	1935	1994
4	Randolph Vasquez	1957	2004
5	Daniel Branson	1965	1990
…	…	…	…
The second table, book,  shows details about books. The columns are:

id – The ID of a given book.
author_id – The ID of the author who wrote that book.
title – The book’s title.
publish_year – The year when the book was published.
publishing_house – The name of the publishing house that printed the book.
rating – The average rating for the book.
These are the first five rows:

id	author_id	title	publish_year	publishing_house	rating
1	NULL	Soulless girl	2008	Golden Albatros	4.3
2	NULL	Weak Heart	1980	Diarmud Inc.	3.8
3	4	Faith Of Light	1995	White Cloud Press	4.3
4	NULL	Memory Of Hope	2000	Rutis Enterprises	2.7
5	6	Warrior Of Wind	2005	Maverick	4.6
…	…	…	…	…	…
The adaptation table has the following columns:

book_id – The ID of the adapted book.
type – The type of adaptation (e.g. movie, game, play, musical).
title – The name of this adaptation.
release_year – The year when the adaptation was created.
rating – The average rating for the adaptation.
Here’s a snapshot of the data from this table:

book_id	type	title	release_year	rating
1	movie	Gone With The Wolves: The Beginning	2008	3
3	movie	Companions Of Tomorrow	2001	4.2
5	movie	Homeless Warrior	2008	4
2	movie	Blacksmith With Silver	2014	4.3
4	movie	Patrons And Bearers	2004	3.2
…	…	…	…	…
The final table is book_review. It consists of the following columns:

book_id - The ID of a reviewed book.
review - The summary of the review.
author - The name of the review's author.
Here’s the data:

book_id	review	author
1	An incredible book	Sylvia Jones
1	Great, although it has some flaws	Jessica Parker
2	Dennis Stokes takes the reader for a ride full of emotions	Thomas Green
3	Incredible craftsmanship of the author	Martin Freeman
4	Not the best book by this author	Jude Falth
5	Claudia Johnson at her best!	Joe Marqiz
6	I cannot recall more captivating plot	Alexander Durham
What's your SQL level? Apply for a test.
Exercise 1: List All Books and Their Authors
Exercise: Show the name of each author together with the title of the book they wrote and the year in which that book was published.

Solution:

SELECT
  name,
  title,
  publish_year
FROM author
JOIN book
  ON author.id = book.author_id;
Solution explanation: The query selects the name of the author, the book title, and its publishing year. This is data from the two tables: author and book. We are able to access both tables by using INNER JOIN. It returns only rows with matching values (values that satisfy the join condition) from both tables.

We first reference the table author in the FROM clause. Then we add the JOIN clause (which can also be written as INNER JOIN in SQL) and reference the table book.

The tables are joined on the common column. In this case, it's id from the table author and author_id from the table book. We want to join the rows where these columns share the same value. We do that using the ON clause and specifying the column names. We also put the table name before each column so the database knows where to look. That’s primarily because there’s an id column in both tables, but we want the id column only from the author table. By referencing the table name, the database will know from which table we need that column.

Solution output:

Here’s the output snapshot. We got all this data by joining two tables:

name	title	publish_year
Marcella Cole	Gone With The Wolves	2005
Lisa Mullins	Companions And Officers	1930
Dennis Stokes	Blacksmith With Silver	1984
Randolph Vasquez	Faith Of Light	1995
Michael Rostkovsky	Warrior Of Wind	2005
…	…	…
Exercise 2: List Authors and Books Published After 2005
Exercise: Show the name of each author together with the title of the book they wrote and the year in which that book was published. Show only books published after 2005.

Solution:

SELECT
  name,
  title,
  publish_year
FROM author
JOIN book
  ON author.id = book.author_id
WHERE publish_year > 2005;
Solution explanation: This exercise and its solution are almost the same as the previous one. This is reflected by the query selecting the same columns and joining the tables in the same way as earlier.

The difference is that the exercise now asks us to show only books published after 2005. This requires filtering the output; we do that using the WHERE clause.

WHERE is a clause that accepts conditions used to filter out the data. It is written after joining the tables. In our example, we filter by referencing the column publish_year after WHERE and using the comparison operator ‘greater than’ (>) to find the years after 2005.

Solution output:

The output shows only one book published after 2005.

name	title	publish_year
Darlene Lyons	Temptations In Nature	2007
Exercise 3: Show Books Adapted Within 4 Years and Rated Lower Than the Adaptation
Exercise: For each book, show its title, adaptation title, adaptation year, and publication year.

Include only books with a rating lower than the rating of their corresponding adaptation. Additionally, show only those books for which an adaptation was released within four years of the book’s publication.

Rename the title column from the book table to book_title and the title column from the adaptation table to adaptation_title.

Solution:

SELECT
  book.title AS book_title,
  adaptation.title AS adaptation_title,
  book.publish_year,
  adaptation.release_year
FROM book
JOIN adaptation
  ON book.id = adaptation.book_id
WHERE adaptation.release_year - book.publish_year <= 4
  AND book.rating < adaptation.rating;
Solution explanation: Let’s start explaining the solution from the FROM and JOIN clauses. The columns we need to show are from the tables book and adaptation. We reference the first table in FROM and the second in JOIN.

In the ON clause, we equal the two book ID columns and specify the table of each column. This is the same as earlier, only with different table and column names.

Now, we need to select the required columns. The thing here is there’s a title column in both tables. To avoid ambiguity, a best practice is to reference the table name before each column in the SELECT.

Note: The above is mandatory only for ambiguous columns. However, it’s a good idea to do that with all columns; it improves code readability and the approach remains consistent.

After selecting the columns, we need to rename some of them. We do that using the keyword AS and writing a new column name afterward. That way, one title column becomes book_title, the other becomes adaptation_title. Giving aliases to the column names also helps get rid of ambiguity.

Now we need to filter the output. The first condition is that the adaptation had to be released four years or less after the book. We again use WHERE and simply deduct the book publish year from the adaptation release year. Then we say that the difference has to be less than or equal to (<=) 4.

We also need to add the second condition, where the book has a lower rating than the adaptation. It’s simple! The question implies that both the first and the second conditions have to be satisfied. The clue is in AND, a logical operator we use for adding the second condition. Here, it uses the ‘less than’ (<) operator to compare the two ratings.

Solution output:

The output shows three book–adaptation pairs that satisfy the conditions.

book_title	adaptation_title	publish_year	release_year
Memory Of Hope	Patrons And Bearers	2000	2004
Music At The Lake	Music At The Lake	2004	2007
Companion Of Tomorrow	Lighting Faith	1949	1952
LEFT JOIN
Now that you get the gist of INNER JOIN, let’s move on to LEFT JOIN. It’s a type of outer join that returns all the columns from the left (the first) table and only the matching rows from the right (the second) table. If there is non-matching data, it’s shown as NULL.

You can learn more in our article about LEFT JOIN.

Exercise 4: Show All Books and Their Adaptations (If Any)
Exercise: Show the title of each book together with the title of its adaptation and the date of the release. Show all books, regardless of whether they had adaptations.

 

Solution:

SELECT
  book.title,
  adaptation.title,
  adaptation.release_year
FROM book
LEFT JOIN adaptation
  ON book.id = adaptation.book_id;
Solution explanation: We first select the required columns from the two tables. Then we join book (the left table) with adaptation (the right table) using LEFT JOIN. You see that the SQL join syntax is the same for INNER JOIN. The only thing that changes is the join keyword.

Note: SQL accepts both LEFT JOIN and LEFT OUTER JOIN. They are the same command.

Solution output:

The output snapshot shows the required data, with some of the data shown as NULL. These are the books without the adaptation.

title	title-2	release_year
Soulless girl	Gone With The Wolves: The Beginning	2008
Faith Of Light	Companions Of Tomorrow	2001
Warrior Of Wind	Homeless Warrior	2008
…	…	…
Guarding The Emperor	NULL	NULL
Blacksmith With Silver	NULL	NULL
…	…	…
Exercise 5: Show All Books and Their Movie Adaptations
Exercise: Show all books with their movie adaptations. Select each book's title, the name of its publishing house, the title of its adaptation, and the type of the adaptation. Keep the books with no adaptations in the result.

Solution:

SELECT
  book.title,
  publishing_house,
  adaptation.title,
  adaptation.type
FROM book
LEFT JOIN adaptation
  ON book.id = adaptation.book_id
WHERE type = 'movie'
  OR type IS NULL;
Solution explanation:

The question asks to show all the rows, even those without any adaptations. It’s possible that there are books without adaptations, so we use LEFT JOIN.

We first select the book title, its publishing house, its adaptation title, and its type.

Then we join book (the left table) with adaptation (the right table) using LEFT JOIN. We join the tables on the book ID. All the books that don’t satisfy the conditions will have NULLs as an adaptation title and type.

We filter data using WHERE. The first condition is that the adaptation type has to be a movie, so we equal the type column with a movie using the equal sign (=).  Note: When using text data in the WHERE condition, it must be enclosed in single quotes ('').

The second filtering condition is added using the logical operator OR. It says that the type can also be NULL if it’s not a movie. The exercise asks us to keep books with no adaptations in the results.

Solution output:

Here’s the output snapshot. You can see that it shows only books adapted as movies or not adapted at all.

title	publishing_house	title-2	type
Soulless girl	Golden Albatros	Gone With The Wolves: The Beginning	movie
Faith Of Light	White Cloud Press	Companions Of Tomorrow	movie
Warrior Of Wind	Maverick	Homeless Warrior	movie
…	…	…	…
Guarding The Emperor	Flying Pen Media	NULL	NULL
Blacksmith With Silver	Diarmud Inc.	NULL	NULL
RIGHT JOIN
Where there’s LEFT JOIN, there’s also RIGHT JOIN, right? Despite being the LEFT JOIN's mirror image, it’s still a part of the SQL joins practice.

It’s a type of join that returns all the columns from the right (the second) table and only the matching rows from the left (the first) table. If there is non-matching data, it’s shown as NULL.

Exercise 6: Show All Books with Their Reviews (If Any)
Exercise: Join the book_review and book tables using a RIGHT JOIN. Show the title of the book, the corresponding review, and the name of the review's author. Consider all books, even those that weren't reviewed.

Solution:

SELECT
  book.title,
  book_review.review,
  book_review.author
FROM book_review
RIGHT JOIN book
  ON book.id = book_review.book_id;
Solution explanation:

We first select the required columns. Then we do as we’re told: join the tables using RIGHT JOIN. We join the tables on the book ID. The table book is the right table; we want all the data from it, regardless of the reviews.

As you can see, the syntax stays the same as in INNER JOIN and LEFT JOIN.

Note: SQL accepts both RIGHT JOIN and RIGHT OUTER JOIN.

Solution output:

The query returns all the book titles, their reviews, and authors. Where there’s no review or author information, a NULL is shown.

title	review	author
Soulless girl	An incredible book	Sylvia Jones
Soulless girl	Great, although it has some flaws	Jessica Parker
…	…	…
Guarding The Emperor	NULL	NULL
Companions And Officers	NULL	NULL
Blacksmith With Silver	NULL	NULL
…	…	…
Practice your SQL knowledge with our SQL Practice Set course.

FULL JOIN
Here’s another join type that’s useful in some scenarios: the FULL JOIN . This is a LEFT JOIN and RIGHT JOIN put together. It shows matching rows from both tables, rows that have no match from the left table, and rows that have no match from the right table. In short, it shows all data from both tables.

You can read more about how and when to use FULL JOIN.

Exercise 7: List All the Books and All the Authors
Exercise: Display the title of each book along with the name of its author. Show all books, even those without an author. Show all authors, even those who haven't published a book yet. Use a FULL JOIN.

Solution:

SELECT
  title,
  name
FROM book
FULL JOIN author
  ON book.author_id = author.id;
Solution explanation: The question requires showing all books, but also all authors – FULL JOIN is perfect for doing this elegantly.

We select the book title and the author's name. Next, we FULL JOIN the table book with the table author. The joining condition is that the author ID has to be the same in both tables. Again, the syntax is the same as in all the previous join types.

Note: SQL accepts both FULL JOIN and FULL OUTER JOIN.

Solution output:

The output shows all the books and all the authors, whether the authors or books exist in both tables or not.

title	name
Gone With The Wolves	Marcella Cole
Companions And Officers	Lisa Mullins
…	…
NULL	Daniel Branson
…	…
Weep Of The West	NULL
Joining 3 or More Tables
Yes, SQL joins allow for joining more than two tables. We’ll see how to do that in this part of the SQL joins practice. You can find a more detailed explanation of multiple joins here.

We also need a new dataset, so let’s introduce it.

Dataset 2
The first table in the dataset is department. Its columns are:

id – The unique ID of the department.
name – The department name, i.e. where a particular type of product is sold.
Here’s the data from the table.

id	name
1	fruits
2	vegetables
3	seafood
4	deli
5	bakery
6	meat
7	dairy
The second table is product, and it consists of the following columns:

id – The ID of a given product.
name – The product’s name.
department_id – The ID of the department where the product is located.
shelf_id – The ID of the shelf of that department where the product is located.
producer_id – The ID of the company that manufactures this product.
price – The product’s price.
Here’s the data snapshot:

id	name	department_id	shelf_id	producer_id	price
1	Apple	1	1	NULL	0.5
2	Avocado	1	1	7	1
3	Banana	1	1	7	0.5
4	Grapefruit	NULL	1	1	0.5
5	Grapes	1	1	4	2
…	…	…	…	…	…
The next table is nutrition_data. Its columns and data are given below:

product_id – The ID of a product.
calories – The calorific value of that product.
fat – The amount of fat in that product.
carbohydrate – The amount of carbohydrates in that product.
protein – The amount of protein in that product.
product_id	calories	fat	carbohydrate	protein
1	130	0	5	1
2	50	4.5	3	1
3	110	0	30	1
4	60	0	15	1
NULL	90	0	23	0
…	…	…	…	…
The fourth table is named producer. It has the following columns:

id – The ID of a given food producer.
name – The name of the producer.
Below is the data from this table:

id	name
1	BeHealthy
2	HealthyFood Inc.
3	SupremeFoods
4	Foodie
5	Gusto
6	Baker n Sons
7	GoodFoods
8	Tasty n Healthy
The last table in the dataset is sales_history. It has the following columns:

date – The date of sale.
product_id – The ID of the product sold.
amount – The amount of that product sold on a particular day.
Here’s the data, too:

date	product_id	amount
2015-01-14	1	14
2015-01-14	1	13
2015-01-15	2	2
2015-01-16	2	6
2015-01-17	3	8
…	…	…
Exercise 8: Show Products Under 150 Calories and Their Department
Exercise: List all products that have fewer than 150 calories. For each product, show its name (rename the column product) and the name of the department where it can be found (name the column department).

Solution:

SELECT
  p.name AS product,
  d.name AS department
FROM department d
JOIN product p
  ON d.id = p.department_id
JOIN nutrition_data nd
  ON nd.product_id = p.id
WHERE nd.calories < 150;
Solution explanation: The general principle of how you join the third (fourth, fifth…) table is that you simply add another JOIN. You can see how it’s done in this article explaining multiple joins. We’ll do it the same way here.

We first join the department table with the product table on the department ID using JOIN. But we also need the third table. To get the data from it, we just add another JOIN, which will join the product table with the nutrition_data table. The syntax is the same as with the first join. In this case, the query joins the tables on the product ID.

Then we use WHERE to find products with fewer than 150 calories. We finally select the product and department names and rename the columns as per the exercise instructions.

Note: You probably noticed both selected columns have the same original name. And you also noticed we solved this ambiguity by putting some strange short table names in front of all the columns in the query. These shortened names are table aliases, which you give by simply writing them after the table name in FROM or JOIN. By giving aliases to the tables, you can shorten the tables’ names. Therefore, you don’t have to write their full names (sometimes they can be really long!), but the short aliases instead. This saves time and space.

Solution output:

The output shows a list of the products and the department they belong to. It includes only those products with fewer than 150 calories.

product	department
Apple	fruits
Avocado	fruits
Banana	fruits
Kiwi	fruits
Lemon	fruits
…	…
Exercise 9: List All Products with Their Producers, Departments, and Carbs
Exercise: For each product, display the:

Name of the company that produced it (name the column producer_name).
Name of the department where the product is located (name it department_name).
Product name (name it product_name).
Total number of carbohydrates in the product.
Your query should still consider products with no information about producer_id or department_id.

Solution:

SELECT
  prod.name AS producer_name,
  d.name AS department_name,
  p.name AS product_name,
  nd.carbohydrate
FROM product p
LEFT JOIN producer prod
  ON prod.id = p.producer_id
LEFT JOIN department d
  ON d.id = p.department_id
LEFT JOIN nutrition_data nd
  ON nd.product_id = p.id;
Solution explanation: The query selects the required columns. Then it joins the table product with the table producer on the producer ID using LEFT JOIN. We choose this type of join because we have to include products without producer data.

Then we add another LEFT JOIN. This one adds the department table and joins it with the product table. Again, we choose LEFT JOIN because we need to show products that don’t have a department.

There’s also a third join! We simply add it to the chain of the previous joins. It’s again LEFT JOIN, as we add the nutrition_data table and join it with the product table.

This is an interesting topic to explore, so here’s an article that explains multiple LEFT JOINs to help you with it.

Solution output:

The output shows all the products with their producer and department names and carbohydrate amounts:

producer_name	department_name	product_name	carbohydrate
BeHealthy	fruits	Kiwi	20
BeHealthy	vegetables	Broccoli	8
BeHealthy	meat	Chicken	NULL
BeHealthy	NULL	Grapefruit	15
HealthyFood Inc.	vegetables	Celery	4
…	…	…	…
If you need more details, please read how to LEFT JOIN multiple tables in SQL.

Exercise 10: Show All the Products, Prices, Producers, and Departments
Exercise: For each product, show its name, price, producer name, and department name.

Alias the columns as product_name, product_price, producer_name, and department_name, respectively. Include all the products, even those without a producer or department. Also, include the producers and departments without a product.

Solution:

SELECT
  p.name AS product_name,
  p.price AS product_price,
  prod.name AS producer_name,
  d.name AS department_name
FROM product p
FULL JOIN producer prod
  ON p.producer_id = prod.id
FULL JOIN department d
  ON d.id = p.department_id;
Solution explanation: This exercise requires using FULL JOIN, as we need all the data from the tables we’ll use: product, producer, and department.

The syntax is the same as in the previous examples. We just join the different tables (product and producer) on the producer ID and use a different type of join:  FULL JOIN.

The second FULL JOIN joins the product table with the department table.

After selecting the required columns and renaming them, we get the following output.

Solution output:

The solution shows all the data from the selected tables and columns:

product_name	product_price	producer_name	department_name
Chicken	5.5	BeHealthy	meat
Broccoli	2.5	BeHealthy	vegetables
Kiwi	0.3	BeHealthy	fruits
Grapefruit	0.5	BeHealthy	NULL
Cucumber	0.7	HealthyFood Inc.	vegetables
…	…	…	…
Self-Join
A self-join is not a distinct type of SQL JOIN – any join can be used for self-joining a table. It’s simply a join used to join the table with itself. By giving different aliases to the same table, it’s treated as two different tables when self-joined.

For more details, check out our illustrated guide to the SQL self-join.

Dataset 3
The dataset for this example consists of only one table: workshop_workers. It has the following columns.

id – The worker’s ID.
name – The worker’s first and last name.
specialization – The worker's specialization.
master_id – The ID of the worker's supervisor.
experience – The worker's years of experience.
project_id – The ID of the project to which the worker is currently assigned.
Here’s the data:

id	name	specialization	master_id	experience	project_id
1	Mathew Conn	woodworking	NULL	20	1
2	Kate Brown	woodworking	1	4	1
3	John Doe	incrusting	5	3	1
4	John Kowalsky	watchmaking	7	2	3
5	Suzan Gregowitch	incrusting	NULL	15	4
Exercise 11: List All Workers and Their Direct Supervisors
Exercise: Show all workers' names together with the names of their direct supervisors. Rename the columns  apprentice_name and master_name, respectively. Consider only workers who have a supervisor (i.e. a master).

Solution:

SELECT
  apprentice.name AS apprentice_name,
  master.name AS master_name
FROM workshop_workers apprentice
JOIN workshop_workers master
  ON apprentice.master_id = master.id;
Solution explanation: Let’s start with explaining the self-join. The general principle is the same as with regular joins. We reference the table in FROM and give it an alias, apprentice. Then we use JOIN and reference the same table in it. This time, we give the table the alias master. We’re basically pretending that one table has the apprentice data and the other has the master data.

The tables are joined on the master ID from the apprentice table and the ID from the master table.

This example is a typical use of a self-join: the table has a column (master_id) that references another column from the same table (id). Both columns show the worker’s ID. When there’s NULL in master_id, it means that the worker doesn’t have a master. In other words, they are the master.

After self-joining, we simply select the required columns and rename them.

Solution output:

The output shows all the apprentices and their direct supervisors.

apprentice_name	master_name
Kate Brown	Mathew Conn
John Doe	Suzan Gregowitch
John Kowalsky	Joe Darrington
Peter Parker	Joe Darrington
Mary Smith	Mathew Conn
Carlos Bell	Suzan Gregowitch
Dennis Wright	Joe Darrington
What's your SQL level? Apply for a test.
Non-Equi Joins
The final topic we’ll tackle in this SQL joins practice are non-equi joins. The joins we used so far are called equi-joins because they use the equality sign (=) in the joining condition. Non-equi are all other joins that use any other operators – comparison operators (<, >, <=, >=, !=, <>), the BETWEEN operator, or any other logical condition – to join tables.

Dataset 4
We’ll use the dataset consisting of two tables. The first table is car. Here are its columns:

id – The car’s ID in the database.
model – The car’s model.
brand – The car’s brand.
original_price – The original price of that car when new.
mileage – The car’s total mileage.
prod_year – The car’s production year.
The data looks like this:

id	model	brand	original_price	mileage	prod_year
1	Speedster	Teiko	80,000	150,000	1999
2	Roadmaster	Teiko	110,000	30,000	1980
3	Sundry	Teiko	40,000	25,000	1991
4	Furu	Domus	50,000	10,000	2002
5	Emperor	Domus	65,000	140,000	2005
6	King	Domus	200,000	6,000	1981
7	Empress	Domus	60,000	7,600	1997
8	Fury	Tatsu	150,000	13,000	1993
The second table is charity_auction with these columns:

car_id – The car’s ID.
initial_price – The car’s initial (i.e. starting) price.
final_price – The actual price when the car was sold.
buyer_id – The ID of the person who bought the car.
Here’s the data:

car_id	initial_price	final_price	buyer_id
1	65,000	NULL	NULL
3	35,000	50,000	1
5	50,000	120,000	3
6	350,000	410,000	4
7	65,000	NULL	NULL
Exercise 12: Show Cars with Higher Mileage Than a Specific Car
Exercise: Show the model, brand, and final price of each car sold at the auction. Consider only those sold cars that have more mileage than the car with the id = 4.

Solution:

SELECT
  car.model,
  car.brand,
  car.final_price
FROM car
JOIN charity_auction ca
  ON car.id = ca.car_id
JOIN car car2
  ON car.mileage > car2.mileage
WHERE car2.id = 4
  AND final_price IS NOT NULL;
Solution explanation: We select the car model, brand, and final price.

In the first JOIN, we join the car table with the charity_auction table. The tables are joined where the car IDs are the same. This is our regular equi JOIN.

We add the second JOIN, which is a self-join. It adds the table car again, so we can filter the data using the non-equi join condition. The condition will return all the cars from the car table and all the cars from the car2 table with the lower mileage. This is a non-equi condition as it uses the ‘greater than’ ( > ) operator. The syntax is the same, but there’s > instead of = this time.

Finally, we need to filter data using WHERE. We’re not interested in comparing the mileage of all cars. We want to show the cars that have a mileage higher than the car with id = 4. This is what the first filtering condition does.

We add another filtering condition that says the final price shouldn’t be NULL, i.e., the car has to have been sold in the auction.

Solution output:

The result shows two cars:

model	brand	final_price
Sundry	Teiko	50,000
Emperor	Domus	120,000
