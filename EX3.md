# EX 3 SubQueries, Views and Joins 
# DATE:
# AIM:
To write SubQueries, Views and Joins queries

## Create employee Table
```sql
CREATE TABLE EMP (EMPNO NUMBER(4) PRIMARY KEY,ENAME VARCHAR2(10),JOB VARCHAR2(9),MGR NUMBER(4),HIREDATE DATE,SAL NUMBER(7,2),COMM NUMBER(7,2),DEPTNO NUMBER(2));
```
## Insert the values
```sql
INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7369, 'SMITH', 'CLERK', 7902, '17-DEC-80', 800, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7499, 'ALLEN', 'SALESMAN', 7698, '20-FEB-81', 1600, 300, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7521, 'WARD', 'SALESMAN', 7698, '22-FEB-81', 1250, 500, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7566, 'JONES', 'MANAGER', 7839, '02-APR-81', 2975, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7654, 'MARTIN', 'SALESMAN', 7698, '28-SEP-81', 1250, 1400, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7698, 'BLAKE', 'MANAGER', 7839, '01-MAY-81', 2850, NULL, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7782, 'CLARK', 'MANAGER', 7839, '09-JUN-81', 2450, NULL, 10);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7788, 'SCOTT', 'ANALYST', 7566, '19-APR-87', 3000, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7839, 'KING', 'PRESIDENT', NULL, '17-NOV-81', 5000, NULL, 10);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7844, 'TURNER', 'SALESMAN', 7698, '08-SEP-81', 1500, 0, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7876, 'ADAMS', 'CLERK', 7788, '23-MAY-87', 1100, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7900, 'JAMES', 'CLERK', 7698, '03-DEC-81', 950, NULL, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7902, 'FORD', 'ANALYST', 7566, TO_DATE('03-DEC-81', 'DD-MON-RR'), 3000, 20, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7934, 'MILLER', 'CLERK', 7782, TO_DATE('23-JAN-82', 'DD-MON-RR'), 1300, 10, 10);
```

## Create department table
```sql
CREATE TABLE DEPT (DEPTNO NUMBER(2) PRIMARY KEY,DNAME VARCHAR2(14),LOC VARCHAR2(13));
```
## Insert the values in the department table
```sql
INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (10, 'ACCOUNTING', 'NEW YORK');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (20, 'RESEARCH', 'DALLAS');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (30, 'SALES', 'CHICAGO');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (40, 'OPERATIONS', 'BOSTON');
```

### Q1) List the name of the employees whose salary is greater than that of employee with empno 7566.


### QUERY:
```
CREATE VIEW details AS SELECT ENAME FROM EMP WHERE SALARY >(select SALARY from EMP where EMPNO=7566);
```
### OUTPUT:
![image](https://github.com/Vaishnavi-saravanan/EX-3-SubQueries-Views-and-Joins/assets/118541897/81dd14fa-c51f-4796-8ef8-493954800c72)

### Q2) List the ename,job,sal of the employee who get minimum salary in the company.

### QUERY:
```
CREATE VIEW minimum AS select ENAME,JOB,SALARY from EMP where SALARY =(select MIN(SALARY) from EMP);
```
### OUTPUT:
![image](https://github.com/Vaishnavi-saravanan/EX-3-SubQueries-Views-and-Joins/assets/118541897/b6e26b99-2531-4dae-bb1f-c2da9d5a6a2f)

### Q3) List ename, job of the employees who work in deptno 10 and his/her job is any one of the job in the department ‘SALES’.

### QUERY:
```
select ENAME,JOB from EMP where DEPTNO=10 AND JOB='SALESMAN';
```
### OUTPUT:
![image](https://github.com/Vaishnavi-saravanan/EX-3-SubQueries-Views-and-Joins/assets/118541897/5e79f800-b6b2-43fb-8bcb-5f9a3874835c)


### Q4) Create a view empv5 (for the table emp) that contains empno, ename, job of the employees who work in dept 10.

### QUERY:
```
create view empv5 as select EMPNO,ENAME,JOB from EMP where DEPTNO=10;
```
### OUTPUT:
![image](https://github.com/Vaishnavi-saravanan/EX-3-SubQueries-Views-and-Joins/assets/118541897/cfb0ef74-71d4-4942-9dfa-81144268dc0f)

### Q5) Create a view with column aliases empv30 that contains empno, ename, sal of the employees who work in dept 30. Also display the contents of the view.

### QUERY:
```
create view empv30 AS select EMPNO,ENAME,SALARY from EMP where DEPTNO=30;
```
### OUTPUT:
![image](https://github.com/Vaishnavi-saravanan/EX-3-SubQueries-Views-and-Joins/assets/118541897/12ba13f8-df88-4e9f-8efd-eaf055e0f8a5)

### Q6) Update the view empv5 by increasing 10% salary of the employees who work as ‘CLERK’. Also confirm the modifications in emp table

### QUERY:
```
update EMP set SALARY=SALARY*1.1 WHERE JOB='clerk';
```
create view empv5 as select EMPNO,ENAME,SALARY,JOB from EMP;

### OUTPUT:
![image](https://github.com/Vaishnavi-saravanan/EX-3-SubQueries-Views-and-Joins/assets/118541897/50dff453-8147-4aba-b0e6-2bca97cf6a02)

## Create a Customer1 Table
```sql
CREATE TABLE Customer1 (customer_id INT,cust_name VARCHAR(20),city VARCHAR(20),grade INT,salesman_id INT);
```
## Inserting Values to the Table
```sql
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3002, 'Nick Rimando', 'New York', 100, 5001);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3007, 'Brad Davis', 'New York', 200, 5001);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3005, 'Graham Zusi', 'California', 200, 5002);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3008, 'Julian Green', 'London', 300, 5002);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3004, 'Fabian Johnson', 'Paris', 300, 5006);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3009, 'Geoff Cameron', 'Berlin', 100, 5003);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3003, 'Jozy Altidor', 'Moscow', 200, 5007);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3001, 'Brad Guzan', 'London', NULL, 5005);
```
## Create a Salesperson1 table
```sql
CREATE TABLE Salesman1 (salesman_id INT,name VARCHAR(20),city VARCHAR(20),commission DECIMAL(4,2));
```
## Inserting Values to the Table
```sql
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5001, 'James Hoog', 'New York', 0.15);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5002, 'Nail Knite', 'Paris', 0.13);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5005, 'Pit Alex', 'London', 0.11);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5006, 'Mc Lyon', 'Paris', 0.14);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5007, 'Paul Adam', 'Rome', 0.13);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5003, 'Lauson Hen', 'San Jose', 0.12);
```
### Q7) Write a SQL query to find the salesperson and customer who reside in the same city. Return Salesman, cust_name and city.

### QUERY:
```
select s.name,c.cust_name,s.city from salesman1 as s ,customer1 as c where s.city=c.city;
```
### OUTPUT:
![image](https://github.com/Vaishnavi-saravanan/EX-3-SubQueries-Views-and-Joins/assets/118541897/e54dd6ef-529e-48d0-98ec-b015da039fa1)

### Q8) Write a SQL query to find salespeople who received commissions of more than 13 percent from the company. Return Customer Name, customer city, Salesman, commission.


### QUERY:
```
select s.name,c.cust_name,c.city,s.commission from salesman1 as s inner join customer1 as c on s.city=c.city where s.commission>0.13;
```
### OUTPUT:
![image](https://github.com/Vaishnavi-saravanan/EX-3-SubQueries-Views-and-Joins/assets/118541897/2f07505b-2465-48d2-9956-b5cfbdf898f3)

### Q9) Perform Natural join on both tables

### QUERY:
```
select s.name,c.cust_name,c.city,s.commission from salesman1 as s natural join customer1 as c where s.commission>0.13;
```
### OUTPUT:
![image](https://github.com/Vaishnavi-saravanan/EX-3-SubQueries-Views-and-Joins/assets/118541897/c0bd364c-f8ec-4c8a-a4d2-6b6a6de0faea)

### Q10) Perform Left and right join on both tables

### QUERY:
```
select s.name,c.cust_name,c.city,s.commission from salesman1 as s left join customer1 as c on s.salesman_id=c.salesman_id where s.commission>0.13;

select s.name,c.cust_name,c.city,s.commission from salesman1 as s right join customer1 as c on s.salesman_id=c.salesman_id where s.commission>0.13;
```
### OUTPUT:
![image](https://github.com/Vaishnavi-saravanan/EX-3-SubQueries-Views-and-Joins/assets/118541897/30169ade-f1af-4270-bfb5-8ebd27161f76)

### RESULT:
Hence successfully created a manager database and execute DML queries using SQL.
