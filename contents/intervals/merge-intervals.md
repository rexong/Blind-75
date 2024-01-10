<frontmatter>
  title: Intervals - Merge Intervals
</frontmatter>

# [Merge Intervals](https://leetcode.com/problems/merge-intervals/)

#### Difficulty: Medium

### Intuition

If there is an overlap, merge the list.

### Contraints

- $0\leqslant$ Length of intervals $\leqslant 1000$

## Approach

1. Sort intervals by start time
2. Initialise result as empty list
3. Set prevInterval to the first element in intervals
4. For every interval starting from second interval
   1. Set curr to interval
   2. If there is an overlap between prev and curr, update prev's end to either prev's end or curr's end, whichever is higher
   3. If there is no overlap,
      1. Append prevInterval to result
      2. Set prevInterval to curr
5. Append prevInterval to result
6. Return result

### Complexity

#### Time Complexity: O(n log n)

For sorting the intervals. Merging the intervals takes linear time.

#### Space Complexity: O(1)

No additional data structure required

### Solution

<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def merge(self, intervals: List[List[int]]) -> List[List[int]]:
        intervals.sort(key=lambda interval : interval[0])
        res = []
        prevInterval = intervals[0]
        for i in range(1, len(intervals)):
            curr = intervals[i]
            if prevInterval[1] >= curr[0]:
                prevInterval[1] = curr[1] if prevInterval[1] < curr[1] else prevInterval[1]
            else:
                res.append(prevInterval)
                prevInterval = curr
        res.append(prevInterval)
        return res


```

</panel>
