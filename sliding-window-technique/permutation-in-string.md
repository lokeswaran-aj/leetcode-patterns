# Permutation in String

## Question

[https://leetcode.com/problems/permutation-in-string/description/](https://leetcode.com/problems/permutation-in-string/description/)

> Given two strings `s1` and `s2`, return `true` _if_ `s2` _contains a permutation of_ `s1`_, or_ `false` _otherwise_.
>
> In other words, return `true` if one of `s1`'s permutations is the substring of `s2`.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code><strong>Input: s1 = "ab", s2 = "eidbaooo"
> </strong><strong>Output: true
> </strong><strong>Explanation: s2 contains one permutation of s1 ("ba").
> </strong></code></pre>

## How did I identify the pattern?

* The input is a string
* We are asked to find the **permutations (substrings arranged in any order)**.
* The start of the substring is like the window start and end of the substring is like the window end

## Intuition

To solve this, we use the **fixed sliding window technique.** The length of the window is the length of the `s1`

The solution is to maintain 2 dictionaries or hashmaps, one is for the character frequency in `s1` and the other is for the character frequency in `s2`.

Check if both the dictionaries have same key-value pairs or else move the window forward.

## Time and Space Complexity

Time Complexity: O(N2), where N2 is the length of the `s2`

Space Complexity: O(min(26, N1)), where N1 is the length of the `s2,` because at most the dictionary could contain all the 26 characters along with their counts.

## Solution

```python
class Solution:
    def checkInclusion(self, s1: str, s2: str) -> bool:
    
        if len(s1) > len(s2): return False
        
        s1Char = Counter(s1)
        s2Char = Counter(s2[:len(s1)])
        start = 0
        end = len(s1)-1
        
        if s1Char == s2Char: return True

        while end < len(s2)-1:
        
            # Expand the window
            end += 1
            s2Char[s2[end]] = 1 + s2Char.get(s2[end],0)
            
            # Reduce the size of the window from the left.
            s2Char[s2[start]] = s2Char[s2[start]]-1
            if s2Char[s2[start]] == 0: del s2Char[s2[start]]
            start += 1

            # Perform necessary operations
            if s1Char == s2Char: return True
            
        return False
```
