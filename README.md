# Algorithm Analysis using Big O Notation
## Name: Maitraiyee Vashistha
## PRN: 24070123057
## Division: ENTC-A3
## Title: Understanding Algorithm Analysis using Big O Notation in C++
-----
## Overview
Big O notation is a mathematical framework that describes the **efficiency** of algorithms. It helps us measure:
- **Time Complexity** – how execution time grows with input size.
- **Space Complexity** – how memory usage grows with input size.

Instead of measuring exact seconds, Big O focuses on **growth trends**. This makes it possible to compare algorithms across machines and scales.

Big O answers questions like:
- If I double my input size, how much slower does my algorithm get?
- Is my algorithm practical for large datasets?
- Should I use Binary Search or Linear Search?

---

## O(1) – Constant Time

### Theory
- **Definition:** An algorithm runs in constant time if its execution does not depend on input size.
- **Key Idea:** No matter how big the dataset is, the algorithm finishes in the same number of steps.
- **Analogy:** Picking the first item in your fridge. The fridge could be full or empty, but the action takes the same time.
- **Use Cases:**
  - Accessing an element in an array by index
  - Pushing/Popping from the top of a stack
  - Hash table insertion or lookup (average case)

### Example Program
Logic: Access the first element of an array directly. Even if the array has millions of elements, the lookup is instant.

```
def get_first_element(arr):
    return arr[0]
```
---

## O(log n) – Logarithmic Time

### Theory
- **Definition:** Algorithms that reduce the problem size by half (or a constant fraction) at every step run in logarithmic time.
- **Key Idea:** Each operation eliminates a huge portion of the data, making the algorithm extremely efficient for large inputs.
- **Analogy:** Looking for a word in a dictionary by flipping to the middle, then halving again.
- **Use Cases:**
  - Binary Search
  - Searching/Insertion in balanced binary search trees (AVL, Red-Black)
  - Efficient divide-and-conquer algorithms

### Example Program
Logic: Binary Search finds an element in a sorted array by repeatedly halving the search space until the target is found or the range is empty.
```
def binary_search(arr, target):
    left, right = 0, len(arr) - 1
    while left <= right:
        mid = (left + right) // 2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    return -1
```
---

## O(n) – Linear Time

### Theory
- **Definition:** An algorithm runs in linear time if execution time grows directly in proportion to the input size.
- **Key Idea:** Every single element must be checked or processed once.
- **Analogy:** Checking every page of a book until you find a specific word. Twice as many pages means twice as long.
- **Use Cases:**
  - Linear Search in unsorted arrays
  - Summing all elements in an array
  - Traversing a list to find min/max

### Example Program
Logic: Linear Search scans every element of an array until it finds the target.
```
def linear_search(arr, target):
    for i in range(len(arr)):
        if arr[i] == target:
            return i
    return -1
```
---

## O(n²) – Quadratic Time

### Theory
- **Definition:** Runtime grows proportional to the square of input size. This often happens with algorithms that use **nested loops**.
- **Key Idea:** If input doubles, work increases fourfold.
- **Analogy:** Checking every pair of students in a class to see who can be partners. With more students, combinations explode.
- **Use Cases:**
  - Bubble Sort, Insertion Sort, Selection Sort
  - Checking all pairs in a dataset
  - Naïve matrix multiplication

### Example Program
Logic: Bubble Sort repeatedly swaps adjacent elements if they are in the wrong order.
```
def bubble_sort(arr):
    n = len(arr)
    for i in range(n):
        for j in range(0, n - i - 1):
            if arr[j] > arr[j + 1]:
                arr[j], arr[j + 1] = arr[j + 1], arr[j]
    return arr
```
---

## O(2ⁿ) – Exponential Time

### Theory
- **Definition:** Exponential algorithms double in runtime with each additional input.
- **Key Idea:** Quickly becomes impractical even for small input sizes.
- **Analogy:** Doubling the number of light switches and checking all possible on/off combinations.
- **Use Cases:**
  - Recursive Fibonacci (naïve)
  - Solving the Traveling Salesman Problem with brute force
  - Exhaustive search problems

### Example Program
Logic: Recursive Fibonacci calculates fib(n) as fib(n-1) + fib(n-2). This causes massive recomputation.
```
def fibonacci(n):
    if n <= 1:
        return n
    return fibonacci(n - 1) + fibonacci(n - 2)
```
---

## O(n!) – Factorial Time

### Theory
- **Definition:** Factorial complexity grows faster than exponential. For n inputs, it tries all n! permutations.
- **Key Idea:** Useful only for very small datasets.
- **Analogy:** Trying every possible seating arrangement for a group of friends.
- **Use Cases:**
  - Solving Traveling Salesman Problem exactly
  - Generating all permutations of a dataset

### Example Program
Logic: Recursive function generates all permutations of a given string.
```
def permute(s, l, r):
    if l == r:
        print("".join(s))
    else:
        for i in range(l, r + 1):
            s[l], s[i] = s[i], s[l]
            permute(s, l + 1, r)
            s[l], s[i] = s[i], s[l]
```
---

## Conclusion

Big O notation gives a **mathematical lens** to evaluate and compare algorithms. By understanding O(1), O(log n), O(n), O(n²), O(2ⁿ), and O(n!), we can:
- Predict scalability of algorithms
- Choose efficient solutions for large inputs
- Avoid impractical algorithms for real-world problems

Efficient algorithms are not just faster – they are often the difference between something being **usable** and **impossible**.
