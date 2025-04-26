# Day 12: SQL Operators, Special Operators, and Fun Query Practice

## Introduction

Today I decided to slow down and nicely revisit one of the most important topics in SQL — **Operators**.  
At the same time, I created a small sample table and solved a bunch of beginner-level queries based on it.  
Honestly, practicing like this is helping me remember things faster without getting bored.

Here’s everything I revised today, along with small examples and explanations.

---

## EMP Table Setup

To make things simple, I created this mini EMP table in my mind:

| EMPNO | ENAME  | SALARY | JOB          |
|------|--------|--------|--------------|
| 1    | SMITH  | 80K    | SALESMAN     |
| 2    | ALLEN  | 40K    | CLERK        |
| 3    | KING   | 1CR    | TEST ENGINEER|
| 4    | JOHN   | 35K    | CEO          |
| 5    | DEB    | 3LK    | DEVELOPER    |

---

## Quick Queries Solved

**1. Display names of employees earning more than 80K:**

```sql
SELECT ENAME 
FROM EMP 
WHERE SALARY > 80000;
```

**2. Display names of employees earning less than 80K:**

```sql
SELECT ENAME 
FROM EMP 
WHERE SALARY < 80000;
```

**3. Display name and annual salary of employees hired after 1981:**

(Assuming there's a `HIREDATE` column.)

```sql
SELECT ENAME, SALARY*12 AS Annual_Salary 
FROM EMP 
WHERE HIREDATE > '1981-12-31';
```

**4. Display details of employees working as Manager:**

```sql
SELECT * 
FROM EMP 
WHERE JOB = 'MANAGER';
```

---

## Operators Revised Today

1. **Arithmetic Operators:** `+`, `-`, `*`, `/`
2. **Comparison Operators:** `>`, `<`, `>=`, `<=`, `=`, `!=`
3. **Relational Operators:** (Comparison operators fall here.)
4. **Concatenation Operator:** `||` (joins two strings)

Example:

```sql
SELECT ENAME || ' has salary ' || SALARY 
FROM EMP;
```

5. **Logical Operators:**
   - **AND**
   - **OR**
   - **NOT**

6. **Special Operators:**
   - **IN**
   - **NOT IN**
   - **BETWEEN**
   - **NOT BETWEEN**
   - **IS NULL**
   - **IS NOT NULL**
   - **LIKE**
   - **NOT LIKE**

7. **Subquery Operators:**
   - **ALL**
   - **ANY**
   - **EXISTS**
   - **NOT EXISTS**

---

## More Query Practice

**5. Display annual bonus of employees (assuming bonus = 2 months' salary):**

```sql
SELECT ENAME, (SALARY/12)*2 AS Annual_Bonus 
FROM EMP;
```

**6. Concatenation Operator Example:**

Display "Hii ENAME your salary is:"

```sql
SELECT 'Hii ' || ENAME || ' your salary is ' || SALARY 
FROM EMP;
```

---

## Logical Operator Based Queries

**7. Display details of employees earning 2000 and working in dept 20:**

```sql
SELECT * 
FROM EMP 
WHERE SALARY = 2000 AND DEPTNO = 20;
```

**8. Display details of employees working in dept 10 or dept 20:**

```sql
SELECT * 
FROM EMP 
WHERE DEPTNO = 10 OR DEPTNO = 20;
```

**9. Display details of employees except those earning salary 2000:**

```sql
SELECT * 
FROM EMP 
WHERE SALARY != 2000;
```

**10. Display details of employees working as SALESMAN in dept 30 earning less than 5000:**

```sql
SELECT ENAME, SALARY, JOB, DEPTNO 
FROM EMP 
WHERE JOB = 'SALESMAN' 
AND DEPTNO = 30 
AND SALARY < 5000;
```

---

## Special Operator Based Queries

**11. IN Operator**

Display employees working in dept 10, 20, 30, 50, 60, 80:

```sql
SELECT * 
FROM EMP 
WHERE DEPTNO IN (10, 20, 30, 50, 60, 80);
```

**12. NOT IN Operator**

Display employees who are Manager or Analyst, but not in certain depts:

```sql
SELECT * 
FROM EMP 
WHERE JOB IN ('MANAGER', 'ANALYST') 
AND DEPTNO NOT IN (10, 20, 30);
```

**13. BETWEEN Operator**

Display employees earning between 2000 and 5000:

```sql
SELECT ENAME 
FROM EMP 
WHERE SALARY BETWEEN 2000 AND 5000;
```

**14. NOT BETWEEN Operator**

Display employees earning salary outside 2000 to 3000 range:

```sql
SELECT ENAME, SALARY 
FROM EMP 
WHERE SALARY NOT BETWEEN 2000 AND 3000;
```

**15. IS NULL Operator**

Display employees not earning any commission:

```sql
SELECT ENAME 
FROM EMP 
WHERE COMM IS NULL;
```

**16. IS NOT NULL Operator**

Display employees who are earning some commission:

```sql
SELECT * 
FROM EMP 
WHERE COMM IS NOT NULL;
```

---

## LIKE Operator Practice

**17. Name starts with 'A':**

```sql
SELECT ENAME 
FROM EMP 
WHERE ENAME LIKE 'A%';
```

**18. Name ends with 'A':**

```sql
SELECT ENAME 
FROM EMP 
WHERE ENAME LIKE '%A';
```

**19. Employees working as ANALYST and earning a 4-digit salary:**

```sql
SELECT * 
FROM EMP 
WHERE JOB = 'ANALYST' 
AND SALARY BETWEEN 1000 AND 9999;
```

---

## NOT LIKE Operator Practice

**20. Display employees whose name does NOT start with 'A':**

```sql
SELECT ENAME 
FROM EMP 
WHERE ENAME NOT LIKE 'A%';
```

---

## Final Thoughts

Today's revision was quite fun because instead of memorizing syntax like a robot, I created a mini EMP table in my mind and solved different types of queries on it.  
This method made operators feel more real and practical, and it honestly didn't feel boring at all.  

see you tomorrow!!
