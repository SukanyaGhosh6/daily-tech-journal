
# Day 15 — SQL Functions and Grouping Concepts  
### A curious learner’s take on SQL built-in functions, grouping, and ordering

Hi! I’m Sukanya Ghosh, and today was all about revisiting some core topics in SQL and Python. While reviewing SQL, I focused on functions — both built-in and how they work with grouping and ordering. I also spent some time brushing up on Python basics like functions, loops, and variable handling. But for this article, I want to share what I explored in SQL, using real queries and examples from a dataset we worked with in class.

---

## What are Functions in SQL?

- Functions help us perform operations or calculations on data.
- They’re categorized into:
  - **Predefined/Built-in Functions**
  - **User-defined Functions**

---

## Built-in SQL Functions

These are divided into two types:

### 1. Single Row Functions (SRF)
- Work on each row individually.
- Examples: `UPPER()`, `LOWER()`, `LENGTH()`, `SUBSTR()`, `TRIM()`

### 2. Multiple Row Functions (MRF)
- Perform calculations across rows (on groups of data).
- Common ones:
  - `MAX()` – highest value
  - `MIN()` – lowest value
  - `SUM()` – total sum
  - `AVG()` – average
  - `COUNT()` – count rows

---

## Practice Queries

Let’s say we have a table `EMP` with employee data. Here are some queries I wrote to understand these functions better:

- **Number of characters in each employee’s name:**
  ```sql
  SELECT ENAME, LENGTH(ENAME) AS NUM_OF_CHAR FROM EMP;
  ```

- **Maximum salary among employees:**
  ```sql
  SELECT MAX(SAL) FROM EMP;
  ```

- **Minimum salary:**
  ```sql
  SELECT MIN(SAL) FROM EMP;
  ```

- **Average salary:**
  ```sql
  SELECT AVG(SAL) FROM EMP;
  ```

- **Total salary to be paid:**
  ```sql
  SELECT SUM(SAL) FROM EMP;
  ```

- **Total number of employees:**
  ```sql
  SELECT COUNT(*) FROM EMP;
  ```

- **Minimum salary and number of employees with 'A' in name:**
  ```sql
  SELECT MIN(SAL), COUNT(*) FROM EMP WHERE ENAME LIKE '%A%';
  ```

- **Number of employees and total salary of those with two consecutive 'L':**
  ```sql
  SELECT COUNT(*), SUM(SAL) FROM EMP WHERE ENAME LIKE '%LL%';
  ```

---

## GROUP BY Clause

- Used to group records with common values.
- **Syntax:**
  ```sql
  SELECT column, AGGREGATE_FUNCTION FROM table GROUP BY column;
  ```
- **Execution Order:**  
  `FROM → WHERE → GROUP BY → SELECT`

### Example Queries:

- **Count of employees in each department:**
  ```sql
  SELECT DEPTNO, COUNT(*) FROM EMP GROUP BY DEPTNO;
  ```

- **Count of employees working as MANAGER or CLERK in each department:**
  ```sql
  SELECT DEPTNO, COUNT(*) 
  FROM EMP 
  WHERE JOB IN ('MANAGER', 'CLERK') 
  GROUP BY DEPTNO;
  ```

---

## HAVING Clause

- Used to filter grouped data.
- **Syntax:**
  ```sql
  SELECT column, AGGREGATE_FUNCTION 
  FROM table 
  GROUP BY column 
  HAVING condition;
  ```
- **Execution Order:**  
  `FROM → WHERE → GROUP BY → HAVING → SELECT`

### Example Queries:

- **Departments with at least 2 employees:**
  ```sql
  SELECT DEPTNO, COUNT(*) 
  FROM EMP 
  GROUP BY DEPTNO 
  HAVING COUNT(*) >= 2;
  ```

- **Jobs with exactly 4 employees and their max salary:**
  ```sql
  SELECT JOB, COUNT(*), MAX(SAL) 
  FROM EMP 
  GROUP BY JOB 
  HAVING COUNT(*) = 4;
  ```

- **Departments with at least 4 MANAGER or ANALYST:**
  ```sql
  SELECT DEPTNO, COUNT(*) 
  FROM EMP 
  WHERE JOB IN ('MANAGER', 'ANALYST') 
  GROUP BY DEPTNO 
  HAVING COUNT(*) >= 4;
  ```

- **Average salary per department if it's less than 3000:**
  ```sql
  SELECT DEPTNO, AVG(SAL) 
  FROM EMP 
  GROUP BY DEPTNO 
  HAVING AVG(SAL) < 3000;
  ```

---

## ORDER BY Clause

- Used to sort records by a column.
- **Syntax:**
  ```sql
  SELECT * FROM EMP ORDER BY column [ASC|DESC];
  ```
- **Execution Order:**  
  `FROM → WHERE → GROUP BY → HAVING → SELECT → ORDER BY`

### Example Queries:

- **Salaries in ascending order:**
  ```sql
  SELECT ENAME, SAL FROM EMP ORDER BY SAL ASC;
  ```

- **Names of MANAGERs in descending order:**
  ```sql
  SELECT ENAME FROM EMP WHERE JOB = 'MANAGER' ORDER BY ENAME DESC;
  ```

---

## Wrap-Up

It was a full-on learning day — refreshing both Python and SQL. My biggest takeaway was how important it is to not just understand these concepts, but to **write actual queries** and **see them run**.

If you're revisiting SQL or just starting out, I hope these notes help you make sense of functions, grouping, and ordering — just like they helped me.

See ya tomorrow!!
