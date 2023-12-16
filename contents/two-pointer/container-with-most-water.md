<frontmatter>
  title: Two Pointer - Container with Most Water
</frontmatter>

# [Container with Most Water](https://leetcode.com/problems/container-with-most-water/)
#### Difficulty: Medium

### Intuition
Use two pointer, one at the start of array and one at the end of array. <br>
Shift the pointer with the shorter height.

Calculating the height<br>
  - Minimum height of 2 lines
  - Distance between 2 lines
  - Multiply both results

### Contraints
- $2\leqslant$ length of array $\leqslant 10^5$ 
- $0\leqslant$ element $\leqslant 10^4$ 
 
## Approach
1. Initialise area to 0
2. Initialise start to 0 and end to the end of the array
3. Iterate while start is not more than end
    1. Find the distance between start and end
    2. Find the minimum height between the two pointer
    3. Calculate the area, get the maximum area
    4. If element at start is less than element at end, increment start by 1
    5. Else, decrement end by 1
4. Return area

### Complexity
#### Time Complexity: O(n)
Every element in the array is visited once and only once, hence linear time. 
#### Space Complexity: O(1)
No extra data struture used, only require 2 pointer and 1 integer. 
### Solution
<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def maxArea(self, height: List[int]) -> int:
        area = 0
        start = 0
        end = len(height) - 1
        while start <= end:
            distance = end - start
            min_height = min(height[start], height[end])
            area = max(area, min_height * distance)
            if height[start] < height[end]:
                start += 1
            else:
                end -= 1
        return area
```
</panel>
