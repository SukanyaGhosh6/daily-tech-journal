As I continued my SQL learning journey, today’s revision covered some important concepts used in table design and data validation — like **precision and scale**, **large object types**, and different types of **constraints** that ensure the data we store is valid and useful.

Everything I learned today is written in a very beginner-friendly way, with examples and practical use cases.

---

## Precision and Scale in SQL

### What is Precision?

Precision is the **total number of digits** that a number can store — both before and after the decimal point.

- It is used when we are storing **numeric values**.
- **Range**: 1 to 38
- **No default value** is set unless we define it.

---

### What is Scale?

Scale is the number of **digits after the decimal point**.

- It is used to store **decimal (fractional) values**.
- **Range**: -84 to 127
- **Default value** is `0`

---

### Example: `NUMBER(5, 2)`

This means:
- **Precision = 5** → The number can have up to 5 digits total.
- **Scale = 2** → Out of those 5 digits, 2 digits will come **after the decimal**.

So a number like `123.45` is valid — 3 digits before and 2 after.

If we try to store a number like `12345.67`, it will be **rejected** because it exceeds the total digits (precision).

---

### Special Case:
If scale is **greater than** precision (e.g., `NUMBER(2, 5)`), then we calculate the difference:

```
Scale - Precision = 5 - 2 = 3
```

This means the number can only have **decimal digits** and **no whole number part**. For example: `0.00012` is valid.

---

## Large Objects (LOBs)

When storing **large content**, like long text, images, or documents, we use **LOB** data types.

---

### CLOB (Character Large Object)

- Used to store a large amount of **character data**
- Can store up to **4 GB** of text

### Syntax:
```sql
bio CLOB
```

### Scenario:
If you are building a blogging platform and want to store a long article or user biography that goes beyond the regular VARCHAR limits, you can use a `CLOB` column for that.

---

### BLOB (Binary Large Object)

- Used to store **binary data** such as images, videos, audio files, PDFs, etc.
- Can store up to **4 GB** of binary content

### Syntax:
```sql
profile_picture BLOB
```

### Scenario:
Let’s say we’re creating a student database, and we want to store their scanned ID card photos. These image files can be stored in a `BLOB` column.

---

## Constraints in SQL

Constraints are **rules** added to columns to control the kind of data that can go into a table. They ensure the data is **accurate and reliable**.

There are **five common types** of constraints in SQL:

---

### 1. UNIQUE Constraint

- Prevents **duplicate values** in a column.
- Allows `NULL` values.

### Example:
```sql
CREATE TABLE Employee (
    email VARCHAR(100) UNIQUE
);
```

### Scenario:
To make sure no two employees register with the same email, we use the `UNIQUE` constraint.

---

### 2. NOT NULL Constraint

- Ensures a column **cannot be left empty** (null).
- Every row **must** have a value in that column.

### Example:
```sql
CREATE TABLE Student (
    name VARCHAR(50) NOT NULL
);
```

### Scenario:
We don’t want students in our database without names. So we add `NOT NULL` to make name mandatory.

---

### 3. CHECK Constraint

- Adds a **custom condition** to the column.
- Only values satisfying the condition are accepted.

### Example:
```sql
CREATE TABLE Orders (
    quantity INT CHECK (quantity > 0)
);
```

### Scenario:
You can’t place an order with 0 or negative items. This condition makes sure that can’t happen.

---

### 4. PRIMARY KEY Constraint

- Used to **uniquely identify each record** in a table.
- Cannot have `NULL` or duplicate values.
- A table can have **only one primary key**.

### Characteristics of Primary Key:
1. Must be unique  
2. Cannot be null  
3. Combination of `UNIQUE + NOT NULL`  
4. Only one per table

### Example:
```sql
CREATE TABLE Department (
    dept_id INT PRIMARY KEY,
    dept_name VARCHAR(50)
);
```

---

### 5. FOREIGN KEY Constraint

- Used to **link two tables** together
- A column in one table refers to the **primary key** in another table

### Characteristics of Foreign Key:
1. Can accept **duplicate values**
2. Can accept **null values**
3. Used to **connect related tables**
4. Can have **multiple** foreign keys in one table
5. The column must be a **primary key in its original table**

---

### Example with Parent and Child Tables

Let’s say we have two tables: `Student` and `Marks`.

#### Parent Table – `Student`
```sql
CREATE TABLE Student (
    roll_no INT PRIMARY KEY,
    name VARCHAR(50)
);
```

#### Child Table – `Marks`
```sql
CREATE TABLE Marks (
    roll_no INT,
    subject VARCHAR(50),
    marks INT,
    FOREIGN KEY (roll_no) REFERENCES Student(roll_no)
);
```

- `Student` is the **parent table** (with primary key `roll_no`)
- `Marks` is the **child table** (its `roll_no` is a foreign key)

This way, we link student data to their marks without repeating student details.

---

## Conclusion

This revision helped me understand how **data precision**, **large storage types**, and **constraints** shape the quality of any database we build. It’s not just about storing data — it’s about **storing it right**.

Knowing when to use `NUMBER(5, 2)` instead of just `INT`, or using `CLOB` to store huge paragraphs, or adding a `CHECK` so only valid marks get saved — all of these make the system more reliable.

Let's keep Learning!!
