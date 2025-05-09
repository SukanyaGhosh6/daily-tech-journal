# Day 21 – SQL Recalling: Multi Join Conditions Assignment

Today’s SQL session focused on advanced multi-join queries based on the classic **SCOTT schema**. Below is a list of practical SQL questions designed to strengthen understanding of joins, filters, and conditional logic in SQL queries.

---

##  EMP Table (Reference)

Based on the screenshot, here's the data from the `EMP` table used in the queries:

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

##  Assignment Queries

### 1. Employees working in 'NEW YORK' earning 4-digit salary  
> **Output**: ENAME, MGR's SAL, EMP LOC

---

### 2. Employees whose ENAME starts with 'S' or 'J'  
> **Output**: ENAME, MGR, HIREDATE, MGR's COMM

---

### 3. Managers hired after 1980 working in 'ACCOUNTING' or 'RESEARCH'  
> **Output**: EMP JOB, MGR HIREDATE, MGR DEPT NAME

---

### 4. Employees earning more than 1000, with manager in 'SALES' department  
> **Output**: ENAME, MGR ENAME, Their DNAME

---

### 5. All 'CLERK' employees  
> **Output**: ENAME, MGR NAME, EMP’s LOC

---

### 6. Managers whose job is 'PRESIDENT'  
> **Output**: ENAME, MANAGER SAL, MGR LOC

---

### 7. Employees who earn more than their managers  
> **Output**: ENAME, EMP SAL, MGR’s NAME, MGR’s SAL, EMP DNAME

---

### 8. Managers in 'NEW YORK' with SAL > 3000  
> **Output**: ENAME, EMP SAL, MGR’s NAME, MGR’s DNAME

---

### 9. Employees hired after their managers in the ACCOUNTING department  
> **Output**: ENAME, EMP HIREDATE, MGR’s HIREDATE

---

### 10. Employees with their manager’s and manager’s manager's name  
> **Output**: ENAME, MGR’S NAME, MGR’S MGR NAME

---

### 11. Employees whose manager was hired before 1982  
> **Output**: ENAME, DNAME, MGR’S NAME, MGR’S DNAME

---

### 12. Full hierarchy with locations  
> **Output**: ENAME with DNAME, MGR’s NAME with LOC, MGR’s MGR NAME with LOC

---

### 13. Complex Join with job, salary and department conditions  
> **Output**:  
- ENAME with DNAME  
- MGR’s SAL with DNAME  
- MGR’s MGR’s JOB with DNAME  
> **Condition**:  
- EMP in DEPT 10  
- MGR job = 'PRESIDENT' or 'ACTUAL MANAGER'  
- MGR’s MGR SAL ≥ MGR SAL

---

### 14. Employees and managers working in the same location  
> **Output**: ENAME, EMP DNAME, MGR’S NAME, MGR’S DNAME

---

##  Reflection

These queries reinforced my understanding of:
- Multi-table joins and aliasing  
- Filtering with aggregate, string, and date conditions  
- Hierarchical employee-manager relationships  
- Logical operator usage (AND/OR) with joins  


