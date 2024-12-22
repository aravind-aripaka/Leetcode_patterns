# Binary Search Problems

**Binary Search** is a classic algorithmic technique to **efficiently find a target element** in a sorted structure (array, search space, etc.) by repeatedly dividing the search interval in half. At each step, we compare the target value with the value in the middle of the current interval:

- If the target is **equal** to the mid value, we’re done.  
- If the target is **less** than the mid value, move to the left half.  
- If the target is **greater** than the mid value, move to the right half.

This yields a time complexity of \( O(\log n) \) for searching in a sorted array of size \( n \).

| **#** | **Problem**                                                | **Key Idea**                                                                                                                                                                                                       | **Link**                                                        |
|:-----:|:-----------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:----------------------------------------------------------------|
| **1** | **704. Binary Search**                                     | Classic binary search on a sorted array to find a target.                                                                                                                                                           | [Link](https://leetcode.com/problems/binary-search/)            |
| **2** | **278. First Bad Version**                                 | Binary search over versions 1 to n; use the `isBadVersion` API to narrow down the first bad one.                                                                                                                     | [Link](https://leetcode.com/problems/first-bad-version/)        |
| **3** | **35. Search Insert Position**                             | Find the position to insert a target if not present, maintaining sorted order.                                                                                                                                       | [Link](https://leetcode.com/problems/search-insert-position/)   |
| **4** | **34. Find First and Last Position of Element in Sorted Array** | Perform two binary searches: one to find the first occurrence, another to find the last.                                                                                                                            | [Link](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/) |
| **5** | **33. Search in Rotated Sorted Array**                     | Even though the array is rotated, one side remains sorted. Use that property to decide which half to explore.                                                                                                        | [Link](https://leetcode.com/problems/search-in-rotated-sorted-array/) |
| **6** | **81. Search in Rotated Sorted Array II**                  | Variant of #33 that handles duplicates. If `nums[mid] == nums[left]`, increment `left` to skip duplicates.                                                                                                           | [Link](https://leetcode.com/problems/search-in-rotated-sorted-array-ii/) |
| **7** | **69. Sqrt(x)**                                            | Binary search on the range [0, x] to find the integer floor of \(\sqrt{x}\).                                                                                                                                         | [Link](https://leetcode.com/problems/sqrtx/)                    |
| **8** | **744. Find Smallest Letter Greater Than Target**          | If `mid` letter <= target, move `left` up; otherwise move `right` down.                                                                                                                                             | [Link](https://leetcode.com/problems/find-smallest-letter-greater-than-target/) |
| **9** | **162. Find Peak Element**                                 | Check the slope around mid; if `nums[mid] < nums[mid + 1]`, go right. Otherwise, go left.                                                                                                                            | [Link](https://leetcode.com/problems/find-peak-element/)        |
| **10**| **852. Peak Index in a Mountain Array**                    | Guaranteed “mountain” array (strictly increasing then decreasing). Similar approach to #162.                                                                                                                         | [Link](https://leetcode.com/problems/peak-index-in-a-mountain-array/) |
| **11**| **875. Koko Eating Bananas**                               | Binary search over possible eating speeds. Check total hours needed against `H`.                                                                                                                                     | [Link](https://leetcode.com/problems/koko-eating-bananas/)      |
| **12**| **1011. Capacity To Ship Packages Within D Days**          | Binary search the possible “capacity” range. For each `mid`, check feasibility by simulating the loading process.                                                                                                    | [Link](https://leetcode.com/problems/capacity-to-ship-packages-within-d-days/) |
| **13**| **410. Split Array Largest Sum**                           | Binary search the answer space (max subarray sum). Check feasibility by splitting array greedily.                                                                                                                    | [Link](https://leetcode.com/problems/split-array-largest-sum/)  |
| **14**| **668. Kth Smallest Number in Multiplication Table**       | Binary search on the value range; for each `mid`, count how many values in the multiplication table are <= `mid`.                                                                                                    | [Link](https://leetcode.com/problems/kth-smallest-number-in-multiplication-table/) |



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

