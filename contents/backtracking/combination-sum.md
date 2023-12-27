<frontmatter>
  title: Backtracking - Combination Sum
</frontmatter>

# [Combination Sum](https://leetcode.com/problems/combination-sum/)
#### Difficulty: Medium

### Intuition
Bruteforce method
- Branch to every element at every level of the tree. 
- Stop only when target is reached or exceeded.

**Problem: Does not account for duplicated sequence**

Better Solution
- At every level of the tree, decide whether to include or exclude the element. 

### Contraints
- $1\leqslant$ length of candidates $\leqslant 30$
- Every element in candidates are unique
 
## Approach
1. Initialise results as empty list 
2. Define DFS Algorithm with current index, `i`, of candidates, total and curr
    1. If total more than target or i more than length of candidates, return
    2. If target equals total, append curr to results and return
    3. Append `i`th element of candidate into curr
    4. Perform DFS on `i`, curr and updated total
    5. Remove the element added in step 2.3 
    6. Perform DFS on `i+1`, curr and total
3. Perform DFS on the first element in candidates
4. Return results

<box type="info" header="##### Special Tips">
  <md>
    For Step 2.2, remember to copy the curr array. Else, any modification to the curr array for the rest of the iteration will affect the array that is appended to results. 
  </md> 
</box>

### Complexity
#### Time Complexity: O($2^{target}$)
At every node, 2 decisions are made. The furtherest depth possible for any target is the target itself, ie, sum of 1 until the target
#### Space Complexity: O($2^{target}$)
This is for the recursive stack, the reasoning is similar to time complexity. Worst case, we would need to build a binary tree of depth target.
### Solution
<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def combinationSum(self, candidates: List[int], target: int) -> List[List[int]]:
        results = []
        
        def dfs(i, total, curr):
            if total > target or i >= len(candidates):
                return
            if total == target:
                results.append(curr.copy()) #important
                return
            curr.append(candidates[i])
            dfs(i, total + candidates[i], curr)
            curr.pop()
            dfs(i + 1, total, curr)
        
        dfs(0, 0, [])

        return results
```
</panel>

