# **Lab 2: MergeSort, QuickSort, and QuickSelect**

## **Overview**

In this lab, you will implement three fundamental divide-and-conquer algorithms: **MergeSort**, **QuickSort**
and **QuickSelect**.

**Learning Objectives**

By the end of this lab, you should be able to:
1. Implement recursive divide-and-conquer algorithms.
2. Understand the partitioning strategy used in QuickSort and QuickSelect.
3. Distinguish between sorting and selection problems.

## Detailed Requirements**

1. For both sort functions, the parameter **ascend** controls the sorting order:

 `MergeSort(arr, ascend=True)`
 `QuickSort(arr, low, high, ascend=True)`
   
- If `ascend=True`, the array should be sorted in **ascending order**.
- If `ascend=False`, the array should be sorted in **descending order**.

Your implementation must use this flag to decide the comparison logic inside your algorithm (for example, when comparing two elements during merging or partitioning).

2. Your implementation of **MergeSort** must:

- Use recursion
- Divide the list into two halves
- Recursively sort both halves
- Merge them into a sorted list
- Return a **new sorted list**, note that this is different from the MergeSort we studied in class. 

- **Do NOT use Python built-in sorting (sorted() or .sort()).**
- **Expected Complexity**

- Time Complexity: **$O(n\log n$)**
- Space Complexity: **$O(n)$**


3. For the **QuickSort** function: 

```python
def QuickSort(arr, low, high, ascend=True):
```

Please: 
 - define the partition function as follows, and perform **in-place** partition. 
```python
def partition(arr, low, high, ascend=True):
```
- Select a pivot (randomly, use `random` library)
- Partition elements around pivot
- Recursively sort subarrays
- **Expected Complexity**: Best/Average: $**O(n \log n)$**, and Worst: $**O(n²)**$

4. The **QuickSelect** to find the k-th smallest element.

```python
def quick_select(arr, low, high, k):
```

 -- Return the **k-th smallest element** in the array (0-based index).

Example:

```python
arr = [7, 2, 9, 4, 1]
quick_select(arr, 0, len(arr)-1, 2)
```

should return

```
4
```

- Must call the partition()
- Must NOT fully sort the array.
- Only recurse into the side that may contain the k-th element.


## **Submission**

- Submit your file as **lab2.py** on **Autograder** (link here)

- **Due Date:** (TBD)

- **IMPORTANT!**

  - You pyhton file must be named exactly **lab2.py**.

  - Do not change any required function names since the test suite will call your functions by name. If you change the function names or parameters, your code will not be graded correctly.
 

 

   
