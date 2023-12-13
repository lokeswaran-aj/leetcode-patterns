---
description: 'Mastering LeetCode: The Two-Pointer Technique'
---

# Two-Pointer Technique

The two-pointer technique is a highly effective and versatile approach in the realm of algorithmic problem-solving, particularly when dealing with array and list-based problems.

The two-pointer technique involves the manipulation of two pointers within an array or list. These pointers may traverse the data structure simultaneously or move in a specific relationship to one another. This technique's strength lies in its adaptability, accommodating scenarios where pairs, subarrays, or linked list nodes require synchronized processing for optimal solutions.

## How to identify Two-Pointer Techniques

Look out for problem statements that involve **searching for a pair or a subarray** with a specific constraint, determining if a solution exists, or finding the shortest or longest possible subarray.

## Real-world Applications

* Finding duplicates
* Sorting
* Collision detection

## Leetcode Examples

* [125. Valid Palindrome](https://leetcode.com/problems/valid-palindrome/)
* [15. 3Sum](https://leetcode.com/problems/3sum/)
* [42. Trapping Rain Water](https://leetcode.com/problems/trapping-rain-water/)

## Types of Two-Pointer Techniques

1. Fast and Slow Pointers
2. Left and Right Pointers

## Python Template for the Two-Pointer Algorithm

### Fast and Slow Pointers

```python
def fast_slow_pointers_algorithm(nums):
    # Initialize fast and slow pointers
    fast, slow = 0, 0
    result = initialize_result()  # Initialize result based on the problem

    # Traverse the list with fast and slow pointers
    while fast < len(nums) and fast + 1 < len(nums):
        # Update result or perform necessary operations
        result = update_result(result, current_element)

        # Move fast pointer (may move by more than 1 element)
        fast += 2

        # Move slow pointer
        slow += 1

    # Return result based on the problem statement
    return result
```

### Left and Right Pointers

```python
def left_right_pointers_algorithm(nums):
    # Initialize left and right pointers
    left, right = 0, len(nums) - 1
    result = initialize_result()  # Initialize result based on the problem
    
    # Traverse the array with left and right pointers
    while left < right:
        # Update result or perform necessary operations
        result = update_result(result, current_element)

        # Move pointers inwards
        left += 1
        right -= 1

    # Return result based on the problem statement
    return result
```

## Time and Space Complexity Analysis

**Time Complexity**

* Time complexity: O(N), where N is the size of the input array or list.

**Space Complexity**

* Space complexity: O(1), as the algorithm typically uses a constant amount of extra space, regardless of the input size.

\
