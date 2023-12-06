# Longest Repeating Character Replacement

## Question

[https://leetcode.com/problems/longest-repeating-character-replacement/description/](https://leetcode.com/problems/longest-repeating-character-replacement/description/)

> You are given a string `s` and an integer `k`. You can choose any character of the string and change it to any other uppercase English character. You can perform this operation at most `k` times.
>
> Return _the length of the longest substring containing the same letter you can get after performing the above operations_.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code><strong>Input: s = "ABAB", k = 2
> </strong><strong>Output: 4
> </strong><strong>Explanation: Replace the two 'A's with two 'B's or vice versa.
> </strong></code></pre>

## How did I identify the pattern?

* The input is a string
* We are asked to find the **longest substring**.
* The start of the substring is like the window start and end of the substring is like the window end

## Intuition

This problem is similar to the [Longest Substring Without Repeating Characters](longest-substring-without-repeating-characters.md) problem. To solve this, we use the **variable sliding window technique.**&#x20;

Track the `maximum length` of repeated characters, the count of every character in a dictionary or hashmap, and the `most frequent character`'s count.

Whenever increasing the window size, increase that character count in the dictionary, then update the `most frequent character` if the count of that character is greater.&#x20;

The condition to reduce the window is when `length of the window - the most frequent character` is greater than `k`, we need to shrinking the window. Compute the maximum length and return it at the end.

> **Note:** We don't have to reduce the most frequent character count while shrinking because when the `length-most frequent character` becomes negative, it will not affect the condition to shrink the window. We only focus on maximizing the most frequent character

## Time and Space Complexity

Time Complexity: O(N), where N is the length of the string

Space Complexity: O(26), because at most the dictionary could contain all the 26 characters along with their counts.

## Solution

````python
```python3
class Solution:
    def characterReplacement(self, s: str, k: int) -> int:
        start = -1
        end = 0
        maxLength = 0
        charCount = {}
        mostFreqChar = 0

        while end<len(s):
        
            # Expand the window
            curChar = s[end]
            charCount[curChar] = charCount.get(curChar, 0) + 1
            if mostFreqChar < charCount[curChar]:
                mostFreqChar = charCount[curChar]

            # Check if the current window satisfies the condition
            while end-start-mostFreqChar > k:
                # Reduce the size of the window from the left.
                start += 1
                charCount[s[start]] = charCount[s[start]]-1

            # Update result or perform necessary operations
            maxLength = max(maxLength, end-start)

            # Move the window forward
            end += 1

        return maxLength
```
````
