<frontmatter>
  title: Trees - Lowest Common Ancestor of a Binary Search Tree
</frontmatter>

# [Lowest Common Ancestor of a Binary Search Tree](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/)
#### Difficulty: Medium

### Intuition
If it requires a split from the node, it is the lowest common ancestor. <br>
Else, the node is either too big or too small for both `p` and `q`. In this case, find the lowest common ancestor of the respective subtree.

### Contraints
- $2\leqslant$ number of nodes $\leqslant 10^5$
- All Nodes' value are unique
- `p` != `q` and both exist in the tree
 
## Approach
1. If `root`'s value is less than `p`'s and `q`'s value, return the LCA of the right child of root
2. If `root`'s value is more than `p`'s and `q`'s value, return the LCA of the left child of root
3. Return `root`

### Complexity
#### Time Complexity: O(log n)
For every iteration required, we only search one of the children.
#### Space Complexity: O(log n)
For every recursive stack, same argument as the time complexity
### Solution
<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def lowestCommonAncestor(self, root: 'TreeNode', p: 'TreeNode', q: 'TreeNode') -> 'TreeNode':
        if root.val < p.val and root.val < q.val:
            return self.lowestCommonAncestor(root.right, p, q)
        if root.val > p.val and root.val > q.val:
            return self.lowestCommonAncestor(root.left, p, q)
        return root
```
</panel>

