# Best Time to Buy and Sell Stock

## Question

[https://leetcode.com/problems/best-time-to-buy-and-sell-stock/description/](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/description/)

>
>
> You are given an array `prices` where `prices[i]` is the price of a given stock on the `ith` day.
>
> You want to maximize your profit by choosing a **single day** to buy one stock and choosing a **different day in the future** to sell that stock.
>
> Return _the maximum profit you can achieve from this transaction_. If you cannot achieve any profit, return `0`.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code><strong>Input: prices = [7,1,5,3,6,4]
> </strong><strong>Output: 5
> </strong></code></pre>

## How did I identify the pattern?

* The input is a list
* We are asked to find the profit in a **subsequent days**.
* The buy date is like the window start and sell date is like the window end

## Intuition

To solve this, we use the **variable sliding window technique**, keeping track of our `minimum purchase price` and `maximum profit` so far. We iterate over the list of prices, updating our minimum purchase price if we find a lower price, and calculating our profit by subtracting the current minimum purchase price from the current price. If this profit is greater than our maximum profit so far, we will update our maximum profit. The final maximum profit is our answer.

## Time and Space Complexity

Time Complexity: O(N), where N is the number of elements in the `prices` list

Space Complexity: O(1)

## Solution

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        start = 0
        end = 1
        maxProfit = 0

        while end < len(prices):
            currentPrice = prices[end]

            profit = currentPrice - prices[start]
            maxProfit = profit if profit > maxProfit else maxProfit

            if prices[start] > currentPrice:
                start = end

            end += 1

        return maxProfit
```
