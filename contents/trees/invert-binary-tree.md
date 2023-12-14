<frontmatter>
  title: Trees - Invert Binary Tree
</frontmatter>

# [Invert Binary Tree](https://leetcode.com/problems/invert-binary-tree/)
#### Difficulty: Easy

### Intuition
Tree is easier with recursion. <br>
In this case, at each depth, flip the left and right pointer of each node.<br>
Then recurse the function on both children.

### Contraints
-  $0\leqslant$ number of nodes $\leqslant 100$ 
 
## Approach
1. If the root is null, return the root
2. Swap the left child and right child
3. Invert the left child
4. Invert the right child
5. Return root

### Complexity
#### Time Complexity: O(n)
Every node has to have its children swap, hence every node is visited once and only once.
#### Space Complexity: O(n)
Recursion stack takes up memory space for every node. Hence, linear space.
### Solution
<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def invertTree(self, root: Optional[TreeNode]) -> Optional[TreeNode]:
        if not root:
            return root
        temp = root.left
        root.left = root.right
        root.right = temp
        self.invertTree(root.left)
        self.invertTree(root.right)
        return root
```
</panel>
