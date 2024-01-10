<frontmatter>
  title: Greedy - Jump Game
</frontmatter>

# [Jump Game](https://leetcode.com/problems/jump-game/)

#### Difficulty: Medium

### Intuition

Let the target be last index. <br>
Start from the last index and work to the first index. Determine if the current index + the element at the index can reach target. If so, update target to current index.

### Contraints

- $0\leqslant$ Length of nums $\leqslant 10000$

## Approach

1. Set target to the last index
2. Iterate every element from the last element
   1. If element + current index can reach target, update target to current index
3. Return True if target is 0 else, False

### Complexity

#### Time Complexity: O(n)

Visit every element once and only once.

#### Space Complexity: O(1)

No additional data structure required.

### Solution

<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def canJump(self, nums: List[int]) -> bool:
        goal = len(nums) - 1
        for i in range(len(nums) - 1, -1, -1):
            if i + nums[i] >= goal:
                goal = i
        return goal == 0
```

</panel>
