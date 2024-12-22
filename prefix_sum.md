# Popular Prefix Sum Problems

A **prefix sum** array (also known as a cumulative sum array) is a simple yet powerful concept often used in array- or subarray-based problems to quickly calculate sums of subranges in \(O(1)\) time after an \(O(n)\) preprocessing step.

## How Prefix Sum Works

1. **Compute** a prefix sum array `prefix`, where `prefix[i]` is the sum of the first `i` elements in the original array. (Sometimes `prefix[0] = 0` is used as a sentinel.)
2. **Query** the sum of any subarray `(l, r)` using:
   \[
   \text{subarray\_sum}(l, r) = \text{prefix}[r] - \text{prefix}[l - 1]
   \]
   (Adjusting indices appropriately depending on the language and whether you used `prefix[0] = 0`.)

This allows quick range-sum lookups without re-summing the entire subarray each time.

---

## Common Prefix Sum Problems on LeetCode

| **#** | **Problem**                                   | **Key Idea**                                                                                                                                                                                        | **Link**                                                               |
|:-----:|:---------------------------------------------:|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:-----------------------------------------------------------------------:|
| **1** | **303. Range Sum Query - Immutable**          | Build a prefix sum array once. Then each range sum query can be answered in \(O(1)\).                                                                                                               | [Link](https://leetcode.com/problems/range-sum-query-immutable/)       |
| **2** | **304. Range Sum Query 2D - Immutable**       | 2D prefix sum: `prefix[i][j]` = sum of elements in submatrix from `(0,0)` to `(i,j)`. Then query any submatrix in \(O(1)\).                                                                          | [Link](https://leetcode.com/problems/range-sum-query-2d-immutable/)    |
| **3** | **560. Subarray Sum Equals K**                | Keep a running sum. Use a hashmap to check how many times `(running_sum - k)` has appeared.                                                                                                          | [Link](https://leetcode.com/problems/subarray-sum-equals-k/)           |
| **4** | **1248. Count Number of Nice Subarrays**      | Similar to #560 but track the count of odd numbers in the subarray. Use prefix sums to detect subarrays with exactly `k` odd numbers.                                                                | [Link](https://leetcode.com/problems/count-number-of-nice-subarrays/)  |
| **5** | **974. Subarray Sums Divisible by K**         | Maintain a running sum mod K. If the same mod appears multiple times in the prefix sums, subarrays between those indices have a total sum divisible by `K`.                                         | [Link](https://leetcode.com/problems/subarray-sums-divisible-by-k/)    |
| **6** | **525. Contiguous Array**                     | Convert 0 to -1, then the problem of finding a balanced subarray of 0s and 1s becomes finding a subarray with sum 0. Use prefix sums with a hashmap of `(sum -> first index)`.                       | [Link](https://leetcode.com/problems/contiguous-array/)                |
| **7** | **1124. Longest Well-Performing Interval**    | Convert “good” (tiring) days to 1 and other days to -1. Prefix sums help find the longest interval with sum > 0.                                                                                     | [Link](https://leetcode.com/problems/longest-well-performing-interval/)|
| **8** | **2090. K Radius Subarray Averages**          | Use prefix sums to quickly compute subarray sums of size `2k+1` for each index, then average them.                                                                                                   | [Link](https://leetcode.com/problems/k-radius-subarray-averages/)      |

---

## Prefix Sum Template

A simple 1D prefix sum in Python:

```python
def build_prefix_sum(nums):
    """
    Returns a list 'prefix' where prefix[i] is the sum
    of nums[0] to nums[i-1]. (prefix[0] = 0 for convenience)
    """
    prefix = [0] * (len(nums) + 1)
    for i in range(1, len(nums) + 1):
        prefix[i] = prefix[i-1] + nums[i-1]
    return prefix

def subarray_sum(prefix, left, right):
    """
    Given the prefix sum array and a 1-based index system:
    subarray_sum(left, right) = prefix[right] - prefix[left - 1]
    """
    return prefix[right] - prefix[left - 1]
