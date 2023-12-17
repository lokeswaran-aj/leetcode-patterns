---
description: medium
---

# Container With Most Water

## Question

[https://leetcode.com/problems/container-with-most-water/description/](https://leetcode.com/problems/container-with-most-water/description/)

> You are given an integer array `height` of length `n`. There are `n` vertical lines drawn such that the two endpoints of the `ith` line are `(i, 0)` and `(i, height[i])`.
>
> Find two lines that together with the x-axis form a container, such that the container contains the most water.
>
> Return _the maximum amount of water a container can store_.
>
> **Notice** that you may not slant the container.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://s3-lc-upload.s3.amazonaws.com/uploads/2018/07/17/question\_11.jpg)
>
> <pre><code><strong>Input: height = [1,8,6,2,5,4,8,3,7]
> </strong><strong>Output: 49
> </strong><strong>Explanation: The above vertical lines are represented by array [1,8,6,2,5,4,8,3,7]. In this case, the max area of water (blue section) the container can contain is 49.
> </strong></code></pre>

## How did I identify the pattern?

* The input is a list
* We are asked to find the **two indices** such that the amount of water between them is the maximum.

## Intuition

* To solve this, we can use the **two-pointer technique**.
* Use two pointers denoted by `left` and `right`, where left is pointing to the first index and right is pointing to the last index initially.
* To calculate the `current amount`, take the _minimum_ height value between left and right height and multiply it by the _difference_ in the left and right index.
* Update the result if the current amount is _greater than_ the result.
* Check which height is smaller and move that pointer inwards.

## Time and Space Complexity

Time Complexity: O(N), where N is the length of the string `heights`

Space Complexity: O(1)

## Solution

```python
class Solution:
    def maxArea(self, height: List[int]) -> int:
        # Initialize left and right pointers
        left = 0
        right= len(height)-1
        maxAmount = 0
    
        # Traverse the array with left and right pointers
        while left < right:

            # Update result or perform necessary operations
            currAmount = min(height[left], height[right]) * (right-left)
            maxAmount = max(maxAmount,currAmount)

            # Move pointers inwards
            if height[left]<height[right]:
                left += 1
            else:
                right -= 1

        # Return result based on the problem statement
        return maxAmount
```
