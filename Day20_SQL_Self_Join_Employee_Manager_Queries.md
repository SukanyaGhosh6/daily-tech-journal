#  Day 20: SQL Self Join & EMP-MANAGER Relationship Queries

Today, I revised some foundational and important SQL queries based on the **EMP table (Scott schema)**. These queries are essential for understanding how **self joins** work and how to extract relationships between employees and their managers.

---

## 🗂 EMP Table Structure (Scott Table)

Here's the sample `EMP` table used in the examples:

| empno | ename  | job       | mgr  | hiredate   | sal  | comm | deptno |
| ----- | ------ | --------- | ---- | ---------- | ---- | ---- | ------ |
| 7369  | SMITH  | CLERK     | 7902 | 1980-12-17 | 800  | NULL | 20     |
| 7499  | ALLEN  | SALESMAN  | 7698 | 1981-02-20 | 1600 | 300  | 30     |
| 7521  | WARD   | SALESMAN  | 7698 | 1981-02-22 | 1250 | 500  | 30     |
| 7566  | JONES  | MANAGER   | 7839 | 1981-04-02 | 2975 | NULL | 20     |
| 7698  | BLAKE  | MANAGER   | 7839 | 1981-05-01 | 2850 | NULL | 30     |
| 7782  | CLARK  | MANAGER   | 7839 | 1981-06-09 | 2450 | NULL | 10     |
| 7788  | SCOTT  | ANALYST   | 7566 | 1987-04-19 | 3000 | NULL | 20     |
| 7839  | KING   | PRESIDENT | NULL | 1981-11-17 | 5000 | NULL | 10     |
| 7844  | TURNER | SALESMAN  | 7698 | 1981-09-08 | 1500 | 0    | 30     |
| 7876  | ADAMS  | CLERK     | 7788 | 1987-05-23 | 1100 | NULL | 20     |
| 7900  | JAMES  | CLERK     | 7698 | 1981-12-03 | 950  | NULL | 30     |
| 7902  | FORD   | ANALYST   | 7566 | 1981-12-03 | 3000 | NULL | 20     |
| 7934  | MILLER | CLERK     | 7782 | 1982-01-23 | 1300 | NULL | 10     |

---

##  Part 1: EMPLOYEE - MANAGER Relationship Queries

1. **SMITH's Reporting Manager Name**

```sql
SELECT e.ename AS Employee, m.ename AS Manager 
FROM emp e 
JOIN emp m ON e.mgr = m.empno 
WHERE e.ename = 'SMITH';
```

2. **ADAMS's Manager's Manager Name**

```sql
SELECT m2.ename AS Manager_of_Manager 
FROM emp e 
JOIN emp m1 ON e.mgr = m1.empno 
JOIN emp m2 ON m1.mgr = m2.empno 
WHERE e.ename = 'ADAMS';
```

3. **Department Name of JONES's Manager**

```sql
SELECT d.dname 
FROM emp e 
JOIN emp m ON e.mgr = m.empno 
JOIN dept d ON m.deptno = d.deptno 
WHERE e.ename = 'JONES';
```

4. **MILLER’s Manager's Salary**

```sql
SELECT m.sal 
FROM emp e 
JOIN emp m ON e.mgr = m.empno 
WHERE e.ename = 'MILLER';
```

5. **Location of SMITH’s Manager’s Manager**

```sql
SELECT d.loc 
FROM emp e 
JOIN emp m1 ON e.mgr = m1.empno 
JOIN emp m2 ON m1.mgr = m2.empno 
JOIN dept d ON m2.deptno = d.deptno 
WHERE e.ename = 'SMITH';
```

6. **Employees Reporting to BLAKE**

```sql
SELECT ename 
FROM emp 
WHERE mgr = (SELECT empno FROM emp WHERE ename = 'BLAKE');
```

7. **Number of Employees Reporting to KING**

```sql
SELECT COUNT(*) 
FROM emp 
WHERE mgr = (SELECT empno FROM emp WHERE ename = 'KING');
```

8. **Details of Employees Reporting to JONES**

```sql
SELECT * 
FROM emp 
WHERE mgr = (SELECT empno FROM emp WHERE ename = 'JONES');
```

9. **Employees Reporting to BLAKE’s Manager**

```sql
SELECT ename 
FROM emp 
WHERE mgr = (
  SELECT mgr 
  FROM emp 
  WHERE ename = 'BLAKE'
);
```

10. **Number of Employees Reporting to FORD’s Manager**

```sql
SELECT COUNT(*) 
FROM emp 
WHERE mgr = (
  SELECT mgr 
  FROM emp 
  WHERE ename = 'FORD'
);
```

---

## 🔗 Part 2: Self-Join Based Queries

1. **Employee and Manager Name (Clerks Only)**

```sql
SELECT e.ename AS Employee, m.ename AS Manager 
FROM emp e 
JOIN emp m ON e.mgr = m.empno 
WHERE e.job = 'CLERK';
```

2. **Employee and Manager's Job (Manager in Dept 10 or 20)**

```sql
SELECT e.ename, m.job 
FROM emp e 
JOIN emp m ON e.mgr = m.empno 
WHERE m.deptno IN (10, 20);
```

3. **Employee and Manager Salary (>2300)**

```sql
SELECT e.ename, m.sal AS Manager_Salary 
FROM emp e 
JOIN emp m ON e.mgr = m.empno 
WHERE e.sal > 2300 AND m.sal > 2300;
```

4. **Employee Name & Manager's Hiredate (Before 1982)**

```sql
SELECT e.ename, m.hiredate 
FROM emp e 
JOIN emp m ON e.mgr = m.empno 
WHERE e.hiredate < '1982-01-01';
```

5. **Employee and Manager’s Comm (Emp: Salesman, Mgr: Dept 30)**

```sql
SELECT e.ename, m.comm 
FROM emp e 
JOIN emp m ON e.mgr = m.empno 
WHERE e.job = 'SALESMAN' AND m.deptno = 30;
```

6. **Employee & Manager Where Employee Earns More**

```sql
SELECT e.ename, m.ename, e.sal, m.sal 
FROM emp e 
JOIN emp m ON e.mgr = m.empno 
WHERE e.sal > m.sal;
```

7. **Employee and Manager Hiredate Where Manager Hired First**

```sql
SELECT e.ename, e.hiredate, m.ename, m.hiredate 
FROM emp e 
JOIN emp m ON e.mgr = m.empno 
WHERE m.hiredate < e.hiredate;
```

8. **Employee and Manager with Same Job**

```sql
SELECT e.ename, m.ename 
FROM emp e 
JOIN emp m ON e.mgr = m.empno 
WHERE e.job = m.job;
```

9. **Employee and Manager Where Manager Is 'MANAGER'**

```sql
SELECT e.ename, m.ename 
FROM emp e 
JOIN emp m ON e.mgr = m.empno 
WHERE m.job = 'MANAGER';
```

10. **Employee, Manager and Their Annual Salary (Emp Dept 10/20, Mgr Higher Salary)**

```sql
SELECT e.ename, m.ename, e.sal*12 AS Emp_Annual, m.sal*12 AS Mgr_Annual 
FROM emp e 
JOIN emp m ON e.mgr = m.empno 
WHERE e.deptno IN (10, 20) AND m.sal > e.sal;
```

11. **Employee and Manager’s Designation**

```sql
SELECT e.ename AS Employee, m.job AS Manager_Job 
FROM emp e 
JOIN emp m ON e.mgr = m.empno;
```

12. **Employees Where Manager’s Salary Ends in 50**

```sql
SELECT e.ename, m.sal 
FROM emp e 
JOIN emp m ON e.mgr = m.empno 
WHERE CAST(m.sal AS VARCHAR) LIKE '%50';
