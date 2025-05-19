# Day 24 — SQL Recall: Pattern Matching & String-Based Conditions

Today was a solid revisit of SQL string functions and pattern matching — the kind of stuff that looks easy but gets tricky when you actually sit down to solve real-world queries. These types of assignments always bring back the feeling of brushing off rust and rediscovering how powerful basic string functions can be.

Here’s a breakdown of some of the scenarios I worked through today:

---

**1. List employees whose name has exactly 4 characters.**

```sql
SELECT * FROM EMP WHERE LENGTH(ENAME) = 4;
````

The `LENGTH()` function came in handy. It simply counts the number of characters in the string.

---

**2. List employees whose job title is exactly 7 characters.**

```sql
SELECT * FROM EMP WHERE LENGTH(JOB) = 7;
```

A lot of people overlook job titles like "ANALYST" or "MANAGER" — perfect 7-char candidates.

---

**3. Count how many times letter 'S' appears in 'QSPIDERS'.**

```sql
SELECT LENGTH('QSPIDERS') - LENGTH(REPLACE('QSPIDERS', 'S', '')) AS S_COUNT FROM DUAL;
```

A classic problem. Here, the trick is to remove all the 'S' characters and compare the length difference.

---

**4. List employees whose job ends with 'MAN'.**

```sql
SELECT * FROM EMP WHERE JOB LIKE '%MAN';
```

The `%` is like "anything before" — perfect for suffix-based filters.

---

**5. List employees whose job starts with 'MAN'.**

```sql
SELECT * FROM EMP WHERE JOB LIKE 'MAN%';
```

Same idea, just reversed — looking for prefixes now.

---

**6. Display names with exactly one 'L'.**

```sql
SELECT * FROM EMP WHERE LENGTH(ENAME) - LENGTH(REPLACE(ENAME, 'L', '')) = 1;
```

This is honestly a neat trick. Comparing lengths pre- and post-replacement tells you the character count.

---

**7. Department names with letter 'O'.**

```sql
SELECT * FROM DEPT WHERE DNAME LIKE '%O%';
```

A good reminder that LIKE isn’t just for employee data — it’s handy across tables.

---

**8. Count of 'L' in 'HELLLLL'.**

```sql
SELECT LENGTH('HELLLLL') - LENGTH(REPLACE('HELLLLL', 'L', '')) AS L_COUNT FROM DUAL;
```

Again, just a solid string trick. I’ll probably use this again in interview prep.

---

**9. Employees whose job contains 'MAN'.**

```sql
SELECT * FROM EMP WHERE JOB LIKE '%MAN%';
```

---

**10. Employees whose job starts with 'MAN'.**

```sql
SELECT * FROM EMP WHERE JOB LIKE 'MAN%';
```

---

**11. Employees whose job ends with 'MAN'.**

```sql
SELECT * FROM EMP WHERE JOB LIKE '%MAN';
```

---

**12. Lowercase first 3 characters of `ENAME`, rest in uppercase.**

```sql
SELECT LOWER(SUBSTR(ENAME,1,3)) || UPPER(SUBSTR(ENAME,4)) AS FORMATTED_NAME FROM EMP;
```

Surprisingly fun to play around with this. Splitting the string and formatting chunks differently.

---

**13. Show a literal sentence: "SMITH is a CLERK and gets salary 2000".**

```sql
SELECT ENAME || ' is a ' || JOB || ' and gets salary ' || SAL AS DESCRIPTION FROM EMP;
```

Loved this one. It’s like turning SQL into a little storytelling tool.

---

**14. Employees hired on a Wednesday.**

```sql
SELECT * FROM EMP WHERE TO_CHAR(HIREDATE, 'DY') = 'WED';
```

---

**15. Employees hired in a leap year.**

```sql
SELECT * FROM EMP WHERE MOD(TO_NUMBER(TO_CHAR(HIREDATE, 'YYYY')), 4) = 0;
```

This might not cover the full leap year logic (like 100 and 400 rules), but it’s a good approximation.

---

**16. Employees hired on a Sunday in May.**

```sql
SELECT * FROM EMP WHERE TO_CHAR(HIREDATE, 'DY') = 'SUN' AND TO_CHAR(HIREDATE, 'MM') = '05';
```

---

**17. Names that end with 'H'.**

```sql
SELECT * FROM EMP WHERE ENAME LIKE '%H';
```

---

**18. Name, salary, and hiredate of employees whose name starts with 'J'.**

```sql
SELECT ENAME, SAL, HIREDATE FROM EMP WHERE ENAME LIKE 'J%';
```

---

**19. Names and job of employees who have 'A' at least twice in their name.**

```sql
SELECT ENAME, JOB FROM EMP 
WHERE LENGTH(ENAME) - LENGTH(REPLACE(ENAME, 'A', '')) >= 2;
```

---

**20. Names and job of employees whose name starts with a vowel.**

```sql
SELECT ENAME, JOB FROM EMP WHERE ENAME LIKE 'A%' OR ENAME LIKE 'E%' 
OR ENAME LIKE 'I%' OR ENAME LIKE 'O%' OR ENAME LIKE 'U%';
```

---

### Reflections

It was a nice session to recall the small but mighty features of SQL — especially string manipulation and LIKE patterns. These are deceptively simple but play a crucial role in real data wrangling, reports, or even small cleanup scripts. Good reminder that getting your hands dirty with examples always beats theoretical cramming.

Tomorrow, I might shift gears a bit — maybe revisit some SQL joins or subqueries or touch on triggers and views. Let’s see what clicks.


