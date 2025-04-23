
#  Day 2: Python Revision — Keywords, Operators, Built-in Functions, Variables & Data Types

Okay, so today I sat down and revised some core Python concepts that I kinda knew but wanted to understand better.  
Instead of just memorizing stuff, I tried out examples and actually played around with the code a bit — it made a huge difference!



## 1.  Keywords – Can’t Use These as Variable Names!

Python has some special words that are reserved, like `if`, `while`, `for`, `True`, `False`, etc. You can’t use them as variable names.

###  Example:

```python
if = 5  # ❌ SyntaxError: invalid syntax
```

Python didn’t like it. 

You can also list all keywords with:

```python
import keyword
print(keyword.kwlist)
```

Turns out there are around **35** of them!

---

## 2.  Operators & Special Symbols – Tiny but Powerful

These symbols do math, comparisons, and more.

###  Common Operators:

```python
a = 10
b = 3

print(a + b)  # Addition
print(a - b)  # Subtraction
print(a * b)  # Multiplication
print(a / b)  # Division
print(a % b)  # Modulo
```

###  Special Symbols:

- `:` is used after `if`, `for`, `def`, etc.
- `@` is used in decorators
- `#` is for comments
- `=` is assignment, `==` is comparison

---

## 3.  Inbuilt Functions – Ready-to-Use Tools

Python gives us a bunch of **built-in functions** — no need to define them yourself.

###  Examples I used:

```python
print(len("Python"))
print(type(3.14))
print(range(5))
print(sorted([3, 1, 2]))
```

They really save time and make your code cleaner.

---

## 4.  Variables, Identifiers & Syntax

A **variable** stores a value. The name you give it is an **identifier**.

###  Example:

```python
x = 10
name = "Sukanya"
```

###  Rules I reminded myself of:
- Can't start with numbers → `2name` ❌
- Only `_` allowed as special character → `first_name` ✅
- Can't use keywords → `for = 5` ❌

---

## 5.  Data Types – Single & Multi-Valued

### 1️⃣ Single-Valued Data Types

####  Integer (`int`)
```python
a = 100
```

####  Float (`float`)
```python
pi = 3.14
```

####  Complex (`complex`)
```python
z = 2 + 3j
```

####  Boolean (`bool`)
```python
is_valid = True
print(5 > 3)  # True
```

---

### 2️⃣ Multi-Valued Data Type: String (`str`)

Strings are text inside quotes, and can be indexed.

```python
text = "Python"
print(text[0])    # P
print(text[-1])   # n
```

- **Positive indexing** starts from 0
- **Negative indexing** starts from -1  
Very useful for slicing, reversing, etc.

---

##  Final Takeaways from Today’s Revision:

- Python has keywords that we **shouldn’t mess with**
- Operators and symbols make the code **work**
- Built-in functions are **super useful** and save time
- Variables store values, and identifiers have **naming rules**
- Python handles different **data types**: numbers, strings, booleans
- Indexing helps you **access characters** inside strings easily

---

This session really helped solidify the basics.  
Next, I’ll try working with **lists, tuples, sets**, and **dictionary** data types. Can’t wait!!!!!!


