---
description: medium
---

# Search a 2D Matrix

## Question

[https://leetcode.com/problems/search-a-2d-matrix/description/](https://leetcode.com/problems/search-a-2d-matrix/description/)

> You are given an `m x n` integer matrix `matrix` with the following two properties:
>
> * Each row is sorted in non-decreasing order.
> * The first integer of each row is greater than the last integer of the previous row.
>
> Given an integer `target`, return `true` _if_ `target` _is in_ `matrix` _or_ `false` _otherwise_.
>
> You must write a solution in `O(log(m * n))` time complexity.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2020/10/05/mat.jpg)
>
> <pre><code><strong>Input: matrix = [[1,3,5,7],[10,11,16,20],[23,30,34,60]], target = 3
> </strong><strong>Output: true
> </strong></code></pre>

## How did I identify the pattern?

* We are asked to find a target in a sorted 2D array.

## Intuition

* This is very similar to the [704. Binary Search](binary-search.md) problem. To solve this, we can use the **binary search pattern**.&#x20;
* Initially, we assign the `start` and `end` to 0 and the number of `rows*columns -1` of the 2D array.
* Loop until the start is less than or equal to the end.
*   To find the middle value, calculate the `middle` index, then divide to get the row and modulo to get the column of the middle value.

    ```python3
    middleValue = matrix[mid//col][mid%col]
    ```
* Finally, check if its value is the target, or else move the appropriate pointer.

## Time and Space Complexity

Time Complexity: O(log M\*N), where M is the number of rows and N is the number of columns of the `matrix`

Space Complexity: O(1)

## Solution

```python
class Solution:
    def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:
        # Initialize the start and end pointers
        row = len(matrix)
        col = len(matrix[0])
        start = 0
        end = (row*col) - 1
        
        while start <= end:
    
            # Calculate mid
            mid = start + (end-start)//2
            middleValue = matrix[mid//col][mid%col]
            
            # Check if the target is in the second half
            if middleValue < target:
                start = mid + 1
            # If the target is in the first half
            elif middleValue > target:
                end = mid - 1
            # If the target is in the middle
            else:
                return True
        # Target not found
        return False
```
