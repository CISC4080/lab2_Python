# **Lab 2: Sorting and Selection: MergeSort, QuickSort, and QuickSelect**



**Course:** CISC 4080 – Computer Algorithms

**Instructor:** Prof. Xiaolan Zhang



## **Submission**



- Submit your file as **lab2.py** on **Autograder** (link here)

- **Due Date:** (TBD)

- **IMPORTANT!**

  - You pyhton file must be named exactly **lab2.py**.

  - Do not change any required function names since the test suite will call your functions by name. If you change the function names or parameters, your code will not be graded correctly.

    

## **Overview**

In this lab, you will implement and analyze three fundamental divide-and-conquer algorithms:

- **MergeSort**
- **QuickSort**
- **QuickSelect**



**Learning Objectives**

By the end of this lab, you should be able to:

1. Implement recursive divide-and-conquer algorithms.
2. Understand the partitioning strategy used in QuickSort and QuickSelect.
3. Distinguish between sorting and selection problems.



This lab consists of **two parts**:

## **Part I — Sorting Algorithms**

1. `MergeSort(arr, ascend=True)`
2. `QuickSort(arr, low, high, ascend=True)`

Both sorting functions include a parameter:

```python
ascend=True
```

This parameter controls the sorting order:

- If `ascend=True`, the array should be sorted in **ascending order**.
- If `ascend=False`, the array should be sorted in **descending order**.

Your implementation must use this flag to decide the comparison logic inside your algorithm (for example, when comparing two elements during merging or partitioning).



### **Task 1: MergeSort**

Your function must be named as:

```python
def MergeSort(arr, ascend=True):
```

**Requirements**

Your implementation must:

- Use recursion
- Divide the list into two halves
- Recursively sort both halves
- Merge them into a sorted list
- Return a **new sorted list**

- **Do NOT use Python built-in sorting (sorted() or .sort()).**
- You may implement a helper function:

```python
def merge(left, right, ascend=True):
```



**Expected Complexity**

- Time Complexity: **$O(n\log n$)**
- Space Complexity: **$O(n)$**

### 

### **Task 2: QuickSort**:

```python
def QuickSort(arr, low, high, ascend=True):
```

You must also implement:

```python
def partition(arr, low, high, ascend=True):
```



**Requirements:**

- Use **in-place** partitioning
- Select a pivot (randomly, use `random` library)
- Partition elements around pivot
- Recursively sort subarrays



**Expected Complexity**

- Best/Average: $**O(n \log n)$**
- Worst: $**O(n²)**$





## **Part II — Selection Algorithm**



Now you will implement **QuickSelect** to find the k-th smallest element.

```python
def quick_select(arr, low, high, k):
```

**Description**

Return the **k-th smallest element** in the array (0-based index).

Example:

```python
arr = [7, 2, 9, 4, 1]
quick_select(arr, 0, len(arr)-1, 2)
```

should return

```
4
```

Because sorted array is `[1,2,4,7,9]`, and index 2 is 4.



**Requirements**:

- Must use the same partition() logic as `QuickSort`.
- Must NOT fully sort the array.
- Only recurse into the side that may contain the k-th element.





## **Part III — Running time analysis (Experimental Comparison)**

In this part, you will **measure the running time** of several algorithms and compare their performance as the input size grows. Your goal is to connect:



- **theoretical time complexity** (Big-O)
- with **real measured runtime** (seconds)



You will compare two categories of problems:

1. **Searching**: Linear Search vs Binary Search
2. **Selection**: QuickSelect vs Sort-then-Index



### **A. Searching**

1. **Linear Search** (scan from left to right)

   - Expected time: **O(n)**

2. **Binary Search** (divide-and-conquer on a sorted array)

   - Expected time: **O(log n)**
   - Requires the array to already be sorted

   

You must implement the following functions

```python
def linear_search(arr, target):
    """
    Return the index of target in arr if found, otherwise return -1.
    """
```

```python
def binary_search(arr, target):
    """
    arr is sorted.
    Return the index of target in arr if found, otherwise return -1.
    """
```



### **B. Selection (k-th smallest element)**

1. **QuickSelect** (from Part II)

   - Expected average time: **O(n)**

2. **Sort first, then index** (Using either the MergeSort or QuickSort you implemented )

   - Sort the entire array, then return arr[k]
   - Expected time: $**O(n\log n)**$ due to sorting

   

You must implement the following function:

```python
def sort_then_index(arr, k, ascend=True):
    """
    Return the k-th smallest element (0-based) by sorting the whole array first.
    You may call your MergeSort or QuickSort from Part I (do NOT use Python sorted()).
    """
```

 You will also reuse your existing:

```python
def quick_select(arr, low, high, k):
```



### **Experimental Setup**

You will test the algorithms on arrays of increasing size:

- n = 1,000
- n = 5000
- n = 10,000
- n = 50,000
- n = 100,000
- n = 500,000
- n = 1,000,000 *(optional if your computer is slow)*
- 

### **Data Generation Rules**

Use Python’s random library to generate test arrays:

- **For searching**:

  - Use a **sorted** array for binary search
  - Use the same data for linear search for fairness

- **For selection**:

  - Use a random array (unsorted)
  - Choose k = n // 2 (median index) for consistency

  

### **Timing Method (Important for Fair Comparison)**



To reduce noise, you must:

- Run each algorithm **multiple times** (e.g., 10 trials)
- Report the **average time**
- Use time.perf_counter() for accurate timing

Example timing structure:

```python
import time

start = time.perf_counter()
# run algorithm
end = time.perf_counter()
elapsed = end - start
```



#### **What to Record**

Create a table like this (in your write-up):

### **Searching Results**

|   **n**   | **Linear Search Time** | **Binary Search Time** |
| :-------: | :--------------------: | :--------------------: |
|   1,000   |           …            |           …            |
|   5,000   |                        |                        |
|  10,000   |           …            |           …            |
|  50,000   |                        |                        |
|  100,000  |           …            |           …            |
|  500,000  |                        |                        |
| 1,000,000 |           …            |           …            |



### **Selection Results**

|   **n**   | **QuickSelect Time** | **Sort-then-Index Time** |
| :-------: | :------------------: | :----------------------: |
|   1,000   |          …           |            …             |
|   5,000   |                      |                          |
|  10,000   |          …           |            …             |
|  50,000   |                      |                          |
|  100,000  |          …           |            …             |
|  500,000  |                      |                          |
| 1,000,000 |          …           |            …             |



### **Analysis **

1. **Linear vs Binary Search:**

   As n increases, which algorithm grows faster in runtime?

   Does your result match **O(n)** vs **O(log n)**? Explain why.

2. **QuickSelect vs Sort-then-Index:**

   Why is QuickSelect often faster than sorting the entire array first?

   