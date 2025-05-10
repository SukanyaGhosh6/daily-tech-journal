# Day 22 – Python Recalling: Basics, Input, Typecasting & Control Statements

Today was all about going back to Python basics — the kind of stuff that forms the foundation for everything else. From printing a line to using conditional statements, it felt good to just write some clean, simple code again.

---

## Printing in Python

Let's start with the most classic thing in programming:

```python
print("Hello, world!")
````

This `print()` function is used to display anything on the screen. Strings, numbers, variables — you name it.

---

## Taking Input from the User

To take data from a user, we use the `input()` function. Here's how it works:

```python
name = input("Enter your name: ")
print("Welcome", name)
```

By default, `input()` treats everything as a string. If we want to work with numbers, we need to **typecast** it.

---

## Typecasting and `eval()` Function

Sometimes we need the input in a specific data type — like `int`, `float`, or even a list. That’s where typecasting comes in.

```python
num = int(input("Enter a number: "))
```

To let Python automatically evaluate the correct data type (especially for collections like lists or tuples), we can use `eval()`:

```python
data = eval(input("Enter something (e.g., [1,2,3]): "))
print(type(data))
```

---

## Some Basic Programs

1. **Add two integers**

```python
a = int(input("Enter first number: "))
b = int(input("Enter second number: "))
print("Sum is:", a + b)
```

2. **Find square of a number**

```python
n = int(input("Enter a number: "))
print("Square:", n * n)
```

3. **Convert float to integer**

```python
f = float(input("Enter a float number: "))
print("Integer value:", int(f))
```

4. **Extract last character of a string**

```python
s = input("Enter a string: ")
print("Last character:", s[-1])
```

5. **Reverse a string**

```python
s = input("Enter a string: ")
print("Reversed:", s[::-1])
```

6. **Get values at even index positions**

```python
s = input("Enter a string: ")
print("Even index characters:", s[::2])
```

7. **Extract last digit from an integer**

```python
n = int(input("Enter a number: "))
print("Last digit:", n % 10)
```

---

## Control Statements in Python

Control statements let us make decisions in code. There are two main types:

* **Decisional (if, if-else, elif, nested if)**
* **Looping (for, while)** — not covered today.

---

### 1. Simple `if` Statement

```python
n = int(input("Enter a number: "))
if n % 2 == 0:
    print("Even number")
```

---

### 2. Check if string has 5 characters

```python
s = input("Enter a string: ")
if len(s) == 5:
    print("String has 5 characters")
```

---

### 3. Square if number is a multiple of 5

```python
n = int(input("Enter a number: "))
if n % 5 == 0:
    print("Square:", n ** 2)
```

---

### 4. Cube if number is odd and divisible by 5

```python
n = int(input("Enter a number: "))
if n % 2 != 0 and n % 5 == 0:
    print("Cube:", n ** 3)
```

---

### 5. Check if a character is uppercase

```python
ch = input("Enter a character: ")
if ch.isupper():
    print("It’s uppercase")
```

---

## If-Else Statement

Syntax:

```python
if condition:
    # true block
else:
    # false block
```

1. **Check if data is float**

```python
data = eval(input("Enter something: "))
if type(data) == float:
    print("It's a float")
else:
    print("Not a float")
```

2. **Is character a vowel?**

```python
ch = input("Enter a character: ")
if ch.lower() in 'aeiou':
    print("It's a vowel")
else:
    print("Not a vowel")
```

3. **Single vs Collection data type**

```python
data = eval(input("Enter something: "))
if type(data) in [int, float, str, bool]:
    print("Single value data type")
else:
    print("Collection data type")
```

4. **Check if number is positive or negative**

```python
n = int(input("Enter a number: "))
if n >= 0:
    print("Positive")
else:
    print("Negative")
```

5. **Check if list has a middle value**

```python
lst = eval(input("Enter a list: "))
if len(lst) % 2 != 0:
    print("Middle value is:", lst[len(lst) // 2])
else:
    print("No single middle value (even length list)")
```

---

## `elif` Statement

Syntax:

```python
if cond1:
    # block1
elif cond2:
    # block2
elif cond3:
    # block3
else:
    # default block (optional)
```

1. **Relation between two integers**

```python
a = int(input("Enter first number: "))
b = int(input("Enter second number: "))
if a > b:
    print("First is greater")
elif b > a:
    print("Second is greater")
else:
    print("Both are equal")
```

2. **Find quadrant of a point**

```python
x = int(input("Enter X: "))
y = int(input("Enter Y: "))
if x > 0 and y > 0:
    print("Quadrant 1")
elif x < 0 and y > 0:
    print("Quadrant 2")
elif x < 0 and y < 0:
    print("Quadrant 3")
elif x > 0 and y < 0:
    print("Quadrant 4")
else:
    print("Origin or axis")
```

3. **Check if number is 2-digit**

```python
n = int(input("Enter a number: "))
if 10 <= abs(n) <= 99:
    print("It’s a 2-digit number")
else:
    print("Not a 2-digit number")
```

---

## Nested `if`

1. **Check if char is vowel or consonant**

```python
ch = input("Enter a character: ")
if ch.isalpha():
    if ch.lower() in 'aeiou':
        print("Vowel")
    else:
        print("Consonant")
else:
    print("Not a letter")
```

2. **Second greatest among four numbers**

```python
a = int(input("A: "))
b = int(input("B: "))
c = int(input("C: "))
d = int(input("D: "))
nums = sorted([a, b, c, d])
print("Second greatest is:", nums[-2])
```

---

3. **FizzBuzz Program**

```python
n = int(input("Enter a number: "))
if n % 3 == 0 and n % 5 == 0:
    print("FIZZBUZZ")
elif n % 3 == 0:
    print("FIZZ")
elif n % 5 == 0:
    print("BUZZ")
else:
    print(n)
```

---

That’s all for today. Felt great revisiting the basics and playing around with logic again. It’s like stretching muscles you didn’t know were sore.

More to come in Day 23!


