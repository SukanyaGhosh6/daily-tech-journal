# Day 21 – SQL Recalling: Multi Join Conditions Assignment

As part of my daily tech journal, today I tackled a set of challenging multi-join queries using the classic SCOTT schema. These queries helped reinforce my skills in SQL joins, filtering conditions, and working with hierarchical employee-manager relationships.

---

##  EMP Table (Reference Snapshot)

This is the data used for today's queries based on the SCOTT schema:

| empno | ename  | job       | mgr  | hiredate   | sal   | comm  | deptno |
|-------|--------|-----------|------|------------|-------|-------|--------|
| 7369  | SMITH  | CLERK     | 7902 | 1980-12-17 | 800   | NULL  | 20     |
| 7499  | ALLEN  | SALESMAN  | 7698 | 1981-02-20 | 1600  | 300   | 30     |
| 7521  | WARD   | SALESMAN  | 7698 | 1981-02-22 | 1250  | 500   | 30     |
| 7566  | JONES  | MANAGER   | 7839 | 1981-04-02 | 2975  | NULL  | 20     |
| 7698  | BLAKE  | MANAGER   | 7839 | 1981-05-01 | 2850  | NULL  | 30     |
| 7782  | CLARK  | MANAGER   | 7839 | 1981-06-09 | 2450  | NULL  | 10     |
| 7788  | SCOTT  | ANALYST   | 7566 | 1987-04-19 | 3000  | NULL  | 20     |
| 7839  | KING   | PRESIDENT | NULL | 1981-11-17 | 5000  | NULL  | 10     |
| 7844  | TURNER | SALESMAN  | 7698 | 1981-08-20 | 1500  | 0     | 30     |
| 7876  | ADAMS  | CLERK     | 7788 | 1987-05-23 | 1100  | NULL  | 20     |
| 7900  | JAMES  | CLERK     | 7698 | 1981-12-03 | 950   | NULL  | 30     |
| 7902  | FORD   | ANALYST   | 7566 | 1981-12-03 | 3000  | NULL  | 20     |
| 7934  | MILLER | CLERK     | 7782 | 1982-01-23 | 1300  | NULL  | 10     |

---

##  SQL Multi Join Assignment – With Queries & Solutions

### 1. ENAME, MGR’s SAL, and EMP LOC for those in NEW YORK with 4-digit salary
```sql
SELECT e.ename, m.sal AS mgr_sal, d.loc
FROM emp e
JOIN emp m ON e.mgr = m.empno
JOIN dept d ON e.deptno = d.deptno
WHERE d.loc = 'NEW YORK' AND e.sal BETWEEN 1000 AND 9999;
````

---

### 2. ENAME, MGR, HIREDATE, and MGR’s COMM if ENAME starts with 'S' or 'J'

```sql
SELECT e.ename, e.mgr, e.hiredate, m.comm
FROM emp e
JOIN emp m ON e.mgr = m.empno
WHERE e.ename LIKE 'S%' OR e.ename LIKE 'J%';
```

---

### 3. EMP JOB, MGR HIREDATE, and MGR DEPT NAME for MGR hired after 1980 in ACCOUNTING/RESEARCH

```sql
SELECT e.job, m.hiredate, d.dname
FROM emp e
JOIN emp m ON e.mgr = m.empno
JOIN dept d ON m.deptno = d.deptno
WHERE m.hiredate > '1980-01-01' AND d.dname IN ('ACCOUNTING', 'RESEARCH');
```

---

### 4. ENAME, MGR ENAME, and DNAME if EMP SAL > 1000 and MGR works in SALES

```sql
SELECT e.ename, m.ename AS mgr_name, d.dname
FROM emp e
JOIN emp m ON e.mgr = m.empno
JOIN dept d ON m.deptno = d.deptno
WHERE e.sal > 1000 AND d.dname = 'SALES';
```

---

### 5. ENAME, MGR NAME, and EMP’s LOC for all CLERKs

```sql
SELECT e.ename, m.ename AS mgr_name, d.loc
FROM emp e
JOIN emp m ON e.mgr = m.empno
JOIN dept d ON e.deptno = d.deptno
WHERE e.job = 'CLERK';
```

---

### 6. ENAME, MANAGER SAL, and MGR LOC if MGR is PRESIDENT

```sql
SELECT e.ename, m.sal AS mgr_sal, d.loc
FROM emp e
JOIN emp m ON e.mgr = m.empno
JOIN dept d ON m.deptno = d.deptno
WHERE m.job = 'PRESIDENT';
```

---

### 7. ENAME, EMP SAL, MGR NAME, MGR SAL, and EMP DNAME if EMP earns more than MGR

```sql
SELECT e.ename, e.sal, m.ename AS mgr_name, m.sal AS mgr_sal, d.dname
FROM emp e
JOIN emp m ON e.mgr = m.empno
JOIN dept d ON e.deptno = d.deptno
WHERE e.sal > m.sal;
```

---

### 8. ENAME, EMP SAL, MGR’s NAME, and MGR’s DNAME if MGR is in NEW YORK and SAL > 3000

```sql
SELECT e.ename, e.sal, m.ename AS mgr_name, d.dname
FROM emp e
JOIN emp m ON e.mgr = m.empno
JOIN dept d ON m.deptno = d.deptno
WHERE d.loc = 'NEW YORK' AND m.sal > 3000;
```

---

### 9. ENAME, EMP HIREDATE, MGR HIREDATE where MGR hired before EMP in ACCOUNTING

```sql
SELECT e.ename, e.hiredate, m.hiredate AS mgr_hiredate
FROM emp e
JOIN emp m ON e.mgr = m.empno
JOIN dept d ON e.deptno = d.deptno
WHERE d.dname = 'ACCOUNTING' AND m.hiredate < e.hiredate;
```

---

### 10. ENAME, MGR NAME, and MGR’s MGR NAME

```sql
SELECT e.ename, m.ename AS mgr_name, mm.ename AS mgr_mgr_name
FROM emp e
JOIN emp m ON e.mgr = m.empno
JOIN emp mm ON m.mgr = mm.empno;
```

---

### 11. ENAME, DNAME, MGR NAME, and MGR DNAME if MGR hired before 1982

```sql
SELECT e.ename, d1.dname, m.ename AS mgr_name, d2.dname AS mgr_dname
FROM emp e
JOIN emp m ON e.mgr = m.empno
JOIN dept d1 ON e.deptno = d1.deptno
JOIN dept d2 ON m.deptno = d2.deptno
WHERE m.hiredate < '1982-01-01';
```

---

### 12. ENAME with DNAME, MGR with LOC, MGR’s MGR NAME with LOC

```sql
SELECT e.ename, d1.dname AS emp_dname, 
       m.ename AS mgr_name, d2.loc AS mgr_loc,
       mm.ename AS mgr_mgr_name, d3.loc AS mgr_mgr_loc
FROM emp e
JOIN emp m ON e.mgr = m.empno
JOIN emp mm ON m.mgr = mm.empno
JOIN dept d1 ON e.deptno = d1.deptno
JOIN dept d2 ON m.deptno = d2.deptno
JOIN dept d3 ON mm.deptno = d3.deptno;
```

---

### 13. ENAME with DNAME, MGR SAL with DNAME, MGR’s MGR JOB with DNAME (complex join)

```sql
SELECT e.ename, d1.dname AS emp_dname,
       m.sal AS mgr_sal, d2.dname AS mgr_dname,
       mm.job AS mgr_mgr_job, d3.dname AS mgr_mgr_dname
FROM emp e
JOIN emp m ON e.mgr = m.empno
JOIN emp mm ON m.mgr = mm.empno
JOIN dept d1 ON e.deptno = d1.deptno
JOIN dept d2 ON m.deptno = d2.deptno
JOIN dept d3 ON mm.deptno = d3.deptno
WHERE e.deptno = 10
  AND m.job IN ('PRESIDENT', 'ACTUAL MANAGER')
  AND mm.sal >= m.sal;
```

---

### 14. ENAME, EMP DNAME, MGR NAME, MGR DNAME if both work in the same LOC

```sql
SELECT e.ename, d1.dname AS emp_dname, 
       m.ename AS mgr_name, d2.dname AS mgr_dname
FROM emp e
JOIN emp m ON e.mgr = m.empno
JOIN dept d1 ON e.deptno = d1.deptno
JOIN dept d2 ON m.deptno = d2.deptno
WHERE d1.loc = d2.loc;
```

---

##  Reflection

This practice session pushed me to understand how to structure layered joins, perform subqueries with conditions, and follow multi-level reporting hierarchies. Revisiting SCOTT schema has proven very effective for deep SQL recall.


