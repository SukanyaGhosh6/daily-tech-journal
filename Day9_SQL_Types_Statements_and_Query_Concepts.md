# Day 9: SQL Statement Types, SELECT Queries, and Core Operations

Today’s SQL revision felt like diving into the "grammar" of SQL — where every command has a category, and every operation has a purpose. I explored the **five major types of SQL statements**, plus four of the most important query concepts: **SELECT**, **PROJECTION**, **SELECTION**, and **JOINS**.

Let’s go over what I learned — explained in the way I understood it.

---

## The 5 Types of SQL Statements (Command Categories)

SQL commands are grouped into 5 types, depending on what they do with the data or structure of the database.

---

### 1. DDL – Data Definition Language

These statements define or change the structure of a database. Think of them like architecture blueprints.

- **CREATE** – Makes a new table or database  
- **ALTER** – Changes structure (like adding/removing columns)  
- **DROP** – Deletes a table or database  
- **TRUNCATE** – Deletes all records but keeps the structure  

#### Scenario:
Let’s say I want to create a table for storing book data.

```sql
CREATE TABLE Books (
    id INT PRIMARY KEY,
    title VARCHAR(100),
    author VARCHAR(50)
);
```

---

### 2. DML – Data Manipulation Language

This is all about the actual data — adding, updating, or deleting records inside a table.

- **INSERT** – Add a new row  
- **UPDATE** – Modify existing data  
- **DELETE** – Remove data from the table  

#### Scenario:
```sql
INSERT INTO Books (id, title, author)
VALUES (1, 'The Alchemist', 'Paulo Coelho');
```

---

### 3. DQL – Data Query Language

There’s only one major command here — **SELECT**. It's used to fetch data from one or more tables.

We’ll talk about SELECT in detail below.

---

### 4. TCL – Transaction Control Language

Used when you're working with transactions (a series of actions that must all happen together).

- **COMMIT** – Save changes permanently  
- **ROLLBACK** – Undo changes if something goes wrong  
- **SAVEPOINT** – Set a marker to rollback to later  

---

### 5. DCL – Data Control Language

Controls who can access or modify data.

- **GRANT** – Give access  
- **REVOKE** – Take back access  

---

## SELECT Statement – The Heart of SQL Queries

`SELECT` is used to pull data from one or more tables. It’s like saying: “Hey database, show me this info.”

### Basic Syntax:
```sql
SELECT * FROM table_name;
```

This will return **all the columns and rows** from the table.

---

## Keywords that Make SELECT More Powerful

Let’s break down a few useful variations of `SELECT`.

---

### 1. SELECT Specific Columns

```sql
SELECT name, age FROM Students;
```

Shows only name and age, not the whole table.

---

### 2. SELECT with Expressions and Aliases

```sql
SELECT name, marks + 10 AS updated_marks FROM Results;
```

Adds 10 to each mark and shows it with the name `updated_marks`.

---

### 3. SELECT DISTINCT

`DISTINCT` is used to **remove duplicates** from the results.

#### Scenario:
If multiple students are from the same city, and I want to list **unique cities**:

```sql
SELECT DISTINCT city FROM Students;
```

This gives me a list of cities without repetition.

---

## The 4 Core Operations Behind SELECT

Let’s now talk about the logic behind what we’re doing when we write SQL queries.

---

### 1. SELECT

This simply **fetches data** from a table — either everything, or specific columns.

```sql
SELECT * FROM Employees;
```

---

### 2. PROJECTION

This means choosing **specific columns** from a table.

#### Example:
```sql
SELECT name, department FROM Employees;
```

We’re projecting the "name" and "department" columns only.

---

### 3. SELECTION

Selection is about **picking rows** based on a condition — it filters the data.

#### Example:
```sql
SELECT * FROM Employees WHERE salary > 50000;
```

We’re selecting only those employees who earn more than 50,000.

---

### 4. JOIN

Join is used to **combine data from multiple tables** using a common column (usually a foreign key).

Let’s say we have:

- `Employee(id, name, dept_id)`
- `Department(dept_id, dept_name)`

We can join them like this:

```sql
SELECT Employee.name, Department.dept_name
FROM Employee
JOIN Department
ON Employee.dept_id = Department.dept_id;
```

Now we get each employee’s name along with their department name.

---

## Summary

Here’s a quick recap of what I revised today:

- **SQL statements** come in 5 flavors: DDL, DML, DQL, TCL, and DCL
- **SELECT** is used to fetch data — either all columns, specific ones, or even transformed values
- **DISTINCT** helps remove duplicates
- Four core operations behind queries are:
  - SELECT → return all data
  - PROJECTION → return specific columns
  - SELECTION → filter rows
  - JOIN → combine tables

---

## Final Thought

I used to think SQL was just about pulling data, but now I’m starting to appreciate how powerful and organized it really is. Every command serves a purpose, and when you combine them, you can get exactly the data you need — clean, filtered, and connected.

This was a good reminder that **sticking to the basics and showing up consistently really pays off**. Understanding concepts like these step by step builds the confidence to take on more complex stuff later.

On to the next topic tomorrow!
