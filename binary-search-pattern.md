---
description: 'Mastering the Binary Search Pattern: A Comprehensive Guide'
---

# Binary Search Pattern

The binary search pattern is a powerful algorithmic approach used to efficiently search for a specific value in a **sorted array**. This technique follows a _divide-and-conquer_ strategy, continually reducing the search space by half until the target element is found or the search space is empty.

## How to identify binary search problems

Whenever we are given a sorted Array or Matrix, and we are asked to find a certain element, the best algorithm we can use is the Binary Search

## Real-world Applications

* Searching databases
* Search engines
* Sorting Algorithms like mergesort and quicksort

## Leetcode Examples

* [704. Binary Search](https://leetcode.com/problems/binary-search/)
* [153. Find Minimum in Rotated Sorted Array](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/)
* [33. Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/)

## Types of Binary Search Algorithms

1. Traditional binary search

## Python Template for the traditional binary search

```python
def traditionalBinarySearch(array):
    # Initialize the left and right pointers
    left = 0
    right = len(array)-1
    
    while left <= right:
    
        # Calculate mid
        mid = left + (right - left) // 2
    
        # Check if the target is in the middle
        if array[mid] == target:
            return mid
        # If the target is in the left half
        elif array[mid] > target:
            right = mid - 1
        # If the target is in the right half
        else:
            left = mid + 1
    
# Target not found
return -1
```

## Time and Space Complexity Analysis

**Time Complexity**

* Time complexity: O(log N), where N is the size of the input array or list.
* In each iteration, the search space is halved, leading to a logarithmic time complexity

**Space Complexity**

* Space complexity: O(1), as the algorithm typically uses a constant amount of extra space, regardless of the input size.
* The space required for variables like `left`, `right`, and `mid` remains constant.

\
