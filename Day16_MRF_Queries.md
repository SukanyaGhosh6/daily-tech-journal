# Day 16: SQL Revision – MRF Queries

This document covers beginner-friendly SQL queries focused on retrieving employee data from a sample `EMP` table. It includes aggregate functions, filtering with `WHERE`, pattern matching with `LIKE`, and usage of logical operators.

---

## 📋 EMP Table Overview (Assumed Schema for Reference)

| Column Name | Data Type | Description                   |
|-------------|-----------|-------------------------------|
| EMPNO       | INT       | Employee Number               |
| ENAME       | VARCHAR   | Employee Name                 |
| JOB         | VARCHAR   | Job Role                      |
| MGR         | INT       | Manager ID                    |
| HIREDATE    | DATE      | Date of Hiring                |
| SAL         | FLOAT     | Salary                        |
| COMM        | FLOAT     | Commission                    |
| DEPTNO      | INT       | Department Number             |

---

## 🔍 SQL Queries

| No. | Query Description                                                                                      | SQL Statement |
|-----|----------------------------------------------------------------------------------------------------------|---------------|
| 1   | Number of employees getting salary less than 2000 in deptno 10                                          | `SELECT COUNT(*), DEPTNO FROM EMP WHERE SAL < 2000 AND DEPTNO = 10;` |
| 2   | Total salary needed to pay employees working as CLERK                                                   | `SELECT SUM(SAL) FROM EMP WHERE JOB = 'CLERK';` |
| 3   | Average salary needed to pay all employees                                                              | `SELECT AVG(SAL) FROM EMP;` |
| 4   | Number of employees having 'A' as the first character in their name                                     | `SELECT COUNT(*) FROM EMP WHERE ENAME LIKE 'A%';` |
| 5   | Number of employees working as CLERK or MANAGER                                                         | `SELECT COUNT(*) FROM EMP WHERE JOB IN ('CLERK', 'MANAGER');` |
| 6   | Total salary of employees hired in the month of February                                                | `SELECT SUM(SAL) FROM EMP WHERE HIREDATE LIKE '%FEB%';` |
| 7   | Number of employees reporting to manager with ID 7839                                                   | `SELECT COUNT(*) FROM EMP WHERE MGR = 7839;` |
| 8   | Number of employees getting commission in deptno 30                                                     | `SELECT COUNT(*) FROM EMP WHERE COMM IS NOT NULL AND DEPTNO = 30;` |
| 9   | Average, total, count, and max salary of employees working as PRESIDENT                                 | `SELECT AVG(SAL), SUM(SAL), COUNT(*), MAX(SAL) FROM EMP WHERE JOB = 'PRESIDENT';` |
| 10  | Number of employees having 'A' anywhere in their name                                                   | `SELECT COUNT(*) FROM EMP WHERE ENAME LIKE '%A%';` |
| 11  | Number and total salary of employees who have two consecutive 'L's in their names                       | `SELECT COUNT(*), SUM(SAL) FROM EMP WHERE ENAME LIKE '%LL%';` |
| 12  | Number of departments present in the employee table (assuming DEPT column)                              | `SELECT COUNT(DEPT) FROM EMP;` |
| 13  | Number of employees having 'Z' in their names                                                           | `SELECT COUNT(*) FROM EMP WHERE ENAME LIKE '%Z%';` |
| 14  | Number of employees having '$' in their names                                                           | `SELECT COUNT(*) FROM EMP WHERE ENAME LIKE '%$%';` |
| 15  | Total salary given to CLERKs in department 30                                                           | `SELECT SUM(SAL) FROM EMP WHERE JOB = 'CLERK' AND DEPTNO = 30;` |
| 16  | Maximum salary of employees working as ANALYST                                                          | `SELECT MAX(SAL) FROM EMP WHERE JOB = 'ANALYST';` |
| 17  | Number of distinct salaries in the employee table                                                       | `SELECT COUNT(DISTINCT SAL) FROM EMP;` |
| 18  | Number of jobs listed in the employee table                                                             | `SELECT COUNT(JOB) FROM EMP;` |
| 19  | Average salary given to CLERKs                                                                          | `SELECT AVG(SAL) FROM EMP WHERE JOB = 'CLERK';` |
| 20  | Minimum salary of MANAGER or CLERK in department 10                                                     | `SELECT MIN(SAL) FROM EMP WHERE DEPTNO = 10 AND JOB IN ('MANAGER','CLERK');` |

