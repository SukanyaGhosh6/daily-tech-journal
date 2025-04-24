# Day 10: Brushing Up Python Basics Through Contests

Today I thought, instead of just revising Python concepts by flipping through notes, I’d actually try applying them — so I jumped into a GeeksforGeeks practice contest.

Honestly, this kind of contest-based revision helps me a lot. It’s like mini-challenges that force you to think, code, and learn *on the spot* — which feels way more fun than just reading theory.

Since I’m still in the early stages of revision, I picked some beginner-level problems. Here are two of them I solved today — along with the concept and thought process behind them.

---

##  Problem 1: Non-Palindromes

### Scenario:
Imagine you're building a filter for a digital diary app, and you want to exclude numbers that look the same from both ends — basically, **palindromes**.

So, given a number `n`, the task is to count how many numbers from `1` to `n` are **not palindromes**.

### What is a palindrome?
It’s just a number (or word) that reads the same forwards and backwards.  
Examples: `121`, `4`, `99` are palindromes.  
`12`, `123`, `45` are not.

### Approach:
We just loop from `1` to `n`, and for each number:
- Convert it to a string
- Reverse it
- Compare both
- If it’s not equal → it’s a **non-palindrome**

### Code:
```python
def nonPalindromic(n):
    count = 0
    for i in range(1, n+1):
        str_i = str(i)
        if str_i != str_i[::-1]:
            count += 1
    return count
```

This one’s all about string manipulation. The slicing trick `[::-1]` is a Pythonic way to reverse a string.

---

## 🧠 Problem 2: Count Prime Factors

### Scenario:
Let’s say you’re writing code for a math learning app, and it needs to highlight the **prime factors** of any given number.

Given a number `n`, we’re asked to count how many **distinct prime factors** it has.

### Reminder:
A **prime factor** is a prime number that divides the number exactly.

#### Example:
For `n = 10`, its factors are `{1, 2, 5, 10}`  
But only `{2, 5}` are prime. So output = `2`.

### Approach:
- Start dividing `n` by small numbers (from `2` onwards)
- For each number `i`, divide `n` until `i` no longer divides it
- If it divides once → count it as a prime factor
- If any part of `n` remains at the end → it’s also a prime

### Code:
```python
def primeDivisorsCount(n):
    count = 0
    i = 2
    while i * i <= n:
        if n % i == 0:
            count += 1
            while n % i == 0:
                n //= i
        i += 1
    if n > 1:
        count += 1
    return count
```

This is a classic number theory problem. The key trick is to use the fact that once you factor out smaller primes, any large leftover `n` is itself a prime.

---

## Final Thoughts

It felt good solving these small but brain-itching problems. At this stage of revision, I’m not aiming for speed or complexity — just for **clarity and consistency**. Writing and debugging even these beginner problems helps reinforce the core Python skills and logic patterns.

I think I’ll make this a regular part of my routine — solve 2–3 problems from contests as I go, and note down what I learned.

Until the next one!
