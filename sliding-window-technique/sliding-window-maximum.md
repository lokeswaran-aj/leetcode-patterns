---
description: hard
---

# Sliding Window Maximum

## Question

[https://leetcode.com/problems/sliding-window-maximum/description/](https://leetcode.com/problems/sliding-window-maximum/description/)

> You are given an array of integers `nums`, there is a sliding window of size `k` which is moving from the very left of the array to the very right. You can only see the `k` numbers in the window. Each time the sliding window moves right by one position.
>
> Return _the max sliding window_.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code><strong>Input: nums = [1,3,-1,-3,5,3,6,7], k = 3
> </strong><strong>Output: [3,3,5,5,6,7]
> </strong><strong>Explanation: 
> </strong>Window position                Max
> ---------------               -----
> <strong>[1  3  -1] -3  5  3  6  7       3
> </strong><strong> 1 [3  -1  -3] 5  3  6  7       3
> </strong><strong> 1  3 [-1  -3  5] 3  6  7       5
> </strong><strong> 1  3  -1 [-3  5  3] 6  7       5
> </strong><strong> 1  3  -1  -3 [5  3  6] 7       6
> </strong><strong> 1  3  -1  -3  5 [3  6  7]      7
> </strong></code></pre>

## How did I identify the pattern?

* The input is an array
* We are asked to find the **maximum sliding window**

## Intuition

To solve this, we use the **fixed sliding window technique.** We need a queue to store the elements in the window in the descending order. This queue is also know as **Monotonic decreasing queue.**&#x20;

Before adding `end` element to the queue, we first pop all the elements smaller than that. So that we can take the `0th` element to the `maximum sliding window`. Then we can pop the `0th` element from the queue while shrinking the window if the its value is same as the `start` element's value.

## Time and Space Complexity

Time Complexity: O(N), where N is the length of the `nums`

Space Complexity: O(N)

## Solution

```python
class Solution:
    def maxSlidingWindow(self, nums: List[int], k: int) -> List[int]:
        maxWindow = [] # Initialize result based on the problem
        queue = deque([])

        for end in range(len(nums)):

            # Expand the window
            while queue and queue[-1] < nums[end]:
                queue.pop()
            queue.append(nums[end])

            start = end-k+1
            # Update result or perform necessary operations
            if start >= 0:
                maxWindow.append(queue[0])

                # Check if the current window satisfies the condition
                if nums[start] == queue[0]:
                    # Shrink the window from the left
                    queue.popleft()
                    
        return maxWindow
```
