---
description: medium
---

# Find Minimum in Rotated Sorted Array

## Question

[https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/description/](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/description/)

> Suppose an array of length `n` sorted in ascending order is **rotated** between `1` and `n` times. For example, the array `nums = [0,1,2,4,5,6,7]` might become:
>
> * `[4,5,6,7,0,1,2]` if it was rotated `4` times.
> * `[0,1,2,4,5,6,7]` if it was rotated `7` times.
>
> Notice that **rotating** an array `[a[0], a[1], a[2], ..., a[n-1]]` 1 time results in the array `[a[n-1], a[0], a[1], a[2], ..., a[n-2]]`.
>
> Given the sorted rotated array `nums` of **unique** elements, return _the minimum element of this array_.
>
> You must write an algorithm that runs in `O(log n) time.`
>
> &#x20;
>
> **Example 1:**
>
> <pre><code><strong>Input: nums = [3,4,5,1,2]
> </strong><strong>Output: 1
> </strong><strong>Explanation: The original array was [1,2,3,4,5] rotated 3 times.
> </strong></code></pre>

## How did I identify the pattern?

* We are asked to find a **minimum number** in a sorted array

## Intuition

* To solve this, we can use the **modified binary search pattern**.
* Initially, we assign the `start` and `end` to 1 and the maximum number in the array
* Find the middle. If the middle value is greater than end value, move the end to `middle - 1`,  else move the start to `middle + 1`

## Time and Space Complexity

Time Complexity: O(log N), where N is the length of the `nums`

Space Complexity: O(1)

## Solution

```python
class Solution:
    def findMin(self, nums: List[int]) -> int:
        # Initialize the start and end pointers
        start = 0
        end = len(nums)-1
        minimumValue = inf
        
        while start <= end:
        
            # Calculate mid and update the result
            mid = start + (end-start)//2
            minimumValue = min(minimumValue, nums[mid])
            
            # Update start and end conditionally
            if nums[mid] < nums[end]:
                end = mid-1
            else:
                start = mid+1
        
        # Return the result
        return minimumValue
```
