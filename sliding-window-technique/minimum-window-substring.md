---
description: hard
---

# Minimum Window Substring

## Question

[https://leetcode.com/problems/minimum-window-substring/description/](https://leetcode.com/problems/minimum-window-substring/description/)

> Given two strings `s` and `t` of lengths `m` and `n` respectively, return _the **minimum window**_&#x20;
>
> _**substring** of_ `s` _such that every character in_ `t` _(**including duplicates**) is included in the window_. If there is no such substring, return _the empty string_ `""`.
>
> The testcases will be generated such that the answer is **unique**.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code><strong>Input: s = "ADOBECODEBANC", t = "ABC"
> </strong><strong>Output: "BANC"
> </strong><strong>Explanation: The minimum window substring "BANC" includes 'A', 'B', and 'C' from string t.
> </strong></code></pre>

## How did I identify the pattern?

* The input is a string
* We are asked to find the **minimum window substring**
* The start of the substring is like the window start and end of the substring is like the window end

## Intuition

To solve this, we use the **variable sliding window technique.** We need to return the smallest substring of `s` that has all the character in `t`. We are going to use 2 dictionaries or hashmaps to track the characters counts in t and the window. We are also going to use two variable `needed and matched` to check if the window has all the characters in t.

When we find a character in s that is also present in t, we can increase the matched. While the **matched and needed are equal**, we start reducing the window size until matched and needed or equal. Everytime, process the length of the window and store it in `minimum substring`. At last, return the minimum substring

## Time and Space Complexity

Time Complexity: O(S), where S is the length of the `s`

Space Complexity: O(min(26, T)), where T is the length of the `t`, because at most the dictionary could contain all the 26 characters along with their counts.

## Solution

```python
class Solution:
    def minWindow(self, s: str, t: str) -> str:
    
        minSubstring = "" # Initialize result based on the problem
        if len(s) < len(t): return minSubstring

        tChar = {}
        sChar = {}

        for c in t:
            tChar[c] = tChar.get(c,0) + 1
            sChar[c] = 0
        
        needed = len(t)
        matched = 0

        start = -1
        end = 0

        while end < len(s):

            # Expand the window
            curChar = s[end]
            if curChar in tChar:
                sChar[curChar] = sChar.get(curChar,0) + 1
                if sChar[curChar] <= tChar[curChar]:
                    matched += 1

            # Check if the current window satisfies the condition
            while matched == needed:
                start += 1
                
                # Update result or perform necessary operations
                if (len(minSubstring) >= end-start+1 or minSubstring == ""):
                    minSubstring = s[start:end+1]
                    
                # Shrink the window from the left
                curChar = s[start]
                if curChar in sChar:
                    sChar[curChar] -= 1
                    if sChar[curChar] < tChar[curChar]:
                        matched -= 1

            # Move the window forward
            end += 1

        return minSubstring
```
