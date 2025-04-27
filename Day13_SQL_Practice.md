#  Day 13 - SQL Practice Journey

Hey everyone!  
Today was a power-packed day of SQL practice.  
I worked mainly with `WHERE` clauses, logical operators, and special operators.  
I also created two basic employee tables to test all the queries.

Let's dive into everything I practiced today:

---

## Setting Up The Tables

First, I created two simple tables: `employee1` and `employee2`.  
Here’s what they looked like:

### Table: `employee1`

| eid | ename  | deptno |
|:---:|:------:|:------:|
| 1   | Smith  | 10     |
| 2   | Allen  | 20     |
| 3   | King   | 40     |
| 4   | Turner | 60     |
| 5   | Scott  | 10     |

### Table: `employee2`

| empno | ename  | salary | job        |
|:-----:|:------:|:------:|:----------:|
| 1     | Smith  | 80000  | Salesman   |
| 2     | Allen  | 40000  | Clerk      |
| 3     | King   | 1000000| Testing    |
| 4     | John   | 35000  | CEO        |
| 5     | Deb    | 300000 | Developer  |

---

# 🧠 SQL Assignments I Practiced

## 1. Special Operators Assignment

Here are the questions and the queries I practiced:

---

**Q1. List all the employees whose commission is NULL.**

```sql
SELECT * FROM EMP WHERE COMM IS NULL;
```

---

**Q2. List all the employees who don’t have a reporting manager.**

```sql
SELECT * FROM EMP WHERE MGR IS NULL;
```

---

**Q3. List all the salesmen in Dept 30.**

```sql
SELECT * FROM EMP WHERE JOB='SALESMAN' AND DEPTNO=30;
```

---

**Q4. List all the salesmen in Dept 30 and having salary greater than 1500.**

```sql
SELECT * FROM EMP WHERE JOB='SALESMAN' AND DEPTNO=30 AND SAL > 1500;
```

---

**Q5. List all the employees whose name starts with 'S' or 'A'.**

```sql
SELECT * FROM EMP WHERE ENAME LIKE 'S%' OR ENAME LIKE 'A%';
```

---

**Q6. List all the employees except those working in Dept 10 & 20.**

```sql
SELECT * FROM EMP WHERE DEPTNO NOT IN (10, 20);
```

---

**Q7. List the employees whose name does NOT start with 'S'.**

```sql
SELECT * FROM EMP WHERE ENAME NOT LIKE 'S%';
```

---

**Q8. List all the employees having reporting managers in Dept 10.**

```sql
SELECT * FROM EMP WHERE MGR IN (SELECT EMPNO FROM EMP WHERE DEPTNO=10);
```

---

**Q9. List all the employees whose commission is NULL and working as clerk.**

```sql
SELECT * FROM EMP WHERE COMM IS NULL AND JOB='CLERK';
```

---

**Q10. List all employees without a reporting manager in Dept 10 or 30.**

```sql
SELECT * FROM EMP WHERE MGR IS NULL AND (DEPTNO=10 OR DEPTNO=30);
```

---

**Q11. List all the salesmen in Dept 30 with salary more than 2450.**

```sql
SELECT * FROM EMP WHERE JOB='SALESMAN' AND DEPTNO=30 AND SAL>2450;
```

---

**Q12. List all the analysts in Dept 20 with salary greater than 2500.**

```sql
SELECT * FROM EMP WHERE JOB='ANALYST' AND DEPTNO=20 AND SAL>2500;
```

---

**Q13. List all employees whose name starts with 'M' or 'J'.**

```sql
SELECT * FROM EMP WHERE ENAME LIKE 'M%' OR ENAME LIKE 'J%';
```

---

**Q14. List all employees with annual salary except those working in Dept 30.**

```sql
SELECT ENAME, SAL*12 AS ANNUAL_SAL FROM EMP WHERE DEPTNO != 30;
```

---

**Q15. List employees whose name does not end with 'ES' or 'R'.**

```sql
SELECT * FROM EMP WHERE ENAME NOT LIKE '%ES' AND ENAME NOT LIKE '%R';
```

---

**Q16. List employees with reporting managers in Dept 10 along with 10% hike in salary.**

```sql
SELECT ENAME, SAL, SAL*1.10 AS HIKE_SAL FROM EMP WHERE MGR IN (SELECT EMPNO FROM EMP WHERE DEPTNO=10);
```

---

**Q17. Display salesmen having 'E' as second-last character and salary with exactly 4 digits.**

```sql
SELECT * FROM EMP WHERE JOB='SALESMAN' AND ENAME LIKE '%E_' AND SAL BETWEEN 1000 AND 9999;
```

---

**Q18. Display employees who joined after year '81.**

```sql
SELECT * FROM EMP WHERE HIREDATE > TO_DATE('31-DEC-1981','DD-MON-YYYY');
```

---

**Q19. Display employees who joined in February.**

```sql
SELECT * FROM EMP WHERE TO_CHAR(HIREDATE,'MM') = '02';
```

---

**Q20. List employees NOT working as Manager and Clerk in Dept 10 and 20 with salary between 1000 and 3000.**

```sql
SELECT * FROM EMP WHERE JOB NOT IN ('MANAGER','CLERK') AND DEPTNO IN (10,20) AND SAL BETWEEN 1000 AND 3000;
```

---

## 2. WHERE Clause Assignment

---

**Q1. Annual salary of employee named 'SMITH'.**

```sql
SELECT SAL*12 AS ANNUAL_SAL FROM EMP WHERE ENAME='SMITH';
```

---

**Q2. Names of employees working as Clerk.**

```sql
SELECT ENAME FROM EMP WHERE JOB='CLERK';
```

---

**Q3. Salary of employees working as Salesman.**

```sql
SELECT SAL FROM EMP WHERE JOB='SALESMAN';
```

---

**Q4. Details of employees earning more than 2000.**

```sql
SELECT * FROM EMP WHERE SAL>2000;
```

---

**Q5. Details of employee named 'JONES'.**

```sql
SELECT * FROM EMP WHERE ENAME='JONES';
```

---

**Q6. Details of employees hired after 1-Jan-81.**

```sql
SELECT * FROM EMP WHERE HIREDATE > '01-JAN-81';
```

---

**Q7. Name and salary with annual salary if annual salary > 12000.**

```sql
SELECT ENAME, SAL, SAL*12 AS ANNUAL_SAL FROM EMP WHERE SAL*12>12000;
```

---

**Q8. Empno of employees in Dept 30.**

```sql
SELECT EMPNO FROM EMP WHERE DEPTNO=30;
```

---

**Q9. Name and Hiredate if hired before 1981.**

```sql
SELECT ENAME, HIREDATE FROM EMP WHERE HIREDATE<'01-JAN-1981';
```

---

**Q10. Details of employees working as Manager.**

```sql
SELECT * FROM EMP WHERE JOB='MANAGER';
```

---

**Q11. Name and salary of employees earning commission = 1400.**

```sql
SELECT ENAME, SAL FROM EMP WHERE COMM=1400;
```

---

**Q12. Employees with commission more than salary.**

```sql
SELECT * FROM EMP WHERE COMM>SAL;
```

---

**Q13. Empno of employees hired before 1987.**

```sql
SELECT EMPNO FROM EMP WHERE HIREDATE<'01-JAN-1987';
```

---

**Q14. Employees working as Analyst.**

```sql
SELECT * FROM EMP WHERE JOB='ANALYST';
```

---

**Q15. Employees earning more than 2000.**

```sql
SELECT * FROM EMP WHERE SAL>2000;
```

---

## 3. Logical Operators Assignment

---

**Q1. Clerks earning less than 1500.**

```sql
SELECT * FROM EMP WHERE JOB='CLERK' AND SAL<1500;
```

---

**Q2. Managers in Dept 30 with their hiredate.**

```sql
SELECT ENAME, HIREDATE FROM EMP WHERE JOB='MANAGER' AND DEPTNO=30;
```

---

**Q3. Salesmen in Dept 30 with annual salary greater than 14000.**

```sql
SELECT EMP.*, SAL*12 AS ANNUAL_SAL FROM EMP WHERE DEPTNO=30 AND JOB='SALESMAN' AND SAL*12>14000;
```

---

**Q4. Employees working in Dept 30 or as Analyst.**

```sql
SELECT * FROM EMP WHERE DEPTNO=30 OR JOB='ANALYST';
```

---

**Q5. Clerks earning less than 1100.**

```sql
SELECT ENAME FROM EMP WHERE SAL<1100 AND JOB='CLERK';
```

---

_(...and so on, following the same format up to Q20 of Logical Operators...)_

---

# Final Thoughts

Today’s session gave me a lot of hands-on practice with:

- **NULL checks**
- **Pattern Matching (LIKE, NOT LIKE)**
- **Range searches (BETWEEN)**
- **Logical combination of conditions (AND, OR, NOT)**

Honestly, writing all these queries manually really helped in remembering the syntax and understanding the flow of SQL better.  
Feeling much more confident now.

see ya tomorrow!!
