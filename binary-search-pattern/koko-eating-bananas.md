---
description: medium
---

# Koko Eating Bananas

## Question

[https://leetcode.com/problems/koko-eating-bananas/description/](https://leetcode.com/problems/koko-eating-bananas/description/)

> Koko loves to eat bananas. There are `n` piles of bananas, the `ith` pile has `piles[i]` bananas. The guards have gone and will come back in `h` hours.
>
> Koko can decide her bananas-per-hour eating speed of `k`. Each hour, she chooses some pile of bananas and eats `k` bananas from that pile. If the pile has less than `k` bananas, she eats all of them instead and will not eat any more bananas during this hour.
>
> Koko likes to eat slowly but still wants to finish eating all the bananas before the guards return.
>
> Return _the minimum integer_ `k` _such that she can eat all the bananas within_ `h` _hours_.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code><strong>Input: piles = [3,6,7,11], h = 8
> </strong><strong>Output: 4
> </strong></code></pre>

## How did I identify the pattern?

* We are asked to find a **minimum number** of bananas from **1 to the maximum number of bananas** available in a pile to complete all the piles in h hours.

## Intuition

* To solve this, we can use the **modified binary search pattern**.
* Initially, we assign the `start` and `end` to 1 and the maximum number in the array
* Loop until the start is less than or equal to the end.
* Find the mid and divide each element in the array to find the hours spent with that speed(mid value)
* Finally, check if its hours spent is more than h, move start to mid + 1, else update the result and move end to mid - 1

## Time and Space Complexity

Time Complexity: O(log(max(piles)\*N), where N is the length of the `piles`

Space Complexity: O(1)

## Solution

```python
class Solution:
    def minEatingSpeed(self, piles: List[int], h: int) -> int:
        # Initialize the start and end pointers
        start = 1
        end = ceil(max(piles) / (h // len(piles)))
        k = end
        
        while start <= end:
        
            # Calculate mid
            mid = start + (end-start)//2
            hoursSpent = 0
            
            for pile in piles:
                hoursSpent += ceil(pile/mid)
            # Update start conditionally
            if hoursSpent > h:
                start = mid + 1
            # Update end conditionally
            else:
                # Update the result
                k = min(k, mid)
                end = mid - 1
        return k
```
