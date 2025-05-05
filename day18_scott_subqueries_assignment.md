# Day 18 – SQL Subqueries & Joins Practice (SCOTT Schema)

##  SCOTT Schema Overview

For this assignment, I used the classic **SCOTT schema**, which consists of two core tables:

### EMP Table – Employee Information

| Column   | Data Type | Description                   |
|----------|-----------|-------------------------------|
| EMPNO    | NUMBER    | Employee Number (PK)          |
| ENAME    | VARCHAR   | Employee Name                 |
| JOB      | VARCHAR   | Job Title                     |
| MGR      | NUMBER    | Manager's EMPNO               |
| HIREDATE | DATE      | Date of Hiring                |
| SAL      | NUMBER    | Salary                        |
| COMM     | NUMBER    | Commission (nullable)         |
| DEPTNO   | NUMBER    | Department Number (FK to DEPT)|

### DEPT Table – Department Information

| Column | Data Type | Description             |
|--------|-----------|-------------------------|
| DEPTNO | NUMBER    | Department Number (PK)  |
| DNAME  | VARCHAR   | Department Name         |
| LOC    | VARCHAR   | Department Location     |

---

##  SQL Assignments Using Subqueries & Joins

##Case 2

1. **DNAME of the employee whose name is SMITH**
```sql
SELECT DNAME
FROM DEPT
WHERE DEPTNO = (SELECT DEPTNO FROM EMP WHERE ENAME = 'SMITH');
````

2. **DNAME and LOC of the employee whose name is KING**

```sql
SELECT DNAME, LOC
FROM DEPT
WHERE DEPTNO = (SELECT DEPTNO FROM EMP WHERE ENAME = 'KING');
```

3. **LOC of the employee whose EMPNO is 7902**

```sql
SELECT LOC
FROM DEPT
WHERE DEPTNO = (SELECT DEPTNO FROM EMP WHERE EMPNO = 7902);
```

4. **DNAME, LOC, and DEPTNO of the employee whose name ends with 'R'**

```sql
SELECT DNAME, LOC, DEPT.DEPTNO
FROM DEPT
WHERE DEPT.DEPTNO IN (
    SELECT DEPTNO FROM EMP WHERE ENAME LIKE '%R'
);
```

5. **DNAME of the employee whose JOB is 'PRESIDENT'**

```sql
SELECT DNAME
FROM DEPT
WHERE DEPTNO = (
    SELECT DEPTNO FROM EMP WHERE JOB = 'PRESIDENT'
);
```

6. **Names of employees working in the ACCOUNTING department**

```sql
SELECT ENAME
FROM EMP
WHERE DEPTNO = (
    SELECT DEPTNO FROM DEPT WHERE DNAME = 'ACCOUNTING'
);
```

7. **ENAME and SAL of employees working in CHICAGO**

```sql
SELECT ENAME, SAL
FROM EMP
WHERE DEPTNO = (
    SELECT DEPTNO FROM DEPT WHERE LOC = 'CHICAGO'
);
```

8. **Details of employees working in SALES**

```sql
SELECT *
FROM EMP
WHERE DEPTNO = (
    SELECT DEPTNO FROM DEPT WHERE DNAME = 'SALES'
);
```

9. **Employee details and annual salary if working in NEW YORK**

```sql
SELECT EMP.*, SAL * 12 AS ANNUAL_SAL
FROM EMP
WHERE DEPTNO = (
    SELECT DEPTNO FROM DEPT WHERE LOC = 'NEW YORK'
);
```

10. **Names of employees working in OPERATIONS department**

```sql
SELECT ENAME
FROM EMP
WHERE DEPTNO = (
    SELECT DEPTNO FROM DEPT WHERE DNAME = 'OPERATIONS'
);
```

---

### CASE 1 QUERIES

1. **Employees earning more than SCOTT in ACCOUNTING**

```sql
SELECT ENAME
FROM EMP
WHERE SAL > (
    SELECT SAL FROM EMP WHERE ENAME = 'SCOTT'
)
AND DEPTNO = (
    SELECT DEPTNO FROM DEPT WHERE DNAME = 'ACCOUNTING'
);
```

2. **Details of employees working as MANAGER in CHICAGO**

```sql
SELECT *
FROM EMP
WHERE JOB = 'MANAGER'
AND DEPTNO = (
    SELECT DEPTNO FROM DEPT WHERE LOC = 'CHICAGO'
);
```

3. **ENAME and SAL of employees earning more than KING in ACCOUNTING**

```sql
SELECT ENAME, SAL
FROM EMP
WHERE SAL > (
    SELECT SAL FROM EMP WHERE ENAME = 'KING'
)
AND DEPTNO = (
    SELECT DEPTNO FROM DEPT WHERE DNAME = 'ACCOUNTING'
);
```

4. **Details of SALESMAN working in SALES**

```sql
SELECT *
FROM EMP
WHERE JOB = 'SALESMAN'
AND DEPTNO = (
    SELECT DEPTNO FROM DEPT WHERE DNAME = 'SALES'
);
```

5. **ENAME, SAL, JOB, HIREDATE of employees in OPERATIONS hired before KING**

```sql
SELECT ENAME, SAL, JOB, HIREDATE
FROM EMP
WHERE DEPTNO = (
    SELECT DEPTNO FROM DEPT WHERE DNAME = 'OPERATIONS'
)
AND HIREDATE < (
    SELECT HIREDATE FROM EMP WHERE ENAME = 'KING'
);
```

6. **All employees whose department name ends with 'S'**

```sql
SELECT ENAME
FROM EMP
WHERE DEPTNO IN (
    SELECT DEPTNO FROM DEPT WHERE DNAME LIKE '%S'
);
```

7. **DNAME of employees whose names contain the character 'A'**

```sql
SELECT DISTINCT DNAME
FROM DEPT
WHERE DEPTNO IN (
    SELECT DEPTNO FROM EMP WHERE ENAME LIKE '%A%'
);
```

8. **DNAME and LOC of employees whose salary is 800**

```sql
SELECT DNAME, LOC
FROM DEPT
WHERE DEPTNO IN (
    SELECT DEPTNO FROM EMP WHERE SAL = 800
);
```

9. **DNAME of employees who earn commission**

```sql
SELECT DISTINCT DNAME
FROM DEPT
WHERE DEPTNO IN (
    SELECT DEPTNO FROM EMP WHERE COMM IS NOT NULL
);
```

10. **LOC of employees who earn commission in DEPT 40**

```sql
SELECT LOC
FROM DEPT
WHERE DEPTNO = 40
AND DEPTNO IN (
    SELECT DEPTNO FROM EMP WHERE COMM IS NOT NULL
);
```

---

##  Summary

Today’s focus was on applying subqueries and joins using the SCOTT schema to extract detailed employee and department data. These exercises really helped reinforce filtering logic, especially using subqueries in `WHERE` clauses. Writing readable and efficient SQL felt more natural by the end of the session.

