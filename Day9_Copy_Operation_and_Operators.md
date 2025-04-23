## Day 9: Copy Operation and Python Operators – A Beginner's Take

So today, I revisited something that might look small but makes a big difference when working with collections in Python — **copy operations**. I also went over the different **types of operators** we use while writing code.

Let me explain everything the way I understood it — simple, clear, and with examples that made things click.

---

## Copy Operation in Python – What's the Big Deal?

Let’s say you have a list of values stored in a variable, and now you want to copy that list to another variable. But — you don’t want the second variable to mess with the original one if you change something.

That’s where copy operations come in.

We **use copy operations to keep the original collection safe** while we work with the copied one. While it technically works for any datatype, we mostly use it with **lists** because they are mutable.

---

### Mutable vs Immutable

Copy operations don’t really apply to **immutable types** like:
- `int`, `float`, `complex`, `bool`, `str`, and `tuple`

They are safe from changes anyway, because they **cannot be changed in-place**.

But with **mutable types** like:
- `list`, `set`, and `dictionary`

…we have to be careful, because changes made using one variable can affect the original collection.

Copy operations don’t really work well on `set` or `dict` unless you handle them correctly — especially since **dictionary keys must be unique and immutable**.

---

## Types of Copy in Python

There are 3 types of copy operations:

---

### 1. General Copy (a.k.a. Normal Copy)

This is the simplest form of copying:

```python
l = [10, 20, 30]
m = l
```

Now both `l` and `m` are pointing to the **same memory**. If I change `m`, it will change `l` too.

#### Example:
```python
m[1] = 200
print(m)  # [10, 200, 30]
print(l)  # [10, 200, 30]
```

So yeah, they’re basically two names for the same list.

#### What if it's a nested list?

```python
l = [40, 80, [20, 30]]
m = l
m[2][1] = 300
print(m)  # [40, 80, [20, 300]]
print(l)  # [40, 80, [20, 300]]
```

Even the nested part got affected — because they’re linked by memory.

---

### 2. Shallow Copy

Now this one's a little smarter.

```python
l = [20, 80, 50]
q = l.copy()
```

Here, `q` gets its own copy — but only for the top level.

#### Example (Linear List):
```python
q[2] = 5
print(q)  # [20, 80, 5]
print(l)  # [20, 80, 50]
```

Looks good — no change in `l`.

#### But with nested lists:
```python
l = [100, [1, 2]]
q = l.copy()
q[1][0] = 999

print(q)  # [100, [999, 2]]
print(l)  # [100, [999, 2]]
```

Even though we used `.copy()`, it still changed the inner list — because shallow copy only handles the **outer layer**.

---

### 3. Deep Copy

This one makes a complete, separate copy — no shared memory at all.

```python
import copy
l = [5, 8.6, 4+3j, 14]
m = copy.deepcopy(l)
m[1] = 2.3
```

#### Output:
```python
print(m)  # [5, 2.3, (4+3j), 14]
print(l)  # [5, 8.6, (4+3j), 14]
```

Even if the list was nested, deep copy would still keep things fully independent.

---

## Operators in Python

Alright, now let’s talk about something we use every day while coding — **operators**. These are special symbols that let us perform different types of operations.

There are 7 types of operators in Python:

---

### 1. Arithmetic Operators

Used to perform basic math.

| Operator | Description     | Example      | Output |
|----------|-----------------|--------------|--------|
| `+`      | Addition         | `5 + 3`      | 8      |
| `-`      | Subtraction      | `5 - 3`      | 2      |
| `*`      | Multiplication   | `5 * 3`      | 15     |
| `/`      | Division         | `5 / 2`      | 2.5    |
| `//`     | Floor Division   | `5 // 2`     | 2      |
| `%`      | Modulus          | `5 % 2`      | 1      |
| `**`     | Exponent         | `2 ** 3`     | 8      |

---

### 2. Logical Operators

Used to combine conditions.

| Operator | Description     | Example           | Output |
|----------|-----------------|-------------------|--------|
| `and`    | Both true        | `True and False`  | False  |
| `or`     | At least one     | `True or False`   | True   |
| `not`    | Reverse result   | `not True`        | False  |

---

### 3. Relational (Comparison) Operators

Used to compare values.

| Operator | Example   | Output |
|----------|-----------|--------|
| `==`     | 5 == 5     | True   |
| `!=`     | 5 != 3     | True   |
| `>`      | 5 > 3      | True   |
| `<`      | 5 < 3      | False  |
| `>=`     | 5 >= 5     | True   |
| `<=`     | 5 <= 3     | False  |

---

### 4. Bitwise Operators

Work with binary values.

| Operator | Example    | Output |
|----------|------------|--------|
| `&`      | 5 & 3       | 1      |
| `|`      | 5 | 3       | 7      |
| `^`      | 5 ^ 3       | 6      |
| `~`      | ~5          | -6     |
| `<<`     | 5 << 1      | 10     |
| `>>`     | 5 >> 1      | 2      |

---

### 5. Assignment Operators

Used to assign values.

| Operator | Example   |
|----------|-----------|
| `=`      | x = 10    |
| `+=`     | x += 5    |
| `-=`     | x -= 3    |
| `*=`     | x *= 2    |
| `/=`     | x /= 2    |

…and similar for `//=`, `%=`, `**=`, etc.

---

### 6. Membership Operators

Used to check if a value exists in a sequence.

| Operator | Example           | Output |
|----------|-------------------|--------|
| `in`     | `'a' in 'apple'`  | True   |
| `not in` | `'z' not in 'apple'` | True |

---

### 7. Identity Operators

Used to compare memory location of objects.

| Operator | Example         | Output |
|----------|------------------|--------|
| `is`     | `x is y`         | True / False |
| `is not` | `x is not y`     | True / False |

---

## Wrapping Up

This revision made me realize how many small details go into something as simple as copying a list or using an operator. The more I play with examples, the more confident I feel.

And honestly, that’s the whole point, right? Keep showing up, keep learning, and just be consistent.

The basics may seem simple, but when you really understand them — that’s when things start getting exciting.

See you in Day 10.
