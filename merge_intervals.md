# Popular Merge Intervals Problems

Many interval-related questions require **merging** or **inserting** intervals, finding **common free/busy slots**, or determining how many **resources** are needed to accommodate overlapping events. A common approach is:

1. **Sort** intervals by their start times.  
2. **Traverse** the sorted list, merging overlapping intervals if necessary (or performing the relevant logic like counting or inserting).

Below is a collection of well-known **Merge Intervals** style problems on LeetCode.

| **#** | **Problem**                                                     | **Key Idea**                                                                                                                                         | **Link**                                                                 |
|:-----:|:---------------------------------------------------------------:|:-----------------------------------------------------------------------------------------------------------------------------------------------------:|:-------------------------------------------------------------------------:|
| **1** | **56. Merge Intervals**                                        | Sort intervals by start time. Merge intervals if they overlap.                                                                                      | [Link](https://leetcode.com/problems/merge-intervals/)                   |
| **2** | **57. Insert Interval**                                        | Insert a new interval into a sorted list of intervals, merge if overlapping.                                                                        | [Link](https://leetcode.com/problems/insert-interval/)                   |
| **3** | **986. Interval List Intersections**                           | Find intersection of two sorted interval lists. Move the pointer of the list with the earlier endpoint.                                            | [Link](https://leetcode.com/problems/interval-list-intersections/)       |
| **4** | **759. Employee Free Time** (Premium)                          | Given multiple employees’ schedules, merge them to find free time slots.                                                                            | [Link](https://leetcode.com/problems/employee-free-time/)                |
| **5** | **253. Meeting Rooms II**                                      | Sort by start time, use a min-heap (priority queue) to track ongoing meetings. Size of heap = min number of rooms needed.                           | [Link](https://leetcode.com/problems/meeting-rooms-ii/)                  |
| **6** | **452. Minimum Number of Arrows to Burst Balloons**            | Sort balloons (intervals) by end coordinate. Greedily shoot an arrow at the end of the first balloon, merge with overlapping balloons.             | [Link](https://leetcode.com/problems/minimum-number-of-arrows-to-burst-balloons/) |
| **7** | **435. Non-overlapping Intervals**                             | Sort intervals by end time. Greedily choose intervals that finish first to maximize the number of non-overlapping intervals (or minimize removals). | [Link](https://leetcode.com/problems/non-overlapping-intervals/)         |

---

## Merge Intervals Template

Below is a general Python template for merging intervals. Variations of this approach can be adapted for more specific interval problems (e.g., adding intervals, finding overlaps, etc.).

```python
def merge_intervals(intervals):
    """
    Merges overlapping intervals in a list of intervals.
    Each interval is represented as [start, end].
    Returns a new list of merged intervals.
    """

    if not intervals:
        return []

    # 1. Sort intervals by start time
    intervals.sort(key=lambda x: x[0])

    merged = [intervals[0]]

    for current in intervals[1:]:
        prev = merged[-1]

        # 2. If current overlaps with the last interval in 'merged'
        if current[0] <= prev[1]:
            # Update the end to the max end of both
            merged[-1][1] = max(prev[1], current[1])
        else:
            # No overlap, just add to the list
            merged.append(current)

    return merged
