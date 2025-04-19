###  `Day5_Set.md` 

#  Day 5: Python Sets — Unordered, Unique & Mutable

Today I explored the `set` data type in Python. Sets are very different from lists and tuples in terms of behavior and purpose, and I had a lot of fun playing with them!

Let’s dive into what makes sets unique 👇



##  What is a Set?

A **set** is a built-in Python data type used to store **multiple items** in a **single variable**, just like lists and tuples.  
However, sets:

Only store **unique** values
Are **unordered**
Are **mutable**
Are **unindexed**

---

##  Syntax & Default Value

```python
# Creating a set
my_set = {1, 2, 3, 4}

# Empty set (IMPORTANT)
empty_set = set()      # ✅ Correct
empty_set_wrong = {}   # ❌ This creates a dictionary
```

###  Example:

```python
numbers = {1, 2, 3, 3, 4}
print(numbers)  # Output: {1, 2, 3, 4}
```

>  The duplicate `3` is automatically removed!

---

##  Characteristics of a Set

### 1.  **Unordered Collection**

Elements are **not stored in a specific order**, so the order you see might be different each time.

```python
s = {5, 2, 9, 1}
print(s)  # Output could be: {1, 2, 5, 9} or {2, 1, 9, 5}
```

---

### 2.  **Stores Only Immutable Data Types**

You can store:
- Numbers (`int`, `float`)
- Strings
- Tuples

You **cannot** store lists or dictionaries directly (because they are mutable).

```python
valid_set = {1, "hello", (2, 3)}  # ✅
invalid_set = {[1, 2], 3}         # ❌ TypeError
```

---

### 3.  **No Duplicates Allowed**

Any repeated elements are automatically removed.

```python
nums = {1, 2, 2, 3, 3, 3}
print(nums)  # {1, 2, 3}
```

---

### 4.  **Cannot Access by Index**

Sets do **not support indexing** or slicing.

```python
s = {10, 20, 30}
print(s[0])  # ❌ TypeError: 'set' object is not subscriptable
```

---

##  Inbuilt Functions in Set

### 1.  `add()` — Add an item

```python
colors = {"red", "blue"}
colors.add("green")
print(colors)  # {'red', 'blue', 'green'}
```

---

### 2.  `remove()` — Remove a specific item (error if not found)

```python
colors.remove("blue")
print(colors)  # Removes 'blue'

colors.remove("yellow")  # ❌ KeyError if 'yellow' doesn't exist
```

---

### 3.  `pop()` — Removes a random element

```python
nums = {1, 2, 3}
nums.pop()
print(nums)  # One random item will be removed
```

⚠️ Since sets are unordered, you never know which element will be removed.

---

##  Summary of What I Learned Today

- `set` is an **unordered**, **mutable**, and **unindexed** collection
- Only **immutable data types** can be stored
- **Duplicates are not allowed**
- Cannot access or modify elements using index
- Useful functions: `add()`, `remove()`, `pop()`

---

Next up: **Dictionaries!** I’m super excited to see how they work with key-value pairs. Let’s go!!!!!!!!
