# Popular Two Pointers Problems

The **Two Pointers** technique is a fundamental approach used in a variety of array and string problems. It involves placing **two indices** (pointers) at strategic positions (e.g., start and end of a list) and moving them towards each other or in a specific manner to achieve a desired goal (e.g., find a pair summing to a target, partition data, or check palindrome properties).

Below is a list of frequently encountered Two Pointers problems on LeetCode.

---

1. [**11. Container With Most Water**](https://leetcode.com/problems/container-with-most-water/)  
   - **Key Idea**: Put one pointer at the start and one at the end; calculate the area and move the pointer pointing to the lesser height. This ensures a chance of finding a taller line and thus potentially a larger area.

2. [**15. 3Sum**](https://leetcode.com/problems/3sum/)  
   - **Key Idea**: Sort the array. For each element, fix it as one number, and then use the standard two-pointer approach (one pointer at the start, one at the end of the remainder) to find pairs that sum to the required value.

3. [**16. 3Sum Closest**](https://leetcode.com/problems/3sum-closest/)  
   - **Key Idea**: Similar to 3Sum (#15). After sorting, use two pointers to find a pair that, together with the fixed element, minimizes the absolute difference from the target.

4. [**18. 4Sum**](https://leetcode.com/problems/4sum/)  
   - **Key Idea**: Extension of 3Sum. Sort the array, then use multiple nested loops plus two-pointer logic to find quadruplets summing to a target.

5. [**26. Remove Duplicates from Sorted Array**](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)  
   - **Key Idea**: Use one pointer (`i`) to track the position of the “unique elements” and another pointer (`j`) to scan through the array. Update the array in-place by skipping duplicates.

6. [**27. Remove Element**](https://leetcode.com/problems/remove-element/)  
   - **Key Idea**: Similar in nature to #26; use two pointers to overwrite elements that don’t match the target value and keep track of the new length.

7. [**125. Valid Palindrome**](https://leetcode.com/problems/valid-palindrome/)  
   - **Key Idea**: Have a pointer at the start and a pointer at the end. Compare characters (in lower-case alphanumeric form), move inward until they meet, verifying each pair matches.

8. [**167. Two Sum II - Input Array Is Sorted**](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)  
   - **Key Idea**: Since array is sorted, place a pointer at the start (`left`) and one at the end (`right`). If the sum of these pointers is too large, move the `right` pointer down; if too small, move the `left` pointer up.

9. [**283. Move Zeroes**](https://leetcode.com/problems/move-zeroes/)  
   - **Key Idea**: Use a pointer (`slow`) to track the position of non-zero elements, and another pointer (`fast`) to explore the array. Swap or overwrite zeroes as you encounter them.

10. [**344. Reverse String**](https://leetcode.com/problems/reverse-string/)  
    - **Key Idea**: Pointer at the start, pointer at the end, swap characters until the pointers cross.

11. [**345. Reverse Vowels of a String**](https://leetcode.com/problems/reverse-vowels-of-a-string/)  
    - **Key Idea**: Similar to #344 but only swap if both pointers are on vowels.

12. [**680. Valid Palindrome II**](https://leetcode.com/problems/valid-palindrome-ii/)  
    - **Key Idea**: Check palindrome using two pointers. If mismatch occurs, skip a character from either left or right pointer and check if that forms a palindrome.

13. [**977. Squares of a Sorted Array**](https://leetcode.com/problems/squares-of-a-sorted-array/)  
    - **Key Idea**: Array is sorted by absolute values from outside in if you look at the ends. Place a pointer at the start and the end, compare squared values, and fill a new array from the back.

---

## How the Two Pointers Technique Works

1. **Initialization**  
   - Often, pointers are placed at the start (`left = 0`) and at the end (`right = len(array) - 1`) of a sorted array.  
   - In other cases, both pointers may start at the beginning, with `fast` scanning ahead and `slow` trailing behind.

2. **Movement**  
   - Depending on the problem, move either or both pointers inward (or forward) based on certain conditions (e.g., sum comparison, matching elements).

3. **Termination**  
   - Stop when pointers cross (for inward-moving patterns) or when the `fast` pointer reaches the end of the array (for problems like removing elements, moving zeroes, etc.).

4. **Updating the Result**  
   - Check the current pair’s sum, product, or other condition each time you move pointers.  
   - For array manipulation problems, overwrite elements or swap them to maintain the desired order/condition.

---

## Tips & Resources

1. **Sorting is Key**  
   - Many two-pointer problems require sorting the array first (e.g., 3Sum, 4Sum, Two Sum II).  

2. **Handling Edge Cases**  
   - Arrays with all identical elements, empty arrays, or single-element arrays.  
   - Strings with special characters for palindrome checks (use two-pointer while ignoring non-alphanumeric characters).

3. **Complexities**  
   - Two pointers typically gives you \( O(n) \) or \( O(n \log n) \) time complexity (depending on sorting).  
   - Space complexity is often \( O(1) \) if you’re just swapping/moving pointers in place.

4. **Variants**  
   - **Fast & Slow** pointers (like in linked list cycle detection or remove nth node from the end).  
   - **Inward** pointers from both ends (like in container-with-most-water or palindrome checks).  

---
# Popular Two Pointers Problems

The **Two Pointers** technique is a fundamental approach used in many array and string problems. You place **two indices** (pointers) in different positions (often at the start and end of an array), then **move** them closer (or adjust them) based on certain conditions until they meet or cross. 

Below is a list of frequently encountered Two Pointers problems on LeetCode, along with a **template** code snippet illustrating the technique.

---

## Two Pointers Template Code

```python
def two_pointer_template(arr, target):
    """
    A generic two-pointer template. 
    Depending on the problem, 'target' could be anything
    (a sum, a condition, etc.), or you may not need 'target' at all.
    """

    left = 0
    right = len(arr) - 1

    # This variable can store results. For instance, 
    # it could track a max area, count of certain elements, etc.
    result = 0

    while left < right:
        # Perform some logic based on arr[left], arr[right], and possibly 'target'

        current_sum = arr[left] + arr[right]  # Example usage
        if current_sum == target:
            # Update result if needed
            result = max(result, current_sum)  # or do something else
            # Then decide how to move pointers
            left += 1
            right -= 1
        elif current_sum < target:
            # Move left pointer to increase sum
            left += 1
        else:
            # current_sum > target
            # Move right pointer to decrease sum
            right -= 1

    return result

