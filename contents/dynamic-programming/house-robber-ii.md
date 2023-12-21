<frontmatter>
  title: Dynamic Programming - House Robber II 
</frontmatter>

# [House Robber II](https://leetcode.com/problems/house-robber-ii/)
#### Difficulty: Medium

### Intuition
First house and last house are adjacent. <br>
We can reuse [House Robber]({{ baseUrl }}/contents/dynamic-programming/house-robber.html) on houses excluding the first house and houses excluding the second house.

### Contraints
- $1\leqslant$ n $\leqslant 100$ 
 
## Approach
1. Define House Robber as a helper function
2. If there is only one house, return the value of the house
3. Return the maximum value the robber can rob with either houses excluding first house or houses excluding second house

### Complexity
#### Time Complexity: O(n)
Running the array twice, once for each case.
#### Space Complexity: O(1)
No additional data structure required.
### Solution
<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def rob(self, nums: List[int]) -> int:
        def helper(nums):
            if not len(nums):
                return 0
            curr, prev = nums[0], 0
            for num in nums[1:]:
                temp = curr
                curr = max(num + prev, curr)
                prev = temp
            return curr
        if len(nums) == 1:
            return nums[0]
        return max(helper(nums[:-1]), helper(nums[1:]))
```
</panel>

