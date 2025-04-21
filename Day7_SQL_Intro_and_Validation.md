
--# Day 7: Getting Started with SQL — Basics, History & How Data is Validated

Since I’ve been learning Python Full Stack Development, I figured it was the right time to start revising SQL. After all, databases are a big part of backend development, and I don’t want to just "know" SQL — I want to really understand it.

Today’s session was all about going back to the fundamentals: What SQL actually is, where it came from, and how data is stored and validated in a structured, meaningful way.

---

## A Quick Look Back: Where SQL Came From

SQL has been around for a while. It was originally called **SEQUEL** (Structured English Query Language), developed by **Raymond Boyce** and **Donald Chamberlin** at IBM in the early 1970s.

Later, in **1986**, the **American National Standards Institute (ANSI)** standardized the language and renamed it to **SQL** — and it’s now the standard language used for interacting with relational databases.

---

## So, What is SQL — Really?

SQL (Structured Query Language) is a language used to store, retrieve, update, and manage data in databases.

But in simple terms, I’d say:

> SQL helps us *talk to the database* — we ask questions, and it gives us the answers.

---

### Scenario: 
Let’s say I’m building a student dashboard. Every time I want to:
- Add a new student’s record  
- Display a list of students  
- Update someone’s email or grade  
- Or even remove a student’s data  

…I’ll be writing SQL queries in the backend to make those things happen.

---

## Middleware & Backend — Where SQL Fits In

In full stack development:
- The **backend** is the part that handles data, logic, and communication with the database.
- **Middleware** sits between the frontend and backend — it helps process user requests and sends data to the right place.

So when someone fills a form on a website (like a sign-up), SQL is often the language working behind the scenes to **store that data in the database**.

---

## Key Concepts I Explored Today

### Data
Any kind of raw information — names, numbers, values.

### Raw Fact
Unprocessed data like `"Red"` or `45`. These are not meaningful until organized.

### Attribute
A column in a table. For example, in a student table, `Name`, `Age`, and `Roll_No` are attributes.

### Entity
A real-world object we want to store data about — like a Student, Product, or Employee.

### Database
A collection of related data organized in a structured way (usually tables).

### CRUD
The 4 basic operations in a database:
- **Create** — add new data
- **Read** — view data
- **Update** — modify existing data
- **Delete** — remove data

---

## DBMS vs. RDBMS — What’s the Difference?

### DBMS (Database Management System)
Stores data in files or single tables. No relationships between data.

### RDBMS (Relational Database Management System)
Stores data in **tables** and allows **relationships** between them using keys.

| Feature              | DBMS                        | RDBMS                            |
|---------------------|-----------------------------|----------------------------------|
| Data Format          | Files / Flat Tables         | Tables with relationships        |
| Data Relationships   | Not Supported               | Fully Supported                  |
| Example              | XML, File-based systems     | MySQL, PostgreSQL, Oracle        |

---

## Tables, Rows, Columns & Cells

To keep things simple:

- A **table** is like an Excel sheet.
- A **row** represents a single record (e.g., one student).
- A **column** is a field/attribute (e.g., name, age).
- A **cell** holds one piece of data (e.g., `Sukanya`).

---

## E.F. Codd’s Rules — Rule 4 on Validation

I came across **Rule 4** from E.F. Codd's 12 Rules of RDBMS, and it made so much sense. It says that before storing data, it must be validated in **two steps**:

### Step 1: Validate the **Data Type**
Check whether the data fits the expected format — like number, text, or date.

### Step 2: Validate the **Constraints**
Enforce rules like "this field must not be empty", or "this value must be unique".

Together, these checks help maintain clean and accurate data in a database.

---

## SQL Data Types I Learned Today

### 1. `CHAR(n)`  
Used for storing **fixed-length** strings. If the data is shorter, it adds spaces.

```sql
name CHAR(10)
```

So `'abc'` becomes `'abc       '`.

---

### 2. `VARCHAR(n)` or `VARCHAR2(n)`  
Stores **variable-length** strings. Much more flexible than `CHAR`.

```sql
email VARCHAR(50)
```

Stores exactly what you input, no padding.

---

### 3. `DATE`  
Stores date values. Helps perform date-based operations.

```sql
dob DATE
```

Stores dates like `'2024-04-21'`.

---

### 4. `NUMBER(p, s)`  
Used to store numeric data with precision and scale.

```sql
price NUMBER(5, 2)
```

Allows values like `123.45` (max 5 digits, with 2 after the decimal).

---

## A Quick Scenario

Let’s say I’m designing a product table for an online store:

```sql
CREATE TABLE Product (
    product_id NUMBER(5),
    name VARCHAR(50),
    price NUMBER(6,2),
    launch_date DATE
);
```

Here:
- Every column has a **data type**
- I can later apply **constraints** like `NOT NULL`, `UNIQUE`, or `PRIMARY KEY` to ensure valid data

---

## Final Thoughts

Today helped me understand that databases are not just about storing information — they’re about storing **valid, structured, meaningful data**.

Things like:
- Single-valued cells
- Relating data across multiple tables
- Validating everything before storage

...are all part of what makes a relational database reliable and efficient.

Next up, I’ll dive into **SQL constraints**, so I can start writing actual table creation queries with real validation rules.

Let’s go one step further tomorrow.
