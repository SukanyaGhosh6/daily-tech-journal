#  Day 6: Python Dictionaries — Key-Value Magic

After sets, I explored another powerful and super useful Python data type — the **dictionary (`dict`)**.  
Unlike lists or sets, dictionaries store data in **key-value pairs**, making it perfect for structured data.

Let’s break it all down.



##  What is a Dictionary?

A **dictionary** is a mutable, unordered collection of data values, used to store data in **key: value** format.

---

##  Syntax

```python
# Default (empty) dictionary
my_dict = {}

# Non-default (with values)
student = {
    "name": "Sukanya",
    "age": 22,
    "is_student": True
}
```

---

##  Indexing is Not Possible

You **cannot** access values using numeric indexes like lists.

```python
print(student[0])  # ❌ TypeError: 0 is not a key
```

Instead, you access values using **keys**:

```python
print(student["name"])  # Sukanya
```

---

##  Modifying a Value in a Dictionary

You can change the value for a given key using **assignment**.

###  Syntax & Example:

```python
student["age"] = 23
print(student)  # {'name': 'Sukanya', 'age': 23, 'is_student': True}
```

If the key doesn't exist, it will add a new one:

```python
student["course"] = "Python"
print(student)  # Adds 'course': 'Python'
```

---

##  Removing a Value Using `pop()`

The `pop()` function removes a key-value pair based on the key.

###  Example:

```python
student.pop("is_student")
print(student)  # {'name': 'Sukanya', 'age': 23, 'course': 'Python'}
```

If the key doesn’t exist, it raises a `KeyError`.

---

##  Dictionaries Are Mutable

You can:
- Add new key-value pairs
- Modify existing values
- Remove items

All **without creating a new dictionary**.

---

##  Final Recap

- Dictionaries store **key-value** pairs
- Defined using `{}` or `dict()`
- **Unindexed** — use keys instead of numeric indexes
- **Mutable** — can add, modify, and delete entries
- Use `pop()` to remove an item by key

---

Tomorrow I’ll explore **slicing** . Let’s keep going!!!!!!!


