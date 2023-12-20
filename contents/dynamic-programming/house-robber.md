<frontmatter>
  title: Dynamic Programming - House Robber
</frontmatter>

# [House Robber](https://leetcode.com/problems/house-robber/)
#### Difficulty: Medium

### Intuition
For every num in the array, update it to the either itself + the previous **valid** neighbour or its previous neighbour, whichever is higher.

### Contraints
- $1\leqslant$ n $\leqslant 45$ 
 
## Approach
1. Initialise `curr` to first element
2. Initialise `prev` to 0
3. Iterate the array, skipping the first element
    1. Set `curr` to max(`prev` + element, `curr`)
    2. Set `prev` to `curr`
4. Return `curr`

### Complexity
#### Time Complexity: O(n)
Access every element in the array once and only once.
#### Space Complexity: O(1)
Using only 2 pointer, `curr` and `prev`
### Solution
<panel header="Don't cheat yourself" type="dark">

```python
  class Solution:
    def rob(self, nums: List[int]) -> int:
        curr, prev = nums[0], 0
        for num in nums[1:]:
            temp = curr
            curr = max(num + prev, curr)
            prev = temp
        return curr
```
</panel>

