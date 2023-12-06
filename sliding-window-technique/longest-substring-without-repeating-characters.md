# Longest Substring Without Repeating Characters

## Question

[https://leetcode.com/problems/longest-substring-without-repeating-characters/description/](https://leetcode.com/problems/longest-substring-without-repeating-characters/description/)

> Given a string `s`, find the length of the **longest**&#x20;
>
> **substring** without repeating characters.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code><strong>Input: s = "abcabcbb"
> </strong><strong>Output: 3
> </strong><strong>Explanation: The answer is "abc", with the length of 3.
> </strong></code></pre>

## How did I identify the pattern?

* The input is a string
* We are asked to find the **longest substring**.
* The start of the substring is like the window start and end of the substring is like the window end

## Intuition

To solve this, we use the **variable sliding window technique**, keeping track of the `longest substring` without repeating characters. We maintain a `set` to check if the new character is already in the substring. We iterate over the `string`, if the new character is already in the set, then we reduce the window size by removing the character at the `start index`. Then we add the current character to the set.  If current substring length is greater than our longest substring so far, we will update our longest substring. The final longest substring is our answer.

## Time and Space Complexity

Time Complexity: O(N), where N is the length of the string

Space Complexity: O(N), because we use a set to maintain the characters in the substring.

## Solution

````python
```python3
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        start = -1
        end = 0
        longestSubstring = 0
        charactersInLongestSubstring = set()
        
        while end < len(s):
            
            # reduce the window size
            while s[end] in charactersInLongestSubstring:
                start += 1
                charactersInLongestSubstring.remove(s[start])

            charactersInLongestSubstring.add(s[end])

            currentSubstring = end-start
            longestSubstring = max(longestSubstring,currentSubstring)

            # increase the window size
            end += 1
            
        return longestSubstring
```
````
