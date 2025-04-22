# Day 8: Python Type Casting — How to Convert Between Data Types

Today, I revised the concept of **type casting in Python**, which basically means converting a value from one data type to another. This is especially useful when we want to make sure two values are of the same type before performing operations or when we want to display data differently.

---

## What is Type Casting?

Type casting (or type conversion) is the process of converting the data type of a value into another type. Python makes this pretty straightforward.

### General Syntax:
```python
destination_variable = destination_type(source_value)
```

For example:
```python
a = 10
b = float(a)
print(b)  # Output: 10.0
```

---

## 1. Integer to Other Data Types

Let’s take `a = 10` as the base value.

```python
a = 10

# int to float
print(float(a))       # 10.0

# int to complex
print(complex(a))     # (10+0j)

# int to bool
print(bool(a))        # True

# int to string
print(str(a))         # '10'

# int to list
print(list(str(a)))   # ['1', '0']

# int to tuple
print(tuple(str(a)))  # ('1', '0')

# int to set
print(set(str(a)))    # {'1', '0'}

# int to dictionary
# Not directly possible, would raise error
# Example of workaround:
a = 10
print(dict([(1, a)])) # {1: 10}
```

---

## 2. Float to Other Data Types

```python
f = 5.67

# float to int
print(int(f))        # 5

# float to complex
print(complex(f))    # (5.67+0j)

# float to bool
print(bool(f))       # True

# float to string
print(str(f))        # '5.67'

# float to list/tuple/set — use string as intermediate
print(list(str(f)))  # ['5', '.', '6', '7']
print(tuple(str(f))) # ('5', '.', '6', '7')
print(set(str(f)))   # {'6', '.', '5', '7'}
```

---

## 3. Complex to Other Data Types

```python
c = complex(4, 5)

# complex to string
print(str(c))        # '(4+5j)'

# complex to bool
print(bool(c))       # True

# Cannot convert complex to int or float directly
# int(c) or float(c) will raise an error
```

---

## 4. Bool to Other Data Types

```python
b = True

# bool to int
print(int(b))        # 1

# bool to float
print(float(b))      # 1.0

# bool to complex
print(complex(b))    # (1+0j)

# bool to string
print(str(b))        # 'True'

# bool to list/tuple/set
print(list(str(b)))  # ['T', 'r', 'u', 'e']
```

---

## 5. String to Other Data Types

```python
s = "123"

# string to int
print(int(s))        # 123

# string to float
print(float(s))      # 123.0

# string to complex
print(complex(s))    # (123+0j)

# string to bool
print(bool(s))       # True

# string to list/tuple/set
print(list(s))       # ['1', '2', '3']
print(tuple(s))      # ('1', '2', '3')
print(set(s))        # {'1', '2', '3'}
```

If the string contains non-numeric values like `"abc"`, then converting to int or float will raise an error.

---

## 6. List to Other Data Types

```python
l = [1, 2, 3]

# list to tuple
print(tuple(l))      # (1, 2, 3)

# list to set
print(set(l))        # {1, 2, 3}

# list to string
print(str(l))        # '[1, 2, 3]'

# list to bool
print(bool(l))       # True

# list to dictionary — only possible if elements are key-value pairs
pairs = [(1, 'a'), (2, 'b')]
print(dict(pairs))   # {1: 'a', 2: 'b'}
```

---

## 7. Tuple to Other Data Types

```python
t = (4, 5, 6)

# tuple to list
print(list(t))       # [4, 5, 6]

# tuple to set
print(set(t))        # {4, 5, 6}

# tuple to string
print(str(t))        # '(4, 5, 6)'

# tuple to bool
print(bool(t))       # True
```

---

## 8. Set to Other Data Types

```python
s = {7, 8, 9}

# set to list
print(list(s))       # [8, 9, 7] (order may vary)

# set to tuple
print(tuple(s))      # (8, 9, 7)

# set to string
print(str(s))        # '{8, 9, 7}'

# set to bool
print(bool(s))       # True
```

You can't directly convert a set to a dictionary unless it contains key-value pairs.

---

## 9. Dictionary to Other Data Types

```python
d = {"a": 1, "b": 2}

# dictionary to string
print(str(d))        # "{'a': 1, 'b': 2}"

# dictionary to bool
print(bool(d))       # True

# dictionary to list, tuple, set — converts keys only
print(list(d))       # ['a', 'b']
print(tuple(d))      # ('a', 'b')
print(set(d))        # {'a', 'b'}
```

To work with values and key-value pairs:

### To get just the values:
```python
print(d.values())    # dict_values([1, 2])
```

### To get both key and value pairs:
```python
print(d.items())     # dict_items([('a', 1), ('b', 2)])
```

---

## Final Thoughts

Understanding how type casting works really helps avoid unexpected errors in programs and allows more flexibility when handling user input or transforming data.

Some conversions are simple and safe (like int to float), while others require careful handling (like converting a string to a list or a dictionary to a list). I’ll keep practicing these with more custom examples and edge cases.

Lets keep learning!!!
