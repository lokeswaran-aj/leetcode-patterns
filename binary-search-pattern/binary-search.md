---
description: easy
---

# Binary Search

## Question

[https://leetcode.com/problems/binary-search/description/](https://leetcode.com/problems/binary-search/description/)

>
>
> Given an array of integers `nums` which is sorted in ascending order, and an integer `target`, write a function to search `target` in `nums`. If `target` exists, then return its index. Otherwise, return `-1`.
>
> You must write an algorithm with `O(log n)` runtime complexity.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code><strong>Input: nums = [-1,0,3,5,9,12], target = 9
> </strong><strong>Output: 4
> </strong><strong>Explanation: 9 exists in nums and its index is 4
> </strong></code></pre>

## How did I identify the pattern?

* We are asked to find a target in a sorted array.

## Intuition

* To solve this, we can use the **binary search pattern**.&#x20;
* Initially, we assign the `start` and `end` to 0 and the last index of the array.
* Loop until the start is less than or equal to the end.
* Find the `middle` index, then check if its value is the target, or else move the appropriate pointer.

## Time and Space Complexity

Time Complexity: O(log N), where N is the length of the `nums`

Space Complexity: O(1)

## Solution

```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        # Initialize the start and end pointers
        start = 0
        end = len(nums)-1
        
        while start <= end:
        
            # Calculate mid
            mid = start + (end - start) // 2
        
    
            # Check if the target is in the second half
            if nums[mid] < target:
                start = mid + 1
            # If the target is in the first half
            elif nums[mid] > target:
                end = mid - 1
            # If the target is in the middle
            else:
                return mid
        
        # Target not found
        return -1
```
