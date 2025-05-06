#  Day 19 – SQL Practice with Nested Subqueries

Welcome to **Day 19** of our SQL learning journey! 🚀 Today, we dive deep into **nested subqueries**, one of the most powerful tools in SQL when you want to extract specific data based on conditions related to aggregates, order, or even multiple tables.

Let’s go through 10 practical queries one by one — all focused on **employee and department** data — and solve them using **nested subqueries**.

---

##  Assumptions

We're working with two main tables:

* **EMP** (with columns: `EMPNO`, `ENAME`, `SAL`, `HIREDATE`, `DEPTNO`)
* **DEPT** (with columns: `DEPTNO`, `DNAME`, `LOC`)

---

### 1. WAQTD 2nd Minimum Salary

```sql
SELECT MIN(SAL) 
FROM EMP 
WHERE SAL > (SELECT MIN(SAL) FROM EMP);
```

 *Explanation*: We first find the **minimum salary**, then fetch the **next higher salary**, which is effectively the **2nd minimum**.

---

### 2. WAQTD 5th Maximum Salary

```sql
SELECT MIN(SAL) 
FROM (
  SELECT DISTINCT SAL 
  FROM EMP 
  ORDER BY SAL DESC 
  FETCH FIRST 5 ROWS ONLY
) AS TOP5;
```

 *Explanation*: We use a subquery to sort and fetch the top 5 salaries, then grab the **minimum** of those — i.e., the **5th highest salary**.

---

### 3. WAQTD Name of the Employee Earning 3rd Maximum Salary

```sql
SELECT ENAME 
FROM EMP 
WHERE SAL = (
  SELECT MIN(SAL) 
  FROM (
    SELECT DISTINCT SAL 
    FROM EMP 
    ORDER BY SAL DESC 
    FETCH FIRST 3 ROWS ONLY
  ) AS TOP3
);
```

 *Explanation*: Similar approach as above, but instead of just the salary, we fetch the employee(s) **with that exact salary**.

---

### 4. WAQTD EMPNO of the Employee Earning 2nd Maximum Salary

```sql
SELECT EMPNO 
FROM EMP 
WHERE SAL = (
  SELECT MAX(SAL) 
  FROM EMP 
  WHERE SAL < (
    SELECT MAX(SAL) FROM EMP
  )
);
```

 *Explanation*: We go one step below the max salary and grab the employee number tied to that.

---

### 5. WAQTD Department Name of an Employee Getting 4th Max Salary

```sql
SELECT D.DNAME 
FROM EMP E 
JOIN DEPT D ON E.DEPTNO = D.DEPTNO 
WHERE E.SAL = (
  SELECT MIN(SAL) 
  FROM (
    SELECT DISTINCT SAL 
    FROM EMP 
    ORDER BY SAL DESC 
    FETCH FIRST 4 ROWS ONLY
  ) AS TOP4
);
```

 *Explanation*: Join with `DEPT` to extract the **department name** for the employee with the **4th highest salary**.

---

### 6. WAQTD Details of the Employee Who Was Hired 2nd

```sql
SELECT * 
FROM EMP 
WHERE HIREDATE = (
  SELECT MIN(HIREDATE) 
  FROM EMP 
  WHERE HIREDATE > (
    SELECT MIN(HIREDATE) FROM EMP
  )
);
```

 *Explanation*: Get the **second earliest hire date**, then pull the full employee details.

---

### 7. WAQTD Name of the Employee Hired Before the Last Employee

```sql
SELECT ENAME 
FROM EMP 
WHERE HIREDATE = (
  SELECT MAX(HIREDATE) 
  FROM EMP 
  WHERE HIREDATE < (
    SELECT MAX(HIREDATE) FROM EMP
  )
);
```

 *Explanation*: Get the **hire date just before the most recent one**, and then fetch the name(s).

---

### 8. WAQTD Location of the Employee Who Was Hired First

```sql
SELECT D.LOC 
FROM EMP E 
JOIN DEPT D ON E.DEPTNO = D.DEPTNO 
WHERE E.HIREDATE = (
  SELECT MIN(HIREDATE) FROM EMP
);
```

 *Explanation*: Join with the department table to get the **location** for the **earliest hired employee**.

---

### 9. WAQTD Details of the Employee Earning 3rd Minimum Salary

```sql
SELECT * 
FROM EMP 
WHERE SAL = (
  SELECT MAX(SAL) 
  FROM (
    SELECT DISTINCT SAL 
    FROM EMP 
    ORDER BY SAL ASC 
    FETCH FIRST 3 ROWS ONLY
  ) AS LOW3
);
```

 *Explanation*: Extract the **3rd lowest salary**, then fetch the full employee data for that salary.

---

### 10. WAQTD DNAME of Employee Getting 2nd Maximum Salary

```sql
SELECT D.DNAME 
FROM EMP E 
JOIN DEPT D ON E.DEPTNO = D.DEPTNO 
WHERE E.SAL = (
  SELECT MAX(SAL) 
  FROM EMP 
  WHERE SAL < (SELECT MAX(SAL) FROM EMP)
);
```

 *Explanation*: One level down from the top salary, and a join to fetch the **department name**.

---

##  Summary

Nested subqueries are a powerful way to isolate data based on aggregate logic like "Nth highest/lowest" or temporal conditions like "hired second." They’re especially useful when ranking or filtering data without relying on analytic functions.


