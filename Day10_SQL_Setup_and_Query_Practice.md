# Day 10: Finally Set Up SQL*Plus — And Practiced Some Core Queries!

So today was mostly spent wrangling with SQL installations again. I had actually installed **SQL Server** on my laptop around 3 years ago during college, but I hadn’t touched it in a while. And now that I’ve been revisiting SQL for my full stack learning, I wanted to get **Oracle SQL*Plus** up and running.

It wasn’t smooth at first.  
I had some leftover Oracle services, missing environment variables, and random error popups like "SP2-0152: Oracle may not be functioning properly"... But after uninstalling everything, resetting environment variables, and doing a clean install of **Oracle 21c XE**, everything finally clicked.

And once it worked — I celebrated by writing a bunch of queries. Nothing too crazy, just brushing up on the basics with the classic `EMP` and `DEPT` tables.

Here’s the list of queries I practiced:

---

##  Core SQL Queries Practiced Today

```sql
-- 1. Display all details from the EMPLOYEE table
SELECT * FROM EMP;

-- 2. Names of all the employees
SELECT ENAME FROM EMP;

-- 3. Name and salary of all the employees
SELECT ENAME, SAL FROM EMP;

-- 4. Name and commission of all the employees
SELECT ENAME, COMM FROM EMP;

-- 5. Employee ID and department number of all the employees
SELECT EMPNO, DEPTNO FROM EMP;

-- 6. Name and hire date of all the employees
SELECT ENAME, HIREDATE FROM EMP;

-- 7. Name and designation of all the employees
SELECT ENAME, JOB FROM EMP;

-- 8. Name, job, and salary of all the employees
SELECT ENAME, JOB, SAL FROM EMP;

-- 9. Department names from the DEPT table
SELECT DNAME FROM DEPT;

-- 10. Department name and location from the DEPT table
SELECT DNAME, LOC FROM DEPT;

-- 11. Name of the employee along with their annual salary
SELECT ENAME, SAL * 12 AS ANNUAL_SALARY FROM EMP;

-- 12. Ename and job for all employees with their half-term salary
SELECT ENAME, JOB, SAL * 6 AS HALF_TERM_SALARY FROM EMP;

-- 13. All employee details along with an annual bonus of 2000
SELECT *, 2000 AS ANNUAL_BONUS FROM EMP;

-- 14. Name, salary, and salary with a hike of 10%
SELECT ENAME, SAL, SAL * 1.10 AS SALARY_WITH_HIKE FROM EMP;

-- 15. Name and salary with a deduction of 25%
SELECT ENAME, SAL * 0.75 AS SALARY_AFTER_DEDUCTION FROM EMP;

-- 16. Name and salary with a monthly hike of 50
SELECT ENAME, SAL + 50 AS SALARY_WITH_MONTHLY_HIKE FROM EMP;

-- 17. Name and annual salary with deduction of 10%
SELECT ENAME, SAL * 12 * 0.90 AS ANNUAL_SALARY_WITH_DEDUCTION FROM EMP;

-- 18. Total salary for each employee (SAL + COMM)
SELECT ENAME, SAL + NVL(COMM, 0) AS TOTAL_SALARY FROM EMP;

-- 19. All employee details with annual salary
SELECT EMP.*, SAL * 12 AS ANNUAL_SALARY FROM EMP;
```

---

##  Notes From This Session

- `NVL()` is super useful to handle null values (especially in `COMM`)
- I had forgotten how powerful even a simple `SELECT` can be when you add conditions, calculations, or aliases
- It felt great to see the queries working after so much setup frustration 

---

##  What's Next?

I’ll probably explore `WHERE` clauses, filters, conditions, and maybe try my hand at **JOINS** again. And I think it’s also time to create my own sample tables soon to play with actual data.

This one was less about learning new queries and more about just **getting the environment ready** and **feeling comfortable again inside SQL\*Plus**.

It feels good to be back in it.

