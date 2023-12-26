<frontmatter>
  title: Binary Search - Find Minimum in Rotated Sorted Array
</frontmatter>

# [Find Minimum in Rotated Sorted Array](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/)
#### Difficulty: Medium

### Intuition
For a single rotated sorted array, there are 2 kinds of array. <br>
1. Array that is not rotated, hence, the minimum element is the element on the left.
2. Array that is rotated, there will be 2 sides, left and right side. Both sides are sorted, and the minimum element in the right half of the array. 
To check for scenario 1, the left element is smaller than or equal to right element. <br>
To check for scenario 2, the left element is smaller than or equal to the middle element. 

### Contraints
- $1\leqslant$ length of array $\leqslant 5000$ 
- All element in the array are unique.

## Approach
1. Initialise left and right pointers to the start and end of the array
2. Initialise result to the first element in the array
3. While left pointer $\leqslant$ right pointer
    1. If the element on the left pointer $\leqslant$ element on right pointer, set result to either result or the element on the left pointer, whichever is lower. Then, break the iteration.
    2. Find the middle pointer
    3. Set result to either result or the element on the middle pointer, whichever is lower.
    4. If element on the left pointer $\leqslant$ element on the middle pointer, set left pointer to right of middle pointer
    5. Else, set right pointer to left of middle pointer
4. Return result

### Complexity
#### Time Complexity: O(log n)
For every iteration, we reduce the search space in the array by half. 
#### Space Complexity: O(1)
Only need 3 pointers
### Solution
<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def findMin(self, nums: List[int]) -> int:
        l, r = 0, len(nums) - 1 
        result = nums[0]
        while l <= r:
            if nums[l] <= nums[r]:
                result = min(result, nums[l])
                break
            m = (r + l) // 2
            result = min(result, nums[m])
            if nums[l] <= nums[m]:
                l = m + 1
            else:
                r = m - 1
        return result
```
</panel>

