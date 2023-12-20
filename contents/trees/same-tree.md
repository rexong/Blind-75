<frontmatter>
  title: Trees - Same Tree
</frontmatter>

# [Same Tree](https://leetcode.com/problems/same-tree/)
#### Difficulty: Easy

### Intuition
False iff
  - Either one of the tree is empty
  - Value of the corresponding node in the tree is not the same
Recurse and check if the tree is the same for the left and right children.

<box type="info" header="##### Special Tips">
  <md>
    Usually when checking for trees, we should check up and until `null`. 
  </md> 
</box>

### Contraints
- $0\leqslant$ number of nodes $\leqslant 100$ 
 
## Approach
1. If both tree is null, return `True`
2. If either tree is null or value of node in both trees is not the same, return `False`
3. Return check same tree for left **and** right child

### Complexity
#### Time Complexity: O(min(n, m))
The number of nodes in the first and second tree are n and m. Given that if the trees are not the same, one tree must be smaller than the other one. Hence, we take the minimum number of node of both trees.
#### Space Complexity: O(min(n, m))
Recursive stack takes up space in memory. Same argument as the time complexity.
### Solution
<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def isSameTree(self, p: Optional[TreeNode], q: Optional[TreeNode]) -> bool:
        if not p and not q:
            return True
        if not p or not q or p.val != q.val:
            return False
        return self.isSameTree(p.left, q.left) and self.isSameTree(p.right, q.right)
```
</panel>
