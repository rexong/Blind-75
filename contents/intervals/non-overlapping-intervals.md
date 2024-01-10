<frontmatter>
  title: Intervals - Non-overlapping Intervals
</frontmatter>

# [Non-overlapping Intervals](https://leetcode.com/problems/non-overlapping-intervals/)

#### Difficulty: Medium

### Intuition

If there is an overlap, increment count. <br>
Choose which interval to remove depends on the end time of the intervals, remove the interval that has a shorter end time.

### Contraints

- $0\leqslant$ Length of intervals $\leqslant 10000$

## Approach

1. Sort intervals by start time
2. Initialise count to 0
3. Set prev to the first interval
4. For every interval starting from the second
   1. Set curr to interval
   2. If there is an overlap
      1. Increment count by 1
      2. If prev's end > curr's end, update prev to curr
   3. Else, set prev to curr
5. Return count

### Complexity

#### Time Complexity: O(n logn)

For sorting the intervals, counting the number of intervals to remove takes linear time.

#### Space Complexity: O(1)

Sorting is in place

### Solution

<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def eraseOverlapIntervals(self, intervals: List[List[int]]) -> int:
        intervals.sort(key=lambda interval : interval[0])
        prev = intervals[0]
        count = 0
        for i in range(1, len(intervals)):
            curr = intervals[i]
            if prev[1] > curr[0]:
                count += 1
                if prev[1] > curr[1]:
                    prev = curr
            else:
                prev = curr
        return count
```

</panel>
