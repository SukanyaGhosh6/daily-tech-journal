# Day 14 - Problem Solving with Arrays in Python

Today, I worked on a series of array problems that helped me sharpen my problem-solving skills with Python. Arrays are such a fundamental part of programming, and tackling these problems has given me a deeper understanding of how to manipulate them efficiently. In this article, I’ll walk you through the problems I solved and how I approached each one with Python.

## 1. **Insert an Element at the End of an Array**

The first problem I tackled was inserting an element at the end of an array. This is a simple task, and in Python, it’s pretty straightforward using the `append()` method.

### Solution:
```python
def insert_at_end(arr, element):
    arr.append(element)
    return arr

arr = [1, 2, 3]
print(insert_at_end(arr, 4))  # Output: [1, 2, 3, 4]
```

It’s as simple as calling `arr.append(element)`, and that adds the element to the end of the array. I felt like this was one of the easier problems, but it’s good practice to reinforce the basics.

## 2. **Insert an Element at a Specific Index in an Array**

Next, I worked on inserting an element at a specific index. The task was to write a function that would insert an element into an array at the given index.

### Solution:
```python
def insert_at_index(arr, index, element):
    arr.insert(index, element)
    return arr

arr = [1, 2, 3, 4]
print(insert_at_index(arr, 2, 10))  # Output: [1, 2, 10, 3, 4]
```

Here, I used the `insert()` method, which allows me to specify the index where the element should go. It was pretty intuitive once I started using it.

## 3. **Delete an Element and Shift the Array**

This one was about deleting an element at a specific index and shifting the rest of the array elements to fill the gap. This is an important operation because it requires shifting elements, something I had to implement manually in some other languages, but Python does it quite easily.

### Solution:
```python
def delete_and_shift(arr, index):
    if 0 <= index < len(arr):
        del arr[index]
    return arr

arr = [1, 2, 3, 4, 5]
print(delete_and_shift(arr, 2))  # Output: [1, 2, 4, 5]
```

I used the `del` statement to remove the element at the given index, and the array is automatically shifted.

## 4. **Calculate the Mean of an Array**

The next challenge was calculating the mean of an array. This is pretty simple and involves summing up the array’s elements and dividing by the length of the array.

### Solution:
```python
def mean_of_array(arr):
    return sum(arr) / len(arr) if len(arr) > 0 else 0

arr = [1, 2, 3, 4]
print(mean_of_array(arr))  # Output: 2.5
```

This was a nice way to practice working with basic statistics in Python. I made sure to handle the case where the array might be empty.

## 5. **Find the Median of an Array**

Finding the median was an interesting one. I had to sort the array first and then find the middle element (or the average of the two middle elements if the array size is even). 

### Solution:
```python
def median_of_array(arr):
    arr.sort()
    n = len(arr)
    if n % 2 == 0:
        return (arr[n//2 - 1] + arr[n//2]) / 2
    else:
        return arr[n//2]

arr = [1, 3, 2, 4]
print(median_of_array(arr))  # Output: 2.5
```

Sorting the array first was the key step, and then it was a matter of checking whether the array length was odd or even to decide how to calculate the median.

## 6. **Count Elements Smaller Than X**

For this problem, I had to count how many elements in the array are smaller than a given value X. This is something I’ve encountered in many coding challenges, so it felt familiar.

### Solution:
```python
def count_smaller_than_x(arr, x):
    return sum(1 for elem in arr if elem < x)

arr = [1, 2, 3, 4, 5]
print(count_smaller_than_x(arr, 4))  # Output: 3
```

I used a generator expression to loop through the array and count how many elements are smaller than X. This is a very efficient approach in Python.

## 7. **Find the Immediate Smaller Element Than X**

This one was about finding the element immediately smaller than a given value X in the array. It took a little thinking, but sorting the array first helped a lot.

### Solution:
```python
def immediate_smaller_than_x(arr, x):
    arr_sorted = sorted(arr)
    for elem in arr_sorted:
        if elem >= x:
            break
    return arr_sorted[arr_sorted.index(elem) - 1] if elem > x else None

arr = [5, 1, 3, 2, 4]
print(immediate_smaller_than_x(arr, 4))  # Output: 3
```

After sorting, I just found the first element that was greater than or equal to X and returned the element just before it. 

## 8. **Count Elements Greater Than X**

This problem was pretty similar to the one about counting smaller elements, but now we’re counting how many elements are greater than X.

### Solution:
```python
def count_greater_than_x(arr, x):
    return sum(1 for elem in arr if elem > x)

arr = [1, 2, 3, 4, 5]
print(count_greater_than_x(arr, 3))  # Output: 2
```

Again, I used a generator expression, which is perfect for this kind of counting task.

## 9. **Find the Immediate Greater Element Than X**

For this problem, I needed to find the element that is immediately greater than X. This required sorting the array, just like when we were looking for the immediate smaller element.

### Solution:
```python
def immediate_greater_than_x(arr, x):
    arr_sorted = sorted(arr)
    for elem in arr_sorted:
        if elem > x:
            return elem
    return None

arr = [5, 1, 3, 2, 4]
print(immediate_greater_than_x(arr, 3))  # Output: 4
```

It was a simple approach: after sorting the array, I just looked for the first element greater than X.

## 10. **Who Has Majority?**

This problem was about finding the majority element, which appears more than half the time in the array. I used the `Counter` from the `collections` module to make this task easier.

### Solution:
```python
from collections import Counter

def majority_element(arr):
    count = Counter(arr)
    majority_count = len(arr) // 2
    for elem, cnt in count.items():
        if cnt > majority_count:
            return elem
    return None

arr = [1, 2, 2, 3, 2]
print(majority_element(arr))  # Output: 2
```

By counting the occurrences of each element, I could easily find the one that appears more than half the time.

## 11. **Check if the Array is Sorted**

This one was simple: I just needed to check if the array is sorted in ascending order. I used Python’s built-in `sorted()` function to compare the array with its sorted version.

### Solution:
```python
def is_array_sorted(arr):
    return arr == sorted(arr)

arr = [1, 2, 3, 4, 5]
print(is_array_sorted(arr))  # Output: True
```

It felt like a quick check that could be useful for a variety of problems.

## 12. **Rotate the Array**

Next, I worked on rotating the array by a given number of positions. I figured out that I can slice the array and rearrange it in just a few lines.

### Solution:
```python
def rotate_array(arr, k):
    return arr[k:] + arr[:k]

arr = [1, 2, 3, 4, 5]
print(rotate_array(arr, 2))  # Output: [3, 4, 5, 1, 2]
```

This method worked perfectly by taking the array from index `k` to the end and then adding the beginning part before `k`.

## 13. **Get Element at a Specific Index**

Here, I just had to retrieve the element at a specific index. I made sure to handle the case where the index is out of range.

### Solution:
```python
def get_element_at_index(arr, index):
    if 0 <= index < len(arr):
        return arr[index]
    return None

arr = [1, 2, 3, 4, 5]
print(get_element_at_index(arr, 2))  # Output: 3
```

It was a simple task, but a good exercise in handling array indices safely.

## 14. **Find Maximum and Minimum in an Array**

The next problem involved finding both the maximum and minimum elements in an array. I used Python’s built-in `max()` and `min()` functions for this one.

### Solution:
```python
def find_max_min(arr):
    return max(arr), min(arr)

arr = [1, 2, 3, 4, 5]
print(find_max_min(arr))  # Output: (5, 1)
```

These built-in functions are really efficient for this task, and I didn’t need to write much code to get the results.

## 15. **Reverse the Array**

Finally, I worked on reversing the array. This is one of the most basic operations, and Python makes it incredibly easy with slicing.

### Solution:
```python
def reverse_array(arr):
    return arr[::-1]

arr = [1, 2, 3, 4, 5]
print(reverse_array(arr))  # Output: [5, 4, 3, 2, 1]
```

Using Python's slicing, reversing an array was done in one line. Super easy!

---

That’s it for today’s array problems! I feel like I’ve practiced a solid set of array manipulation techniques, and these are definitely things I’ll keep in mind for future coding challenges and interviews. 
