Prepare Sample Data To Practice SQL Skills
Sample Table – Worker
|WORKER_ID	|FIRST_NAME|	LAST_NAME|	SALARY|	JOINING_DATE	|DEPARTMENT|
|-----|----------|----------|----------|----------|----------|
|001	|Monika	Arora	|100000	|2021-02-20 09:00:00|	HR|
|002	|Niharika	Verma	|80000	|2021-06-11 09:00:00|	Admin|
|003	|Vishal	Singhal	|300000	|2021-02-20 09:00:00|	HR|
|004	|Amitabh	Singh	|500000	|2021-02-20 09:00:00|	Admin|
|005	|Vivek	Bhati	|500000	|2021-06-11 09:00:00|	Admin|
|006	|Vipul	Diwan	|200000	|2021-06-11 09:00:00|	Account|
|007	|Satish	Kumar	|75000	|2021-01-20 09:00:00|	Account|
|008	|Geetika	Chauhan	|90000	|2021-04-11 09:00:00|	Admin|
Worker Table
Sample Table – Bonus
WORKER_REF_ID	BONUS_DATE	BONUS_AMOUNT
1	2023-02-20 00:00:00	5000
2	2023-06-11 00:00:00	3000
3	2023-02-20 00:00:00	4000
1	2023-02-20 00:00:00	4500
2	2023-06-11 00:00:00	3500
Bonus Table
Sample Table – Title
WORKER_REF_ID	WORKER_TITLE	AFFECTED_FROM
1	Manager	2023-02-20 00:00:00
2	Executive	2023-06-11 00:00:00
8	Executive	2023-06-11 00:00:00
5	Manager	2023-06-11 00:00:00
4	Asst. Manager	2023-06-11 00:00:00
7	Executive	2023-06-11 00:00:00
6	Lead	2023-06-11 00:00:00
3	Lead	2023-06-11 00:00:00
Title Table
To prepare the sample data, run the following queries in your database query executor or SQL command line. We’ve tested them with the latest version of MySQL Server and MySQL Workbench query browser. You can download these tools and install them to execute the SQL queries. However, these queries will run fine in any online MySQL compiler, you may use them.



Replay

Unmute
Current Time 
7:27
/
Duration 
7:27

Fullscreen
Now Playing









Play Video
50 SQL Exercises, Practice, Solution

Share
Watch onHumix
SQL Script to Seed Sample Data.
Initialize Test Data
Run the following script to create test tables and insert data.
Run
CREATE TABLE Worker (
    WORKER_ID INT NOT NULL PRIMARY KEY,
    FIRST_NAME CHAR(25),
    LAST_NAME CHAR(25),
    SALARY INT,
    JOINING_DATE DATETIME,
    DEPARTMENT CHAR(25)
);

INSERT INTO Worker (WORKER_ID, FIRST_NAME, LAST_NAME, SALARY, JOINING_DATE, DEPARTMENT) VALUES
    (1, 'Monika', 'Arora', 100000, '2021-02-20 09:00:00', 'HR'),
    (2, 'Niharika', 'Verma', 80000, '2021-06-11 09:00:00', 'Admin'),
    (3, 'Vishal', 'Singhal', 300000, '2021-02-20 09:00:00', 'HR'),
    (4, 'Amitabh', 'Singh', 500000, '2021-02-20 09:00:00', 'Admin'),
    (5, 'Vivek', 'Bhati', 500000, '2021-06-11 09:00:00', 'Admin'),
    (6, 'Vipul', 'Diwan', 200000, '2021-06-11 09:00:00', 'Account'),
    (7, 'Satish', 'Kumar', 75000, '2021-01-20 09:00:00', 'Account'),
    (8, 'Geetika', 'Chauhan', 90000, '2021-04-11 09:00:00', 'Admin');

CREATE TABLE Bonus (
    WORKER_REF_ID INT,
    BONUS_AMOUNT INT,
    BONUS_DATE DATETIME,
    FOREIGN KEY (WORKER_REF_ID) REFERENCES Worker(WORKER_ID) ON DELETE CASCADE
);

INSERT INTO Bonus (WORKER_REF_ID, BONUS_AMOUNT, BONUS_DATE) VALUES
    (1, 5000, '2023-02-20'),
    (2, 3000, '2023-06-11'),
    (3, 4000, '2023-02-20'),
    (1, 4500, '2023-02-20'),
    (2, 3500, '2023-06-11');

CREATE TABLE Title (
    WORKER_REF_ID INT,
    WORKER_TITLE CHAR(25),
    AFFECTED_FROM DATETIME,
    FOREIGN KEY (WORKER_REF_ID) REFERENCES Worker(WORKER_ID) ON DELETE CASCADE
);

INSERT INTO Title (WORKER_REF_ID, WORKER_TITLE, AFFECTED_FROM) VALUES
    (1, 'Manager', '2023-02-20 00:00:00'),
    (2, 'Executive', '2023-06-11 00:00:00'),
    (8, 'Executive', '2023-06-11 00:00:00'),
    (5, 'Manager', '2023-06-11 00:00:00'),
    (4, 'Asst. Manager', '2023-06-11 00:00:00'),
    (7, 'Executive', '2023-06-11 00:00:00'),
    (6, 'Lead', '2023-06-11 00:00:00'),
    (3, 'Lead', '2023-06-11 00:00:00');
    
Tables and data initialized successfully!
Running the above SQL on any MySQL instance will show a result similar to the one below.

SQL Query Questions - Creating Sample Data
Creating Sample Data to Practice SQL Skill.
Start with 20 Basic SQL Questions for Practice
Below are some of the most commonly asked SQL query questions and answers for practice. Get a timer to track your progress and start practicing.

Q-1. Write an SQL query to fetch “FIRST_NAME” from the Worker table using the alias name <WORKER_NAME>.
Ans.

The required query is:

Ezoic
Query #1
RunShow Solution
Select FIRST_NAME AS WORKER_NAME from Worker;
SQL query executed successfully!
Details
WORKER_NAME
Monika
Niharika
Vishal
Amitabh
Vivek
Vipul
Satish
Geetika
Q-2. Write an SQL query to fetch “FIRST_NAME” from the Worker table in upper case.
Ans.

The required query is:

Query #2
RunShow Solution
Select upper(FIRST_NAME) from Worker;
SQL query executed successfully!
Details
upper(FIRST_NAME)
MONIKA
NIHARIKA
VISHAL
AMITABH
VIVEK
VIPUL
SATISH
GEETIKA
Q-3. Write an SQL query to fetch unique values of DEPARTMENT from the Worker table.
Ans.

Ezoic
The required query is:

Query #3
RunShow Solution
Select distinct DEPARTMENT from Worker;
SQL query executed successfully!
Details
DEPARTMENT
HR
Admin
Account
Q-4. Write an SQL query to print the first three characters of  FIRST_NAME from the Worker table.
Ans.

The required query is:

Ezoic
Query #4
RunShow Solution
Select substring(FIRST_NAME,1,3) from Worker;
SQL query executed successfully!
Details
substring(FIRST_NAME,1,3)
Mon
Nih
Vis
Ami
Viv
Vip
Sat
Gee
Q-5. Write an SQL query to find the position of the alphabet (‘a’) in the first name column ‘Amitabh’ from the Worker table.
Ans.

The required query is:

Query #5
RunShow Solution
SELECT INSTR(FIRST_NAME, 'a') FROM Worker WHERE FIRST_NAME = 'Amitabh';
SQL query executed successfully!
Details
INSTR(FIRST_NAME, 'a')
5
Q-6. Write an SQL query to print the FIRST_NAME from the Worker table after removing white spaces from the right side.
Ans.

The required query is:

Query #6
RunShow Solution
Select RTRIM(FIRST_NAME) from Worker;
SQL query executed successfully!
Details
RTRIM(FIRST_NAME)
Monika
Niharika
Vishal
Amitabh
Vivek
Vipul
Satish
Geetika
Q-7. Write an SQL query to print the DEPARTMENT from the Worker table after removing white spaces from the left side.
Ans.

The required query is:

Query #7
RunShow Solution
Select LTRIM(DEPARTMENT) from Worker;
SQL query executed successfully!
Details
LTRIM(DEPARTMENT)
HR
Admin
HR
Admin
Admin
Account
Account
Admin
Q-8. Write an SQL query that fetches the unique values of DEPARTMENT from the Worker table and prints its length.
Ans.

The required query is:

Query #8
RunShow Solution
SELECT DISTINCT DEPARTMENT, LENGTH(DEPARTMENT) AS Department_Length FROM Worker;
SQL query executed successfully!
Details
DEPARTMENT	Department_Length
HR	2
Admin	5
Account	7
Q-9. Write an SQL query to print the FIRST_NAME from the Worker table after replacing ‘a’ with ‘A’.
Ans.

The required query is:

Query #9
RunShow Solution
Select REPLACE(FIRST_NAME,'a','A') from Worker;
SQL query executed successfully!
Details
REPLACE(FIRST_NAME,'a','A')
MonikA
NihArikA
VishAl
AmitAbh
Vivek
Vipul
SAtish
GeetikA
Q-10. Write an SQL query to print the FIRST_NAME and LAST_NAME from the Worker table into a single column COMPLETE_NAME. A space char should separate them.
Ans.

The required query is:

Query #10
RunShow Solution
SELECT FIRST_NAME || ' ' || LAST_NAME AS COMPLETE_NAME FROM Worker;
SQL query executed successfully!
Details
COMPLETE_NAME
Monika Arora
Niharika Verma
Vishal Singhal
Amitabh Singh
Vivek Bhati
Vipul Diwan
Satish Kumar
Geetika Chauhan
Q-11. Write an SQL query to print all Worker details from the Worker table order by FIRST_NAME Ascending.
Ans.

The required query is:

Query #11
RunShow Solution
Select * from Worker order by FIRST_NAME asc;
SQL query executed successfully!
Details
WORKER_ID	FIRST_NAME	LAST_NAME	SALARY	JOINING_DATE	DEPARTMENT
4	Amitabh	Singh	500000	2021-02-20 09:00:00	Admin
8	Geetika	Chauhan	90000	2021-04-11 09:00:00	Admin
1	Monika	Arora	100000	2021-02-20 09:00:00	HR
2	Niharika	Verma	80000	2021-06-11 09:00:00	Admin
7	Satish	Kumar	75000	2021-01-20 09:00:00	Account
6	Vipul	Diwan	200000	2021-06-11 09:00:00	Account
3	Vishal	Singhal	300000	2021-02-20 09:00:00	HR
5	Vivek	Bhati	500000	2021-06-11 09:00:00	Admin
Q-12. Write an SQL query to print all Worker details from the Worker table order by FIRST_NAME Ascending and DEPARTMENT Descending.
Ans.

Ezoic
The required query is:

Query #12
RunShow Solution
Select * from Worker order by FIRST_NAME asc, DEPARTMENT desc;
SQL query executed successfully!
Details
WORKER_ID	FIRST_NAME	LAST_NAME	SALARY	JOINING_DATE	DEPARTMENT
4	Amitabh	Singh	500000	2021-02-20 09:00:00	Admin
8	Geetika	Chauhan	90000	2021-04-11 09:00:00	Admin
1	Monika	Arora	100000	2021-02-20 09:00:00	HR
2	Niharika	Verma	80000	2021-06-11 09:00:00	Admin
7	Satish	Kumar	75000	2021-01-20 09:00:00	Account
6	Vipul	Diwan	200000	2021-06-11 09:00:00	Account
3	Vishal	Singhal	300000	2021-02-20 09:00:00	HR
5	Vivek	Bhati	500000	2021-06-11 09:00:00	Admin
Q-13. Write an SQL query to print details for Workers with the first names “Vipul” and “Satish” from the Worker table.
Ans.

The required query is:

Ezoic
Query #13
RunShow Solution
Select * from Worker where FIRST_NAME in ('Vipul','Satish');
SQL query executed successfully!
Details
WORKER_ID	FIRST_NAME	LAST_NAME	SALARY	JOINING_DATE	DEPARTMENT
6	Vipul	Diwan	200000	2021-06-11 09:00:00	Account
7	Satish	Kumar	75000	2021-01-20 09:00:00	Account
Q-14. Write an SQL query to print details of workers excluding first names, “Vipul” and “Satish” from the Worker table.
Ans.

The required query is:

Query #14
RunShow Solution
Select * from Worker where FIRST_NAME not in ('Vipul','Satish');
SQL query executed successfully!
Details
WORKER_ID	FIRST_NAME	LAST_NAME	SALARY	JOINING_DATE	DEPARTMENT
1	Monika	Arora	100000	2021-02-20 09:00:00	HR
2	Niharika	Verma	80000	2021-06-11 09:00:00	Admin
3	Vishal	Singhal	300000	2021-02-20 09:00:00	HR
4	Amitabh	Singh	500000	2021-02-20 09:00:00	Admin
5	Vivek	Bhati	500000	2021-06-11 09:00:00	Admin
8	Geetika	Chauhan	90000	2021-04-11 09:00:00	Admin
Q-15. Write an SQL query to print details of Workers with DEPARTMENT name as “Admin”.
Ans.

Ezoic
The required query is:

Query #15
RunShow Solution
Select * from Worker where DEPARTMENT like 'Admin%';
SQL query executed successfully!
Details
WORKER_ID	FIRST_NAME	LAST_NAME	SALARY	JOINING_DATE	DEPARTMENT
2	Niharika	Verma	80000	2021-06-11 09:00:00	Admin
4	Amitabh	Singh	500000	2021-02-20 09:00:00	Admin
5	Vivek	Bhati	500000	2021-06-11 09:00:00	Admin
8	Geetika	Chauhan	90000	2021-04-11 09:00:00	Admin
Q-16. Write an SQL query to print details of the Workers whose FIRST_NAME contains ‘a’.
Ans.

The required query is:

Ezoic
Query #16
RunShow Solution
Select * from Worker where FIRST_NAME like '%a%';
SQL query executed successfully!
Details
WORKER_ID	FIRST_NAME	LAST_NAME	SALARY	JOINING_DATE	DEPARTMENT
1	Monika	Arora	100000	2021-02-20 09:00:00	HR
2	Niharika	Verma	80000	2021-06-11 09:00:00	Admin
3	Vishal	Singhal	300000	2021-02-20 09:00:00	HR
4	Amitabh	Singh	500000	2021-02-20 09:00:00	Admin
7	Satish	Kumar	75000	2021-01-20 09:00:00	Account
8	Geetika	Chauhan	90000	2021-04-11 09:00:00	Admin
Q-17. Write an SQL query to print details of the Workers whose FIRST_NAME ends with ‘a’.
Ans.

The required query is:

Query #17
RunShow Solution
Select * from Worker where FIRST_NAME like '%a';
SQL query executed successfully!
Details
WORKER_ID	FIRST_NAME	LAST_NAME	SALARY	JOINING_DATE	DEPARTMENT
1	Monika	Arora	100000	2021-02-20 09:00:00	HR
2	Niharika	Verma	80000	2021-06-11 09:00:00	Admin
8	Geetika	Chauhan	90000	2021-04-11 09:00:00	Admin
Q-18. Write an SQL query to print details of the Workers whose FIRST_NAME ends with ‘h’ and contains six alphabets.
Ans.

Ezoic
The required query is:

Query #18
RunShow Solution
Select * from Worker where FIRST_NAME like '_____h';
SQL query executed successfully!
Details
WORKER_ID	FIRST_NAME	LAST_NAME	SALARY	JOINING_DATE	DEPARTMENT
7	Satish	Kumar	75000	2021-01-20 09:00:00	Account
Q-19. Write an SQL query to print details of the Workers whose SALARY lies between 100000 and 500000.
Ans.

The required query is:

Query #19
RunShow Solution
Select * from Worker where SALARY between 100000 and 500000;
SQL query executed successfully!
Details
WORKER_ID	FIRST_NAME	LAST_NAME	SALARY	JOINING_DATE	DEPARTMENT
1	Monika	Arora	100000	2021-02-20 09:00:00	HR
3	Vishal	Singhal	300000	2021-02-20 09:00:00	HR
4	Amitabh	Singh	500000	2021-02-20 09:00:00	Admin
5	Vivek	Bhati	500000	2021-06-11 09:00:00	Admin
6	Vipul	Diwan	200000	2021-06-11 09:00:00	Account
Q-20. Write an SQL query to print details of the Workers who joined in Feb 2021.
Ans.

The required query is:

Query #20
RunShow Solution
SELECT * FROM Worker WHERE strftime('%Y', JOINING_DATE) = '2021' AND strftime('%m', JOINING_DATE) = '02';
SQL query executed successfully!
Details
WORKER_ID	FIRST_NAME	LAST_NAME	SALARY	JOINING_DATE	DEPARTMENT
1	Monika	Arora	100000	2021-02-20 09:00:00	HR
3	Vishal	Singhal	300000	2021-02-20 09:00:00	HR
4	Amitabh	Singh	500000	2021-02-20 09:00:00	Admin
12 Medium SQL Query Interview Questions / Answers for Practice
At this point, you have acquired a good understanding of the basics of SQL, let’s move on to some more intermediate-level SQL query interview questions. These questions will require us to use more advanced SQL syntax and concepts, such as GROUP BY, HAVING, and ORDER BY.

Ezoic
Q-21. Write an SQL query to fetch the count of employees working in the department ‘Admin’.
Ans.

The required query is:

Query #21
RunShow Solution
SELECT COUNT(*) FROM Worker WHERE DEPARTMENT = 'Admin';
SQL query executed successfully!
Details
COUNT(*)
4
Q-22. Write an SQL query to fetch worker names with salaries >= 50000 and <= 100000.
Ans.

Ezoic
The required query is:

Query #22
RunShow Solution
SELECT FIRST_NAME || ' ' || LAST_NAME AS Worker_Name, Salary FROM Worker WHERE Salary BETWEEN 50000 AND 100000;
SQL query executed successfully!
Details
Worker_Name	SALARY
Monika Arora	100000
Niharika Verma	80000
Satish Kumar	75000
Geetika Chauhan	90000
Q-23. Write an SQL query to fetch the number of workers for each department in descending order.
Ans.

The required query is:

Ezoic
Query #23
RunShow Solution
SELECT DEPARTMENT, count(WORKER_ID) No_Of_Workers FROM Worker GROUP BY DEPARTMENT ORDER BY No_Of_Workers DESC;
SQL query executed successfully!
Details
DEPARTMENT	No_Of_Workers
Admin	4
HR	2
Account	2
Q-24. Write an SQL query to print details of the Workers who are also Managers.
Ans.

The required query is:

Query #24
RunShow Solution
SELECT DISTINCT W.FIRST_NAME, T.WORKER_TITLE FROM Worker W INNER JOIN Title T ON W.WORKER_ID = T.WORKER_REF_ID AND T.WORKER_TITLE in ('Manager');
SQL query executed successfully!
Details
FIRST_NAME	WORKER_TITLE
Monika	Manager
Vivek	Manager
Q-25. Write an SQL query to fetch duplicate records having matching data in some fields of a table.
Ans.

Ezoic
The required query is:

Query #25
RunShow Solution
SELECT WORKER_TITLE, AFFECTED_FROM, COUNT(*) FROM Title GROUP BY WORKER_TITLE, AFFECTED_FROM HAVING COUNT(*) > 1;
SQL query executed successfully!
Details
WORKER_TITLE	AFFECTED_FROM	COUNT(*)
Executive	2023-06-11 00:00:00	3
Lead	2023-06-11 00:00:00	2
Q-26. Write an SQL query to show only odd rows from a table.
Ans.

The required query is:

Ezoic
Query #26
RunShow Solution
SELECT * FROM Worker WHERE WORKER_ID % 2 <> 0;
SQL query executed successfully!
Details
WORKER_ID	FIRST_NAME	LAST_NAME	SALARY	JOINING_DATE	DEPARTMENT
1	Monika	Arora	100000	2021-02-20 09:00:00	HR
3	Vishal	Singhal	300000	2021-02-20 09:00:00	HR
5	Vivek	Bhati	500000	2021-06-11 09:00:00	Admin
7	Satish	Kumar	75000	2021-01-20 09:00:00	Account
Q-27. Write an SQL query to show only even rows from a table.
Ans.

The required query is:

Query #27
RunShow Solution
SELECT * FROM Worker WHERE WORKER_ID % 2 = 0;
SQL query executed successfully!
Details
WORKER_ID	FIRST_NAME	LAST_NAME	SALARY	JOINING_DATE	DEPARTMENT
2	Niharika	Verma	80000	2021-06-11 09:00:00	Admin
4	Amitabh	Singh	500000	2021-02-20 09:00:00	Admin
6	Vipul	Diwan	200000	2021-06-11 09:00:00	Account
8	Geetika	Chauhan	90000	2021-04-11 09:00:00	Admin
Q-28. Write an SQL query to clone a new table from another table.
Ans.

The general query to clone a table with data is:

Query #28
RunShow Solution
CREATE TABLE WorkerClone AS SELECT * FROM Worker;
SQL query executed successfully!
Details
No records found.

Q-29. Write an SQL query to fetch intersecting records of two tables.
Ans.

The required query is:

Query #29
RunShow Solution
SELECT * FROM Worker INTERSECT SELECT * FROM WorkerClone;
SQL query executed successfully!
Details
WORKER_ID	FIRST_NAME	LAST_NAME	SALARY	JOINING_DATE	DEPARTMENT
1	Monika	Arora	100000	2021-02-20 09:00:00	HR
2	Niharika	Verma	80000	2021-06-11 09:00:00	Admin
3	Vishal	Singhal	300000	2021-02-20 09:00:00	HR
4	Amitabh	Singh	500000	2021-02-20 09:00:00	Admin
5	Vivek	Bhati	500000	2021-06-11 09:00:00	Admin
6	Vipul	Diwan	200000	2021-06-11 09:00:00	Account
7	Satish	Kumar	75000	2021-01-20 09:00:00	Account
8	Geetika	Chauhan	90000	2021-04-11 09:00:00	Admin
Q-30. Write an SQL query to show records from one table that another table does not have.
Ans.

The required query is:

Query #30
RunShow Solution
SELECT * FROM Worker EXCEPT SELECT * FROM WorkerClone;
SQL query executed successfully!
Details
No records found.

Q-31. Write an SQL query to show the current date and time.
Ans.

The following MySQL query returns the current date:

Query #31
RunShow Solution
SELECT CURRENT_TIMESTAMP;
SQL query executed successfully!
Details
CURRENT_TIMESTAMP
2024-08-01 14:24:05
Q-32. Write an SQL query to show the top n (say 10) records of a table.
Ans.

Specify the SQL query in the below code box:

Ezoic
Query #32
RunShow Solution
SELECT *
FROM Worker
ORDER BY SALARY DESC  -- Order by salary in descending order to get the highest salaries first
LIMIT 10;             -- Limit the result to the top 10 records
SQL query executed successfully!
Details
WORKER_ID	FIRST_NAME	LAST_NAME	SALARY	JOINING_DATE	DEPARTMENT
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

Q-33. Write an SQL query to determine the nth (say n=5) highest salary from a table.
Ans.

MySQL query to find the nth highest salary:

Ezoic
Query #33
RunShow Solution
SELECT DISTINCT SALARY
FROM Worker
ORDER BY SALARY DESC
LIMIT 1 OFFSET 4;
SQL query executed successfully!
Details
SALARY
90000
SQL Server query to find the nth highest salary:

SELECT TOP 1 Salary
FROM (
 SELECT DISTINCT TOP n Salary
 FROM Worker 
 ORDER BY Salary DESC
 )
ORDER BY Salary ASC;
Copy
Q-34. Write an SQL query to determine the 5th highest salary without using the TOP or limit method.
Ans.

The following query is using the correlated subquery to return the 5th highest salary:

Query #34
RunShow Solution
SELECT Salary FROM Worker W1 WHERE 4 = (SELECT COUNT(DISTINCT W2.Salary) FROM Worker W2 WHERE W2.Salary >= W1.Salary);
SQL query executed successfully!
Details
SALARY
100000
Use the following generic method to find the nth highest salary without using TOP or limit.

SELECT Salary
FROM Worker W1
WHERE n-1 = (
 SELECT COUNT( DISTINCT ( W2.Salary ) )
 FROM Worker W2
 WHERE W2.Salary >= W1.Salary
 );
Copy
Q-35. Write an SQL query to fetch the list of employees with the same salary.
Ans.

The required query is:

Ezoic
Query #35
RunShow Solution
SELECT distinct W.WORKER_ID, W.FIRST_NAME, W.Salary from Worker W, Worker W1 where W.Salary = W1.Salary and W.WORKER_ID != W1.WORKER_ID;
SQL query executed successfully!
Details
WORKER_ID	FIRST_NAME	SALARY
4	Amitabh	500000
5	Vivek	500000
Q-36. Write an SQL query to show the second-highest salary from a table.
Ans.

The required query is:

Query #36
RunShow Solution
SELECT max(Salary) from Worker where Salary not in (Select max(Salary) from Worker);
SQL query executed successfully!
Details
max(Salary)
300000
Q-37. Write an SQL query to show one row twice in the results from a table.
Ans.

Ezoic
The required query is:

Query #37
RunShow Solution
SELECT FIRST_NAME, DEPARTMENT from Worker W where W.DEPARTMENT='HR' union all select FIRST_NAME, DEPARTMENT from Worker W1 where W1.DEPARTMENT='HR';
SQL query executed successfully!
Details
FIRST_NAME	DEPARTMENT
Monika	HR
Vishal	HR
Monika	HR
Vishal	HR
Q-38. Write an SQL query to fetch intersecting records of two tables.
Ans.

The required query is:

Query #38
RunShow Solution
-- Note:
--       You Must Run Query #28
--       Both Tables Must Have Same Structure.

-- SQLite and MySQL compatible syntax
SELECT * FROM Worker
INTERSECT
SELECT * FROM WorkerClone;

-- SQLite and MySQL compatible syntax
SELECT w.*
FROM Worker w
INNER JOIN WorkerClone wc ON w.WORKER_ID = wc.WORKER_ID;
SQL query executed successfully!
Details
WORKER_ID	FIRST_NAME	LAST_NAME	SALARY	JOINING_DATE	DEPARTMENT
1	Monika	Arora	100000	2021-02-20 09:00:00	HR
2	Niharika	Verma	80000	2021-06-11 09:00:00	Admin
3	Vishal	Singhal	300000	2021-02-20 09:00:00	HR
4	Amitabh	Singh	500000	2021-02-20 09:00:00	Admin
5	Vivek	Bhati	500000	2021-06-11 09:00:00	Admin
6	Vipul	Diwan	200000	2021-06-11 09:00:00	Account
7	Satish	Kumar	75000	2021-01-20 09:00:00	Account
8	Geetika	Chauhan	90000	2021-04-11 09:00:00	Admin
WORKER_ID	FIRST_NAME	LAST_NAME	SALARY	JOINING_DATE	DEPARTMENT
1	Monika	Arora	100000	2021-02-20 09:00:00	HR
2	Niharika	Verma	80000	2021-06-11 09:00:00	Admin
3	Vishal	Singhal	300000	2021-02-20 09:00:00	HR
4	Amitabh	Singh	500000	2021-02-20 09:00:00	Admin
5	Vivek	Bhati	500000	2021-06-11 09:00:00	Admin
6	Vipul	Diwan	200000	2021-06-11 09:00:00	Account
7	Satish	Kumar	75000	2021-01-20 09:00:00	Account
8	Geetika	Chauhan	90000	2021-04-11 09:00:00	Admin
Q-39. Write an SQL query to fetch the first 50% of records from a table.
Ans.

The required query is:

Query #39
RunShow Solution
SELECT * FROM WORKER WHERE WORKER_ID <= (SELECT count(WORKER_ID)/2 from Worker);
SQL query executed successfully!
Details
WORKER_ID	FIRST_NAME	LAST_NAME	SALARY	JOINING_DATE	DEPARTMENT
1	Monika	Arora	100000	2021-02-20 09:00:00	HR
2	Niharika	Verma	80000	2021-06-11 09:00:00	Admin
3	Vishal	Singhal	300000	2021-02-20 09:00:00	HR
4	Amitabh	Singh	500000	2021-02-20 09:00:00	Admin
Practicing SQL query interview questions is a great way to improve your understanding of the language and become more proficient in SQL. In addition to improving your technical skills, practicing SQL query questions can help you advance your career. Many employers seek candidates with strong SQL skills, so demonstrating your proficiency can get you a competitive edge.

Ezoic
Q-40. Write an SQL query to fetch the departments that have less than five people in them.
Ans.

The required query is:

Query #40
RunShow Solution
SELECT DEPARTMENT, COUNT(WORKER_ID) as 'Number of Workers' FROM Worker GROUP BY DEPARTMENT HAVING COUNT(WORKER_ID) < 5;
SQL query executed successfully!
Details
DEPARTMENT	Number of Workers
Account	2
Admin	4
HR	2
Q-41. Write an SQL query to show all departments along with the number of people in there.
Ans.

Ezoic
The following query returns the expected result:

Query #41
RunShow Solution
SELECT DEPARTMENT, COUNT(DEPARTMENT) as 'Number of Workers' FROM Worker GROUP BY DEPARTMENT;
SQL query executed successfully!
Details
DEPARTMENT	Number of Workers
Account	2
Admin	4
HR	2
Q-42. Write an SQL query to show the last record from a table.
Ans.

The following query will return the last record from the Worker table:

Query #42
RunShow Solution
Select * from Worker where WORKER_ID = (SELECT max(WORKER_ID) from Worker);

Ezoic
SQL query executed successfully!
Details
WORKER_ID	FIRST_NAME	LAST_NAME	SALARY	JOINING_DATE	DEPARTMENT
8	Geetika	Chauhan	90000	2021-04-11 09:00:00	Admin
Q-43. Write an SQL query to fetch the first row of a table.
Ans.

The required query is:

Query #43
RunShow Solution
Select * from Worker where WORKER_ID = (SELECT min(WORKER_ID) from Worker);
SQL query executed successfully!
Details
WORKER_ID	FIRST_NAME	LAST_NAME	SALARY	JOINING_DATE	DEPARTMENT
1	Monika	Arora	100000	2021-02-20 09:00:00	HR
Q-44. Write an SQL query to fetch the last five records from a table.
Ans.

The required query is:

Query #44
RunShow Solution
-- Solution 1
SELECT * FROM Worker WHERE WORKER_ID <= 5 UNION SELECT * FROM (SELECT * FROM Worker W ORDER BY W.WORKER_ID DESC) AS W1 WHERE W1.WORKER_ID <= 5;

-- Solution 2
SELECT * FROM Worker ORDER BY WORKER_ID DESC LIMIT 5;
SQL query executed successfully!

Ezoic
Details
WORKER_ID	FIRST_NAME	LAST_NAME	SALARY	JOINING_DATE	DEPARTMENT
1	Monika	Arora	100000	2021-02-20 09:00:00	HR
2	Niharika	Verma	80000	2021-06-11 09:00:00	Admin
3	Vishal	Singhal	300000	2021-02-20 09:00:00	HR
4	Amitabh	Singh	500000	2021-02-20 09:00:00	Admin
5	Vivek	Bhati	500000	2021-06-11 09:00:00	Admin
WORKER_ID	FIRST_NAME	LAST_NAME	SALARY	JOINING_DATE	DEPARTMENT
8	Geetika	Chauhan	90000	2021-04-11 09:00:00	Admin
7	Satish	Kumar	75000	2021-01-20 09:00:00	Account
6	Vipul	Diwan	200000	2021-06-11 09:00:00	Account
5	Vivek	Bhati	500000	2021-06-11 09:00:00	Admin
4	Amitabh	Singh	500000	2021-02-20 09:00:00	Admin
Q-45. Write an SQL query to print the names of employees having the highest salary in each department.
Ans.

The required query is:

Query #45
RunShow Solution
SELECT t.DEPARTMENT, t.FIRST_NAME, t.Salary from (SELECT max(Salary) as TotalSalary, DEPARTMENT from Worker group by DEPARTMENT) as TempNew Inner Join Worker t on TempNew.DEPARTMENT = t.DEPARTMENT and TempNew.TotalSalary = t.Salary;
SQL query executed successfully!
Details
DEPARTMENT	FIRST_NAME	SALARY
HR	Vishal	300000
Admin	Amitabh	500000
Admin	Vivek	500000
Account	Vipul	200000
Q-46. Write an SQL query to fetch three max salaries from a table.
Ans.

The required query is:

Query #46
RunShow Solution
SELECT distinct Salary from Worker a WHERE 3 >= (SELECT count(distinct Salary) from Worker b WHERE a.Salary <= b.Salary) order by a.Salary desc;
SQL query executed successfully!
Details
SALARY
500000
300000
200000

Ezoic
Q-47. Write an SQL query to fetch three min salaries from a table.
Ans.

The required query is:

Query #47
RunShow Solution
SELECT distinct Salary from Worker a WHERE 3 >= (SELECT count(distinct Salary) from Worker b WHERE a.Salary >= b.Salary) order by a.Salary desc;
SQL query executed successfully!
Details
SALARY
90000
80000
75000
Q-48. Write an SQL query to fetch nth max salaries from a table.
Ans.

The required query is:

Query #48
RunShow Solution
-- Set the value of n
WITH vars AS (SELECT 5 AS n)
-- Use the variable in a query
SELECT DISTINCT Salary FROM Worker a WHERE (SELECT n FROM vars) >= (SELECT COUNT(DISTINCT Salary) FROM Worker b WHERE a.Salary <= b.Salary) ORDER BY a.Salary DESC;
SQL query executed successfully!
Details
SALARY
500000
300000
200000
100000
90000
Q-49. Write an SQL query to fetch departments along with the total salaries paid for each of them.
Ans.

Ezoic
The required query is:

Query #49
RunShow Solution
SELECT DEPARTMENT, sum(Salary) from Worker group by DEPARTMENT;
SQL query executed successfully!
Details
DEPARTMENT	sum(Salary)
Account	275000
Admin	1170000
HR	400000
Q-50. Write an SQL query to fetch the names of workers who earn the highest salary.
Ans.

The required query is:

Query #50
RunShow Solution
SELECT FIRST_NAME, SALARY from Worker WHERE SALARY=(SELECT max(SALARY) from Worker);
SQL query executed successfully!
Details
FIRST_NAME	SALARY
Amitabh	500000
Vivek	500000
