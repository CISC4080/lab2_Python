# **Lab 2: MergeSort, QuickSort, and QuickSelect**


## **Submission**

- Submit your file as **lab2.py** on **Autograder** (link here)

- **Due Date:** (TBD)

- **IMPORTANT!**

  - You pyhton file must be named exactly **lab2.py**.

  - Do not change any required function names since the test suite will call your functions by name. If you change the function names or parameters, your code will not be graded correctly.

  
## **Overview**

In this lab, you will implement three fundamental divide-and-conquer algorithms: **MergeSort**, **QuickSort**
and **QuickSelect**.

**Learning Objectives**

By the end of this lab, you should be able to:
1. Implement recursive divide-and-conquer algorithms.
2. Understand the partitioning strategy used in QuickSort and QuickSelect.
3. Distinguish between sorting and selection problems.

This lab consists of **two parts**:

## **Part I — Sorting Algorithms**

1. `MergeSort(arr, ascend=True)`
2. `QuickSort(arr, low, high, ascend=True)`
3. 
This parameter **ascend** controls the sorting order:

- If `ascend=True`, the array should be sorted in **ascending order**.
- If `ascend=False`, the array should be sorted in **descending order**.

Your implementation must use this flag to decide the comparison logic inside your algorithm (for example, when comparing two elements during merging or partitioning).

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

**Requirements**:

- Must use the same partition() logic as `QuickSort`.
- Must NOT fully sort the array.
- Only recurse into the side that may contain the k-th element.


## Running time analysis (Experimental Comparison)**

In this part, you will **measure the running time** of several algorithms and compare their performance as the input size grows. Your goal is to connect:

 
- **theoretical time complexity** (Big-O)
- with **real measured runtime** (seconds)

You will compare two categories of problems:


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


 

 

   
