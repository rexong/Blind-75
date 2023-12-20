<frontmatter>
  title: Trees - Validate Binary Search Tree
</frontmatter>

# [Validate Binary Search Tree](https://leetcode.com/problems/validate-binary-search-tree/)
#### Difficulty: Medium

### Intuition
Using a DFS approach. <br>
Use a helper function to keep track of the boundary at each node. <br>
This is because there may exist a scenario where a node in the right tree has value less than root. 

### Contraints
- $1\leqslant$ number of nodes $\leqslant 10^4$ 
 
## Approach
1. Create a helper function, with node, left and right boundary as arguments
    1. If node is null, return true
    2. If the value of left child is more than root or value of right child more than root, return False
    3. Return helper on left and right child, with the left and right boundary updated
2. Return helper on root with `-inf` and `inf`

### Complexity
#### Time Complexity: O(n)
Every node is visited once and only once
#### Space Complexity: O(n)
Due to the recursive stack
### Solution
<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def isValidBST(self, root: Optional[TreeNode]) -> bool:
        def helper(node, left, right):
            if not node:
                return True
            if not (node.val > left and node.val < right):
                return False
            return helper(node.left, left, node.val) and helper(node.right, node.val, right)
        return helper(root, -float("inf"), float("inf"))
```
</panel>

