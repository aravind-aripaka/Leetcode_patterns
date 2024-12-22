# Popular Binary Search Problems

**Binary Search** is a classic algorithmic technique to **efficiently find a target element** in a sorted structure (array, search space, etc.) by repeatedly dividing the search interval in half. At each step, we compare the target value with the value in the middle of the current interval:

- If the target is **equal** to the mid value, we’re done.  
- If the target is **less** than the mid value, move to the left half.  
- If the target is **greater** than the mid value, move to the right half.

This yields a time complexity of \( O(\log n) \) for searching in a sorted array of size \( n \).

---

## Binary Search Template Code

Below is a **generic** binary search template in Python. It can be adapted for problems where you just need to check for existence of a target, or find an insertion index, or run a binary search on an **answer space** (e.g., searching for a valid capacity or minimum feasible value).

```python
def binary_search_template(nums, target):
    """
    Generic binary search template.
    `nums` is assumed to be sorted in ascending order.
    Returns the index of `target` if found, or -1 if not present.
    """

    left, right = 0, len(nums) - 1
    
    while left <= right:
        mid = (left + right) // 2  # or left + (right - left) // 2 to avoid overflow in other languages
        if nums[mid] == target:
            return mid
        elif nums[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    
    return -1  # Target not found
