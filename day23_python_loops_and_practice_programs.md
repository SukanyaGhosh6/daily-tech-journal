# Day 23 – Python Recalling: Looping Statements with Practice

Today I focused on **looping statements in Python**. Loops are essential when we want to run a block of code multiple times. Python gives us two main types:

- `while` loop
- `for` loop

Let’s break them down, one at a time.

---

##  While Loop

### **Syntax**:
```python
while condition:
    # statement block
````

### **Flow Diagram**:

1. Check the condition
2. If True → execute the block
3. Go back and re-check
4. If False → exit the loop

---

### **Practice Programs using while loop**:

**1. Print numbers from 1 to 5**

```python
i = 1
while i <= 5:
    print(i)
    i += 1
```

**2. Even numbers between 1 to 50**

```python
i = 1
while i <= 50:
    if i % 2 == 0:
        print(i)
    i += 1
```

**3. Reverse a given number**

```python
n = int(input("Enter a number: "))
rev = 0
while n > 0:
    rev = rev * 10 + n % 10
    n = n // 10
print("Reversed:", rev)
```

**4. Sum of individual digits**

```python
n = int(input("Enter a number: "))
s = 0
while n > 0:
    s += n % 10
    n //= 10
print("Sum:", s)
```

**5. Factorial of a number**

```python
n = int(input("Enter a number: "))
f = 1
i = 1
while i <= n:
    f *= i
    i += 1
print("Factorial:", f)
```

**6. Extract lowercase characters from string**

```python
s = input("Enter a string: ")
i = 0
while i < len(s):
    if s[i].islower():
        print(s[i], end="")
    i += 1
```

**7. Convert lowercase to uppercase**

```python
s = input("Enter a string: ")
i = 0
while i < len(s):
    if s[i].islower():
        print(s[i].upper(), end="")
    else:
        print(s[i], end="")
    i += 1
```

---

##  For Loop

Used when you already know how many times to loop.

### **Syntax of range()**:

```python
range(start, stop, step)
```

### **Syntax of for loop**:

```python
for variable in range(...):
    # block
```

---

### **Practice Programs using for loop**:

**1. Find length of a collection without using len()**

```python
s = input("Enter something: ")
count = 0
for _ in s:
    count += 1
print("Length:", count)
```

**2. Check if a string is palindrome**

```python
s = input("Enter a string: ")
rev = ''
for i in range(len(s)-1, -1, -1):
    rev += s[i]
if s == rev:
    print("Palindrome")
else:
    print("Not a palindrome")
```

**3. Remove duplicate values from a list**

```python
l = [1,2,2,3,4,4,5]
unique = []
for i in l:
    if i not in unique:
        unique.append(i)
print(unique)
```

**4. Tuple word lengths:**

```python
t = (12, 4+3j, 4.3, 'hai', 8, 'python', 1.6, 'ab')
out = {}
for i in t:
    if type(i) == str:
        out[i] = len(i)
print(out)
```

**5. Dictionary from words with 2-letter slices:**

```python
l = [5, 3.2, 'data', 4+3j, 'Science', 12]
out = {}
for i in l:
    if type(i) == str:
        out[i.lower()] = i[:2]
print(out)
```

**6. String from A to Z**

```python
s = ''
for i in range(65, 91):
    s += chr(i)
print(s)
```

**7. Word lengths in a sentence**

```python
s = 'hai hello how are you'
out = {}
for word in s.split():
    out[word] = len(word)
print(out)
```

**8. Extensions from filenames**

```python
l = ['python.py', 'pro1.html', 'pro2.py', 'google.com']
out = []
for item in l:
    ext = item.split('.')[-1]
    out.append(ext)
print(out)
```

**9. Reverse words in a sentence**

```python
s = 'how are you'
words = s.split()
rev = ''
for word in words[::-1]:
    rev += word + ' '
print(rev.strip())
```

**10. Frequency count of characters**

```python
s = 'abcababccc'
out = {}
for i in s:
    out[i] = out.get(i, 0) + 1
res = ''
for k in out:
    res += k + str(out[k])
print(res)
```

**11. Filter letters: only vowels and 'on'**

```python
s = 'example on for loop'
out = ''
for i in s:
    if i in 'aeiou' or i in 'on':
        out += i
print(out)
```

**12. Factorial using for loop**

```python
n = int(input("Enter a number: "))
f = 1
for i in range(1, n+1):
    f *= i
print("Factorial:", f)
```

**13. Perfect number check**

```python
n = int(input("Enter a number: "))
s = 0
for i in range(1, n):
    if n % i == 0:
        s += i
if s == n:
    print("Perfect number")
else:
    print("Not perfect")
```

**14. Armstrong number check**

```python
n = int(input("Enter a number: "))
sum = 0
temp = n
while temp > 0:
    digit = temp % 10
    sum += digit ** 3
    temp //= 10
if sum == n:
    print("Armstrong number")
else:
    print("Not an Armstrong number")
```

---

## That’s a wrap for today

It felt great revisiting loops. These are the core building blocks for real-world logic. Tomorrow, I’ll dig deeper into nested loops and maybe some pattern printing too.

See you in Day 24!

