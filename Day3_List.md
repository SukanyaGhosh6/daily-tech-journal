
```markdown
#  Day 3: Python Lists — Basics, Characteristics & Common Functions

Today I focused on one of the most important and commonly used data types in Python — Lists.  
I explored what they are, how they behave, and played around with some built-in functions.

Let’s break it down 👇



##  What is a List?

A list is a built-in Python data structure that is used to store a collection of items in a single variable.

Lists are ordered
They are mutable (can be changed after creation)
They can contain items of any data type
Defined using square brackets `[]`


```
##  Homogeneous vs. Heterogeneous Lists

###  Homogeneous List
All elements are of the same type.

```python
numbers = [1, 2, 3, 4, 5]  # All integers

```
###  Heterogeneous List
List contains elements of different data types.

```python
mixed = [1, "hello", 3.14, True]
```

---

##  Syntax to Create a List

```python
# An empty list
my_list = []

# A list with some values
fruits = ["apple", "banana", "cherry"]
```

You can also initialize a list using the `list()` function:

```python
colors = list(["red", "green", "blue"])
```

---

##  Characteristics of Lists

- **Mutable** → You can update, insert, or delete items.
- **Ordered** → Maintains the order in which elements were added.
- **Indexable** → Access items using index like `list[0]`
- **Can hold duplicates** → Same values can appear more than once.

---

##  Inbuilt Functions for Lists

Let’s explore some of the most useful built-in functions I practiced today 👇

---

### 1.  `append()` — Add item at the end

**Syntax:**

```python
list_name.append(item)
```

**Example:**

```python
fruits = ["apple", "banana"]
fruits.append("cherry")
print(fruits)  # ['apple', 'banana', 'cherry']
```

---

### 2.  `insert()` — Insert item at a specific index

**Syntax:**

```python
list_name.insert(index, item)
```

**Example:**

```python
fruits = ["apple", "cherry"]
fruits.insert(1, "banana")
print(fruits)  # ['apple', 'banana', 'cherry']
```

---

### 3.  `pop()` — Removes item at a given index (or last item by default)

**Syntax:**

```python
list_name.pop([index])
```

**Example:**

```python
fruits = ["apple", "banana", "cherry"]
fruits.pop()       # Removes 'cherry'
fruits.pop(0)      # Removes 'apple'
print(fruits)      # ['banana']
```

---

### 4.  `remove()` — Removes the first occurrence of a value

**Syntax:**

```python
list_name.remove(value)
```

**Example:**

```python
numbers = [1, 2, 3, 2, 4]
numbers.remove(2)
print(numbers)  # [1, 3, 2, 4]
```

Only the **first** `2` was removed.

---

##  Summary of What I Learned Today

 Lists are one of Python's most flexible data structures
 They can be **homogeneous** or **heterogeneous**
 Lists are **mutable**, **ordered**, and **indexable**
 You can manipulate them using built-in methods like `append()`, `insert()`, `pop()`, and `remove()`

---

Tomorrow I’ll dive into **tuples, sets, and dictionaries** — and how they compare with lists. 


