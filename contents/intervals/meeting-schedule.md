<frontmatter>
  title: Intervals - Meeting Schedule
</frontmatter>

# [Meeting Schedule](https://neetcode.io/problems/meeting-schedule/)

#### Difficulty: Easy

### Intuition

Sort intervals by start time in ascending order. <br>
Compare pairs of intervals, first and second, at a time, check if there is overlap. <br>
Overlap occurs when end time of first is more than start time of second.

### Contraints

- $0\leqslant$ Length of intervals $\leqslant 100$

## Approach

1. If intervals is empty, return True
2. Sort intervals based on the interval start
3. Initialise currentInterval to the first interval of the sorted intervals
4. For every interval starting from the second interval
   1. If currentInterval's end > interval's start, return False
   2. Update currentInterval with interval
5. Return True

### Complexity

#### Time Complexity: O(n logn)

Sorting the intervals takes nlogn time, which subsumes the linear time taken to find any overlaps.

#### Space Complexity: O(1)

Sorting the intervals can be done in place.

### Solution

<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
  def canAttendMeetings(self, intervals: List[Interval]) -> bool:
      if len(intervals) == 0:
          return True
      intervals.sort(key= lambda interval : interval.start)
      currInterval = intervals[0]
      for i in range(1, len(intervals)):
          if currInterval.end > intervals[i].start:
              return False
          currInterval = intervals[i]
      return True

```

</panel>
