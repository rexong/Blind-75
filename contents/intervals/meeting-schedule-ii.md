<frontmatter>
  title: Intervals - Meeting Schedule II 
</frontmatter>

# [Meeting Schedule II](https://neetcode.io/problems/meeting-schedule-ii/)

#### Difficulty: Medium

### Intuition

Try drawing out the time line. The minimum number of days required would be the maximum number of overlaps at any point in time. <br>

### Contraints

- $0\leqslant$ Length of intervals $\leqslant 100$

## Approach

1. Initialise 2 arrays, one to sort by start time, one to sort by end time
2. Initialise start and end pointer to 0
3. Initialise count and maxCount to 0
4. While start pointer still in range
   1. If end pointer's end time > start pointer's start time, increment count and start pointer by 1
   2. Else, decrement count and increment end pointer by 1
   3. Update maxCount to either maxCount or count, whichever is higher
5. Return maxCount

### Complexity

#### Time Complexity: O(n logn)

For sorting the interval. <br>
Finding the intervals takes linear time, which can be subsume by the sorting of intervals.

#### Space Complexity: O(n)

For the start and end array, which are not sorted in place

### Solution

<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def minMeetingRooms(self, intervals: List[Interval]) -> int:
        starts = sorted(intervals, key=lambda interval : interval.start)
        ends = sorted(intervals, key=lambda interval : interval.end)
        startPtr, endPtr = 0, 0
        count, maxCount = 0, 0
        while startPtr < len(starts):
            if ends[endPtr].end > starts[startPtr].start:
                count += 1
                startPtr += 1
            else:
                count -= 1
                endPtr += 1
            maxCount = max(maxCount, count)
        return maxCount

```

</panel>
