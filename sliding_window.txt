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
