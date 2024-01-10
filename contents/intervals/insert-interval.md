<frontmatter>
  title: Intervals - Insert Interval
</frontmatter>

# [Insert Interval](https://leetcode.com/problems/insert-interval/)

#### Difficulty: Medium

### Intuition

Check if the newInterval should be entirely before, after or overlaps each interval. <br>
If before, insert newInterval before the interval. Since newInterval is inserted, we can return the rest of the interval as well. <br>
If after, move to the next interval. <br>
If overlaps, update newInterval with newInterval and current interval such that newInterval is the longest interval that can be formed.

### Contraints

- $0\leqslant$ Length of intervals $\leqslant 1000$

## Approach

1. Initialise result as empty list
2. Iterate every interval
   1. If newInterval is entirely before interval
      1. Append newInterval into result
      2. Return result with the rest of the intervals
   2. If newInterval is entirely after interval
      1. Append interval into result
   3. Else, there is an overlap
      1. Update newInterval by taking the minimum start and maximum end of newInterval and interval
3. Append newInterval into result
4. Return result

### Complexity

#### Time Complexity: O(n)

Iterate through every interval once and only once.

#### Space Complexity: O(1)

No additional data structure required.

### Solution

<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def insert(self, intervals: List[List[int]], newInterval: List[int]) -> List[List[int]]:
        result = []

        # returns true if interval1 is before interval2
        def isBefore(interval1, interval2):
            return interval1[1] < interval2[0]

        # returns true if interval1 is after interval2
        def isAfter(interval1, interval2):
            return interval1[0] > interval2[1]

        for i in range(len(intervals)):
            interval = intervals[i]
            if isBefore(newInterval, interval):
                result.append(newInterval)
                return result + intervals[i:]
            if isAfter(newInterval, interval):
                result.append(interval)
            else:
                newInterval[0] = min(newInterval[0], interval[0])
                newInterval[1] = max(newInterval[1], interval[1])
        result.append(newInterval)
        return result

```

</panel>
