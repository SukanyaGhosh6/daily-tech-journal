# Day 11: Python Revision – Operators, Arithmetic, and Modular Math Practice

Since I’ve been revisiting basic Python concepts like arithmetic operators, modular math, and number properties, today I focused on solving some small but powerful problems to apply those ideas. These problems helped me connect basic syntax with real logic building — and honestly, it felt like a productive warm-up session.

Here are the problems I tackled today, along with their solutions and the ideas behind them.

---

## Problem 1: Addition Under Modulo

### Task:
Given two large integers `a` and `b`, find their sum under modulo `10^9 + 7`

### Why Modulo?
Large numbers can overflow or exceed storage, so we reduce the result under a limit (`MOD = 10^9 + 7`), which is a big prime commonly used in programming contests.

### Code:
```python
class Solution:
    def sumUnderModulo(self, a, b):
        MOD = 10**9 + 7
        return (a % MOD + b % MOD) % MOD
```

---

## Problem 2: Multiplication Under Modulo

### Task:
Multiply two large numbers and return the result under `10^9 + 7`.

### Code:
```python
class Solution:
    def multiplicationUnderModulo(self, a, b):
        MOD = 10**9 + 7
        return ((a % MOD) * (b % MOD)) % MOD
```

---

## Problem 3: Modular Inverse

### Task:
Find a number `x` such that `(a * x) % m == 1`.

This is known as the **modular inverse** of `a` under `m`.

### Code:
```python
class Solution:
    def modInverse(self, a, m):
        for x in range(1, m):
            if (a * x) % m == 1:
                return x
        return -1
```

---

## Problem 4: Digits in Factorial

### Task:
Find the number of digits in `N!` without calculating the factorial directly.

### Idea:
Use logarithms to estimate size:
- `log10(2 * 3 * 4 ... * N)` = `log10(2) + log10(3) + ... + log10(N)`
- Number of digits = `floor(sum) + 1`

### Code:
```python
import math
class Solution:
    def digitsInFactorial(self, N):
        if N == 0 or N == 1:
            return 1
        digits = 0
        for i in range(2, N + 1):
            digits += math.log10(i)
        return math.floor(digits) + 1
```

---

## Problem 5: Check if a Number is Prime

### Task:
Check if a given number `N` is prime using an optimized method.

### Code:
```python
class Solution:
    def isPrime(self, N):
        if N == 1:
            return False
        if N == 2 or N == 3:
            return True
        if N % 2 == 0 or N % 3 == 0:
            return False
        i = 5
        while i * i <= N:
            if N % i == 0 or N % (i + 2) == 0:
                return False
            i += 6
        return True
```

---

## Problem 6: Exactly 3 Divisors

### Task:
Count how many numbers ≤ N have exactly 3 divisors.

### Key Idea:
Only numbers that are **squares of prime numbers** have exactly 3 divisors:  
`1, p, p²`

So we:
- Loop from 2 to √N
- If the number is prime, check if its square ≤ N
- Count it

### Code:
```python
import math

class Solution:
    def is_prime(self, num):
        if num < 2:
            return False
        if num == 2 or num == 3:
            return True
        if num % 2 == 0 or num % 3 == 0:
            return False
        i = 5
        while i * i <= num:
            if num % i == 0 or num % (i + 2) == 0:
                return False
            i += 6
        return True

    def exactly3Divisors(self, N):
        count = 0
        for i in range(2, int(math.sqrt(N)) + 1):
            if self.is_prime(i):
                if i * i <= N:
                    count += 1
        return count
```

---

## Final Thoughts:

These problems were all pretty simple, but they reinforced a lot of core concepts:
- How to apply modulo for safe calculations
- How to use `log10` instead of multiplying huge numbers
- How to identify numbers based on their divisors or structure (like primes and their squares)

 On to more practice tomorrow!
