# Popular Monotonic Stack Problems

A **monotonic stack** is a data structure (often a simple stack) that helps maintain elements in a sorted manner (non-decreasing or non-increasing) as you iterate through data. When a new element does not maintain the monotonic property, you **pop** from the stack until it does. This technique is widely used to efficiently solve problems related to **next greater element**, **stock span**, **largest rectangle**, and more.

Below is a list of frequently encountered **Monotonic Stack** problems on LeetCode:

| **#** | **Problem**                        | **Key Idea**                                                                                                                                                                     | **Link**                                                                 |
|:-----:|:----------------------------------:|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:-------------------------------------------------------------------------:|
| **1** | **496. Next Greater Element I**    | Use a decreasing stack: traverse `nums2`, pop smaller elements from the top. For each element in `nums1`, check its next greater in a hashmap.                                    | [Link](https://leetcode.com/problems/next-greater-element-i/)            |
| **2** | **503. Next Greater Element II**   | Circular array version of Next Greater Element. Use stack + modulo arithmetic or a double traversal to handle wraparounds.                                                        | [Link](https://leetcode.com/problems/next-greater-element-ii/)           |
| **3** | **556. Next Greater Element III**  | Similar idea but for digits of a number. Find the next lexicographically greater permutation, or return -1 if none exists.                                                        | [Link](https://leetcode.com/problems/next-greater-element-iii/)          |
| **4** | **739. Daily Temperatures**        | Maintain a decreasing stack of indices. For each day, pop until you find a warmer temperature on the stack top or stack becomes empty.                                            | [Link](https://leetcode.com/problems/daily-temperatures/)                |
| **5** | **901. Online Stock Span**         | For each new price, pop smaller prices from the stack and aggregate spans. The height of the stack helps compute the span quickly.                                                | [Link](https://leetcode.com/problems/online-stock-span/)                 |
| **6** | **84. Largest Rectangle in Histogram** | Use a stack to store indices of bars in non-decreasing height. When a bar is smaller than the stack’s top, pop and calculate the rectangle area.                                  | [Link](https://leetcode.com/problems/largest-rectangle-in-histogram/)    |
| **7** | **85. Maximal Rectangle**          | Build on #84 for each row in a binary matrix. Treat each row as a histogram where consecutive 1s increase the “height.”                                                           | [Link](https://leetcode.com/problems/maximal-rectangle/)                 |
| **8** | **316. Remove Duplicate Letters**  | Keep a **monotonically increasing** stack of characters. If a new character is smaller than the stack’s top and the top character will appear again later, pop it.               | [Link](https://leetcode.com/problems/remove-duplicate-letters/)          |
| **9** | **402. Remove K Digits**           | Similar to #316 but remove exactly `k` digits to form the smallest number. Use a **monotonically increasing** stack to greedily pop larger digits when possible.                  | [Link](https://leetcode.com/problems/remove-k-digits/)                   |

---

## Monotonic Stack Template

Below is a generic Python template for a **monotonically increasing** stack. You can adapt it to your particular problem (e.g., to handle next greater elements, remove duplicates, or compute spans).

```python
def monotonic_stack_increasing(nums):
    """
    Returns a list representing the next greater element for each element.
    For a strictly increasing stack, the top always holds the smallest element encountered so far.
    """

    # This will hold the result for each element (e.g., next greater element)
    # Initialize all with -1 or some default
    result = [-1] * len(nums)
    
    stack = []  # will store indices or values (depending on problem)

    # Traverse through the list
    for i, val in enumerate(nums):
        # While stack is not empty and current element is greater
        # than the element at the top of the stack:
        while stack and nums[stack[-1]] < val:
            top_index = stack.pop()
            result[top_index] = val
        
        # Push current index onto stack
        stack.append(i)
    
    # Any remaining indices in the stack will have -1 or default as next greater
    # (because they don't have a next greater element)
    return result
