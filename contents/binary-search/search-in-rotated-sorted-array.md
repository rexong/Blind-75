<frontmatter>
  title: Binary Search - Search in Rotated Sorted Array
</frontmatter>

# [Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/)
#### Difficulty: Medium

### Intuition
Requires Knowledge from [Find Minimum in Rotated Sorted Array]({{ baseUrl }}/contents/binary-search/find-minimum-in-rotated-sorted-array.html) <br>
If the left to middle pointer's elements are sorted, and target is between the left to middle pointers' element, search the elements between left to middle pointer. Else, search the elements between the middle to right pointers' elements. <br>
If the left to middle pointer's elements are not sorted, and target is between middle to right pointers' element, search the elements between middle to right pointer. Else, search the elements between the left to middle pointers' elements.

### Contraints
- $1\leqslant$ length of array $\leqslant 5000$
- All element in array are unique.

## Approach
1. Initialise left and right pointer to the start and end of the array
2. While the left pointer $\leqslant$ right pointer
    1. Find the middle pointer
    2. If the target is the element of middle pointer, return the middle pointer
    3. If left pointer to middle pointer is sorted,
        1. If target is between the element of left and middle pointer, move right pointer to the left of middle pointer
        2. Else, move left pointer to the right of the middle pointer
    4. If middle to right pointer is sorted,
        1. If target is between the element of middle and right pointer, move left pointer to the right of the middle pointer
        2. Else, move right pointer to the left of the middle pointer.
3. Return -1 if iteration ends

### Complexity
#### Time Complexity: O(log n)
Every iteration, we reduce the search space in the array by half.
#### Space Complexity: O(1)
Only need 3 pointers
### Solution
<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        l, r = 0, len(nums) - 1
        while l <= r:
            m = (r + l) // 2
            if target == nums[m]:
                return m
            if nums[l] <= nums[m]:
                if target <= nums[m] and target >= nums[l]:
                    r = m - 1
                else:
                    l = m + 1
            else:
                if target >= nums[m] and target <= nums[r]:
                    l = m + 1
                else:
                    r = m - 1
        return -1
```
</panel>

