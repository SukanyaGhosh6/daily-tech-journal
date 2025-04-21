# Day 7: Getting Started with SQL — History, Core Concepts & E.F. Codd’s Rules

Since I’ve been learning Python Full Stack Development, I figured it was the right time to start revising SQL. After all, databases are a huge part of backend development, and I don’t want to just "know" SQL — I want to really understand it.

Today’s session was all about getting comfortable with SQL from the ground up: where it came from, how it works, what it's used for, and how structured data is actually stored and validated.

---

## A Quick Look Back: Where SQL Came From

SQL wasn’t always called SQL.

In the early 1970s, two IBM engineers — **Raymond Boyce** and **Donald Chamberlin** — developed a language called **SEQUEL** (Structured English Query Language). It was designed to interact with relational databases.

Later, in **1986**, the **American National Standards Institute (ANSI)** adopted the language and standardized it as **SQL** — and that’s the version we use today in almost every tech stack involving databases.

---

## So, What is SQL — Really?

SQL (Structured Query Language) is a special language used to manage and interact with databases.

In simpler words:
> SQL helps us store, retrieve, and organize structured data.

---

### Scenario:
Imagine I’m building a school management system. I’d use SQL to:
- Add new students
- Update their grades or details
- Delete old records
- Search for students who scored above 90

All of this is done through SQL queries.

---

## Middleware & Backend — Where SQL Fits In

In full-stack development:

- The **backend** is where all the data, logic, and rules live.
- **Middleware** acts as a bridge between the frontend and backend — helping requests get processed properly.

When a user submits a form (say, to register for a course), SQL is used in the backend to save that information into a database.

---

## Key Concepts I Explored Today

- **Data** – Raw information like "Sukanya", 21, "CSE".
- **Raw Fact** – Unprocessed values without context (like 78 or "Red").
- **Attribute** – A column in a table (like `Name` or `Age`).
- **Entity** – A real-world object we’re storing data about (like a Student).
- **Database** – A structured collection of data, stored in a way that’s easy to manage and retrieve.
- **CRUD** – The four basic operations: Create, Read, Update, and Delete.

---

## DBMS vs. RDBMS

### DBMS (Database Management System)
- Stores data in files or flat tables.
- No relation between different tables.

### RDBMS (Relational DBMS)
- Stores data in **tables**.
- Allows **relationships** between tables via keys.

| Feature              | DBMS                        | RDBMS                            |
|---------------------|-----------------------------|----------------------------------|
| Structure            | Files / Flat Tables         | Tables with relationships        |
| Relationships        | Not Supported               | Supported                        |
| Data Consistency     | Less Reliable               | High Data Integrity              |
| Examples             | XML, File-based Systems     | MySQL, PostgreSQL, Oracle        |

---

## Tables, Rows, Columns & Cells

- A **Table** is like a sheet where we store related data.
- A **Row** contains one complete record (like a student).
- A **Column** defines an attribute (like `Roll No`, `Marks`).
- A **Cell** holds a single value where a row and column meet.

---

## E.F. Codd’s Rules (1 to 4)

These rules define what a proper **relational database** should follow. Today, I learned about the first four rules:

###  Rule 1: Data in Cells Must Be Single-Valued

Each cell in a table should contain only **one value**, not multiple.  
For example:

```sql
-- Good:
Subjects = 'Math'

-- Not good:
Subjects = 'Math, English, Science'  -- ❌ violates Rule 1
```

---

###  Rule 2: Everything Is Stored in Tables

In an RDBMS, even **meta-information** (data about the data) should be stored in tables.  
This makes querying and maintaining the system consistent.

---

###  Rule 3: Data Can Be Stored Across Multiple Tables

You can normalize data by storing it across multiple related tables, and then **connect them using keys**.

### Example:
- `Student` table → student_id, name, class
- `Marks` table → student_id, subject, score

You can use `student_id` as a **foreign key** to connect them.

---

###  Rule 4: Data Must Be Validated in Two Steps

Before inserting data into a table, it should be validated by:

#### 1. **Data Type Validation**
Make sure the value matches the type expected (text, number, date, etc.).

#### 2. **Constraint Validation**
Ensure the value follows rules like:
- `NOT NULL` → value must be present
- `UNIQUE` → no duplicates
- `PRIMARY KEY` → must be unique + not null

---

## SQL Data Types I Learned Today

These are the main data types used in RDBMS systems like Oracle, MySQL, and PostgreSQL:

### 1. `CHAR(n)`
Stores **fixed-length** strings.

```sql
name CHAR(10)  -- Always reserves 10 spaces
```

If you insert `'abc'`, it becomes `'abc       '`.

---

### 2. `VARCHAR(n)` / `VARCHAR2(n)`
Stores **variable-length** strings.

```sql
email VARCHAR(50)
```

Stores only what’s needed — no extra space.

---

### 3. `DATE`
Used to store date values.

```sql
dob DATE
```

Can store dates like `'2024-04-21'`.

---

### 4. `NUMBER(p, s)`
Used to store numbers with precision (`p`) and scale (`s`).

```sql
price NUMBER(6, 2)  -- Up to 6 digits, 2 after the decimal
```

So, `9999.99` is valid, but `1234567.89` is not.

---

## Real-World Example

Let’s say I’m building an inventory table for an e-commerce app:

```sql
CREATE TABLE Product (
    product_id NUMBER(5),
    name VARCHAR(50),
    price NUMBER(6, 2),
    launch_date DATE
);
```

Here:
- Each field has a **specific data type**
- Later, I’ll add **constraints** to ensure data is valid

---

## Final Thoughts

Today’s session gave me a clearer understanding of how relational databases work behind the scenes. I now see that SQL is not just about writing queries — it’s about building **clean, structured, validated systems** for storing important information.

These four rules alone already show how disciplined RDBMS systems are:

- Each value should be **simple and single**
- Everything is stored as **tables**
- We can spread data across **multiple connected tables**
- Every value must be **validated before storage**

Let's keep Learning :D
