---
description: medium
---

# Search in Rotated Sorted Array

## Question

[https://leetcode.com/problems/search-in-rotated-sorted-array/description/](https://leetcode.com/problems/search-in-rotated-sorted-array/description/)

> There is an integer array `nums` sorted in ascending order (with **distinct** values).
>
> Prior to being passed to your function, `nums` is **possibly rotated** at an unknown pivot index `k` (`1 <= k < nums.length`) such that the resulting array is `[nums[k], nums[k+1], ..., nums[n-1], nums[0], nums[1], ..., nums[k-1]]` (**0-indexed**). For example, `[0,1,2,4,5,6,7]` might be rotated at pivot index `3` and become `[4,5,6,7,0,1,2]`.
>
> Given the array `nums` **after** the possible rotation and an integer `target`, return _the index of_ `target` _if it is in_ `nums`_, or_ `-1` _if it is not in_ `nums`.
>
> You must write an algorithm with `O(log n)` runtime complexity.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code><strong>Input: nums = [4,5,6,7,0,1,2], target = 0
> </strong><strong>Output: 4
> </strong></code></pre>

## How did I identify the pattern?

* We are asked to find a target **number** in a sorted array

## Intuition

* To solve this, we can use the **binary search pattern**.
* Initially, we assign the `start` and `end` to first and last index
* Find the middle. If the middle value is the target, return the index.
* Or else, find out if the `middle` index is in the left or right-sorted portion.
* If it is in the left-sorted portion, check if the target is greater than the middle value or less than start value, then move the start pointer; else, move the end pointer
* If it is in the right sort portion, check if the target is less than the middle value or greater than the right value, then move the end pointer; otherwise,  move the start pointer.

## Time and Space Complexity

Time Complexity: O(N), where N is the length of the `nums`

Space Complexity: O(1)

## Solution

```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        # Initialize the start and end pointers
        start = 0
        end = len(nums)-1
        while start <= end:
        
            # Calculate mid and update the result
            middle = start + (end-start)//2
            if nums[middle] == target:
                return middle

            # Find if the middle is in left or right sorted portion
            if nums[start] <= nums[middle]:
                # Update start and end conditionally
                if target > nums[middle] or target < nums[start]:
                    start = middle + 1
                else:
                    end = middle - 1
            else:
                # Update start and end conditionally
                if target < nums[middle] or target > nums[end]:
                    end = middle - 1
                else:
                    start = middle + 1
                    
        # Result not found
        return -1

```
