---
description: medium
---

# Two Sum II - Input Array Is Sorted

## Question

[https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/description/](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/description/)

> Given a **1-indexed** array of integers `numbers` that is already _**sorted in non-decreasing order**_, find two numbers such that they add up to a specific `target` number. Let these two numbers be `numbers[index1]` and `numbers[index2]` where `1 <= index1 < index2 < numbers.length`.
>
> Return _the indices of the two numbers,_ `index1` _and_ `index2`_, **added by one** as an integer array_ `[index1, index2]` _of length 2._
>
> The tests are generated such that there is **exactly one solution**. You **may not** use the same element twice.
>
> Your solution must use only constant extra space.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code><strong>Input: numbers = [2,7,11,15], target = 9
> </strong><strong>Output: [1,2]
> </strong><strong>Explanation: The sum of 2 and 7 is 9. Therefore, index1 = 1, index2 = 2. We return [1, 2].
> </strong></code></pre>

## How did I identify the pattern?

* The input is a list
* We are asked to find the **two number whose sum is equal to a target**

## Intuition

* To solve this, we can use the **two-pointer technique**. Use two pointers denoted by `left` and `right`, where left is pointing to the first index and right is pointing to the last index initially.
* While left is less than right, if the sum of the elements corresponding to the left and right index results in `target`, return a list of left and right after adding 1 to each of them because the problem statement states that the given array is a **1-indexed** array.
* If the sum is greater than the target, the right index has to be decreased by one.
* Lastly, if the sum is less than the target, the left index has to be increased by one.

## Time and Space Complexity

Time Complexity: O(N), where N is the length of the string `numbers`

Space Complexity: O(1)

## Solution

```python
class Solution:
    def twoSum(self, numbers: List[int], target: int) -> List[int]:
        # Initialize left and right pointers
        left = 0
        right = len(numbers)-1

        # Traverse the array with left and right pointers
        while left<right:
        
            # Update result or perform necessary operations
            currentSum = numbers[left]+numbers[right]
            if currentSum == target:
            
                # Return result based on the problem statement
                return [left+1, right+1]
                
            # Move pointers inwards
            elif currentSum > target:
                right -= 1
            else:
                left += 1
```
