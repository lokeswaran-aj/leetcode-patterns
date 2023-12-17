---
description: hard
---

# 42. Trapping Rain Water

## Question

[https://leetcode.com/problems/trapping-rain-water/description/](https://leetcode.com/problems/trapping-rain-water/description/)

>
>
> Given `n` non-negative integers representing an elevation map where the width of each bar is `1`, compute how much water it can trap after raining.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2018/10/22/rainwatertrap.png)
>
> <pre><code><strong>Input: height = [0,1,0,2,1,0,1,3,2,1,2,1]
> </strong><strong>Output: 6
> </strong><strong>Explanation: The above elevation map (black section) is represented by array [0,1,0,2,1,0,1,3,2,1,2,1]. In this case, 6 units of rain water (blue section) are being trapped.
> </strong></code></pre>

## How did I identify the pattern?

* The input is a list
* We can use the **two pointers** to find the amount of water that can be trapped between them.

## Intuition

* To solve this, we can use the **two-pointer technique**.
* Use two pointers denoted by `left` and `right`, where left is pointing to the first index and right is pointing to the last index initially.
* Use `leftMax` and `rightMax` pointing to left and right values initially.
* Check if leftMax or rightMax is smaller, calculate its new max and check the difference between the max and current height for the trapped amount and update the total.

## Time and Space Complexity

Time Complexity: O(N), where N is the length of the string `height`

Space Complexity: O(1)

## Solution

```python
class Solution:
    def trap(self, height: List[int]) -> int:
        # Initialize left and right pointers
        total = 0
        left = 0
        right = len(height)-1
        leftMax = height[left]
        rightMax = height[right]

        # Traverse the array with left and right pointers
        while left < right:

            # Move pointers inwards
            if leftMax < rightMax:
                left += 1
                
                # Update result or perform necessary operations
                leftMax = max(leftMax,height[left])
                total += (leftMax-height[left])
            else:
                right -= 1
                rightMax = max(rightMax,height[right])
                total += (rightMax-height[right])

        # Return result based on the problem statement
        return total
```
