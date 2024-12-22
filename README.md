

# Sliding Window Pattern

The **Sliding Window** pattern is a popular technique for solving problems on arrays and strings where we need to find a **contiguous subarray/substring** that meets certain criteria (e.g., maximum/minimum sum, target conditions, number of distinct elements). 

By **sliding** a window across our data and **updating** relevant counts/aggregates as we go, we often achieve an efficient \( O(n) \) or \( O(n \cdot k) \) time complexity, instead of recalculating everything from scratch at each step.

---

## How It Works

1. **Initialize** two pointers (often called `left` and `right`) at the start of the array or string.
2. **Expand** the `right` pointer, adding the current element to the window’s running total, frequency map, etc.
3. If a **condition is exceeded** (e.g., sum too large, too many distinct characters, etc.), **shrink** the window from the left by updating the running total/frequency map and moving `left` forward.
4. **Track** your desired result (e.g., the maximum window size, minimum window size, or any other measure).

---

## Sliding Window Template

Below is a generic Python template that demonstrates the core idea. You can adapt it for your specific problem logic:

```python
def sliding_window_template(arr, k):  # 'k' might be a target, or used in a condition
    left = 0
    window_sum = 0  # could be a frequency map, product, etc.
    result = float('-inf')  # or float('inf') if minimizing

    for right in range(len(arr)):
        # 1. Expand window by including arr[right]
        window_sum += arr[right]

        # 2. Adjust window if condition is violated
        while condition_not_met(window_sum, k):
            window_sum -= arr[left]
            left += 1

        # 3. Update result if needed
        result = max(result, window_sum)
        # Or for length-based problems:
        # result = max(result, right - left + 1)

    return result
1. [**3. Longest Substring Without Repeating Characters**](https://leetcode.com/problems/longest-substring-without-repeating-characters/)  
   - **Key Idea**: Track last occurrence of each character to ensure no duplicates in the current window.

2. [**76. Minimum Window Substring**](https://leetcode.com/problems/minimum-window-substring/)  
   - **Key Idea**: Find a substring in `s` containing all characters of `t`. Use frequency maps and shrink when valid.

3. [**209. Minimum Size Subarray Sum**](https://leetcode.com/problems/minimum-size-subarray-sum/)  
   - **Key Idea**: Running sum approach. Expand window until sum >= target, then shrink to find minimum length.

4. [**340. Longest Substring with At Most K Distinct Characters**](https://leetcode.com/problems/longest-substring-with-at-most-k-distinct-characters/) *(Premium)*  
   - **Key Idea**: Use a hash map to count distinct characters. Shrink when more than `k` distinct characters.

5. [**424. Longest Repeating Character Replacement**](https://leetcode.com/problems/longest-repeating-character-replacement/)  
   - **Key Idea**: We can replace up to `k` characters to get the longest substring with all same characters.

6. [**438. Find All Anagrams in a String**](https://leetcode.com/problems/find-all-anagrams-in-a-string/)  
   - **Key Idea**: Fixed window size = length of `p`. Compare frequency of current window with `p`'s frequency.

7. [**567. Permutation in String**](https://leetcode.com/problems/permutation-in-string/)  
   - **Key Idea**: Similar to #438; check if any substring of length `len(p)` is a permutation of `p`.

8. [**713. Subarray Product Less Than K**](https://leetcode.com/problems/subarray-product-less-than-k/)  
   - **Key Idea**: Maintain the product of the window. Shrink from left if product >= `k`.

9. [**904. Fruit Into Baskets**](https://leetcode.com/problems/fruit-into-baskets/)  
   - **Key Idea**: At most two distinct fruits (like #340 but with `k = 2`).

10. [**1004. Max Consecutive Ones III**](https://leetcode.com/problems/max-consecutive-ones-iii/)  
    - **Key Idea**: You can flip at most `k` zeroes. Track number of zeroes in the window and shrink if exceeded.

11. [**1052. Grumpy Bookstore Owner**](https://leetcode.com/problems/grumpy-bookstore-owner/)  
    - **Key Idea**: Use sliding window of size `X` to find the best segment to reduce grumpiness and maximize satisfied customers.

12. [**1423. Maximum Points You Can Obtain from Cards**](https://leetcode.com/problems/maximum-points-you-can-obtain-from-cards/)  
    - **Key Idea**: Instead of thinking in terms of selecting `k` from ends, think of ignoring a window of size `len(cards)-k` in the middle and minimize its sum.

13. [**1456. Maximum Number of Vowels in a Substring of Given Length**](https://leetcode.com/problems/maximum-number-of-vowels-in-a-substring-of-given-length/)  
    - **Key Idea**: Fixed-size window; count vowels and slide across the string.

---
