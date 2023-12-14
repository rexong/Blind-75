<frontmatter>
  title: Trees - Maximum Depth of Binary Tree
</frontmatter>

# [Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/)
#### Difficulty: Easy

### Intuition
**Recursion**, for every level, it is 1 + (max depth of either left or right child)

### Contraints
- $0\leqslant$ number of nodes $\leqslant 10^4$ 
 
## Approach
1. If root is null, return 0
2. Else return 1 + max depth of left or right child

### Complexity
#### Time Complexity: O(n)
Every node is visited once and only once, hence linear time.
#### Space Complexity: O(n)
Every recursion stack for every node. Hence, linear space
### Solution
<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def maxDepth(self, root: Optional[TreeNode]) -> int:
        if not root:
            return 0
        return 1 + max(self.maxDepth(root.left), self.maxDepth(root.right))
```
</panel>
