```markdown
#  Day 4: Python Tuples — Immutable but Powerful

Today I explored `tuple`, another important built-in data type in Python.  
Tuples are quite similar to lists, but with one major difference — they’re immutable.

Let’s go through what I revised and discovered.



##  What is a Tuple?

A tuple is an ordered collection of elements — like a list — but once created, its elements cannot be changed.

It is defined using parentheses `()` or the `tuple()` constructor.

---
```
## Syntax

```python
# Using parentheses
t = (1, 2, 3)

# Using tuple() function
t = tuple([4, 5, 6])
```

### ✅ Default Value

An empty tuple is created like this:

```python
empty = ()
print(empty)        # ()
print(type(empty))  # <class 'tuple'>
```

---

## Tuples are Immutable

Once created, you **cannot modify**, **add**, or **remove** elements in a tuple.

###  Example:

```python
t = (10, 20, 30)
t[1] = 100  # ❌ This will raise a TypeError
```

 Error:
```
TypeError: 'tuple' object does not support item assignment
```

---

##  Useful Built-in Functions

###  `id(t)` – Identity in memory
```python
t = (1, 2, 3)
print(id(t))
```

###  `type(t)` – Tells the data type
```python
print(type(t))  # <class 'tuple'>
```

###  `bool(t)` – Truthiness of tuple
```python
print(bool((1, 2)))  # True
print(bool(()))      # False
```

- Any **non-empty** tuple is `True`
- An **empty tuple** is considered `False`

---

##  Tuples Are Immutable, But…

You **can modify a mutable object inside a tuple** — like a list.

###  Example:

```python
t = (1, 2, [3, 4])
t[2].append(5)
print(t)  # (1, 2, [3, 4, 5])
```

 The tuple itself is still immutable — but it contains a **mutable list**, and that list can be changed!

---

##  Final Takeaways

- `tuple` is like a list, but **immutable**
- Use `()` to define it
- Supports `id()`, `type()`, `bool()` functions
- Can't change items directly — but can modify **mutable items inside** (like lists)
- Great for **fixed data collections** and when immutability is needed

---

Tomorrow, I’ll explore **sets** and how they differ from lists & tuples. 
