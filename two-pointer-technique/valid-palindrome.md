# Valid Palindrome

## Question

[https://leetcode.com/problems/valid-palindrome/description/](https://leetcode.com/problems/valid-palindrome/description/)

> A phrase is a **palindrome** if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, it reads the same forward and backward. Alphanumeric characters include letters and numbers.
>
> Given a string `s`, return `true` _if it is a **palindrome**, or_ `false` _otherwise_.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code><strong>Input: s = "A man, a plan, a canal: Panama"
> </strong><strong>Output: true
> </strong><strong>Explanation: "amanaplanacanalpanama" is a palindrome.
> </strong></code></pre>

## How did I identify the pattern?

* The input is a string
* We are asked to find the **palindrome** where we would look out for same character from both the ends

## Intuition

To solve this, we can use the **Left and Right Pointers technique**. We can keep going until the `left` and `right` pointers cross. Firstly, check if the characters at left and right are alphabets or numbers by using the `string.isalnum()` method while the left and right don't cross. If they are not alphanumeric characters, we can move the pointer inward. Finally, check if the characters are the same or not.

## Time and Space Complexity

Time Complexity: O(N), where N is the length of the string `s`

Space Complexity: O(1)

## Solution

```python
class Solution:
    def isPalindrome(self, s: str) -> bool:
        sLength = len(s)
        # Initialize left and right pointers
        left = 0
        right = sLength - 1

        # Traverse the array with left and right pointers
        while  left < right:

            # Update result or perform necessary operations
            while left < right and not s[left].isalnum():
                left += 1

            while left < right  and not s[right].isalnum():
                right -= 1                

            if s[left].lower() != s[right].lower():
                return False
           # Move pointers inwards
            else:
                left += 1
                right -= 1

        # Return result based on the problem statement
        return True
```
