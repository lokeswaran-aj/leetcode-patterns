---
description: Medium
---

# 3Sum

## Question

[https://leetcode.com/problems/3sum/description/](https://leetcode.com/problems/3sum/description/)

> Given an integer array nums, return all the triplets `[nums[i], nums[j], nums[k]]` such that `i != j`, `i != k`, and `j != k`, and `nums[i] + nums[j] + nums[k] == 0`.
>
> Notice that the solution set must not contain duplicate triplets.
>
> &#x20;
>
> **Example 1:**
>
> ```
> Input: nums = [-1,0,1,2,-1,-4]
> Output: [[-1,-1,2],[-1,0,1]]
> Explanation:
> nums[0] + nums[1] + nums[2] = (-1) + 0 + 1 = 0.
> nums[1] + nums[2] + nums[4] = 0 + 1 + (-1) = 0.
> nums[0] + nums[3] + nums[4] = (-1) + 2 + (-1) = 0.
> The distinct triplets are [-1,0,1] and [-1,-1,2].
> Notice that the order of the output and the order of the triplets does not matter.
> ```

## How did I identify the pattern?

* The input is a list
* We are asked to find the **three numbers** whose sum is equal to 0

## Intuition

* This problem is a superset of the [Two Sum](https://leetcode.com/problems/two-sum/description/) problem. To solve this, we can use the **two-pointer technique**.
* First of all, sort the input array so that we can use the two-pointer technique.
* Loop from the first value, then use two pointers denoted by `left` and `right`, where left is pointing to the `i+1` index and right is pointing to the last index initially.
* If the sum is greater than 0, the right index has to be decreased by one.
* If the sum is less than 0, the left index has to be increased by one.
* If the sum of the numbers corresponding to the i, left and right index results in `0`, append the list of `nums` at i, left and right.

> **Note:**
>
> * We can break the first loop when the nums\[i] is positive, because after the all the values will be more than 0. So you will not find a triplet.
> * When we find a triplet and incement the left by 1, we need to check if value of nums\[left] == nums\[left-1] and increment the left again to avoid duplicate triplets.

## Time and Space Complexity

Time Complexity: O(N\*N), where N is the length of the string `nums`

Space Complexity: O(1)

## Solution

```python
class Solution:
    def threeSum(self, nums: List[int]) -> List[List[int]]:
        result = []
        nums.sort()

        for i, num in enumerate(nums):
            if num>0:
                break
            if i>0 and num == nums[i-1]:
                continue

            # Initialize left and right pointers
            left = i+1
            right = len(nums)-1

            # Traverse the array with left and right pointers
            while left < right:
            
                # Move pointers inwards
                if nums[left] + nums[right] + num > 0:
                    right -= 1
                elif nums[left] + nums[right] + num < 0:
                    left += 1
                else:
                
                    # Update result or perform necessary operations
                    result.append([num, nums[left], nums[right]])
                    left += 1
                    right -= 1
                    while nums[left] == nums[left-1] and left < right:
                        left += 1

        # Return result based on the problem statement
        return result
```
