<frontmatter>
  title: Trees - Construct Binary Tree from Preorder and Inorder Traversal
</frontmatter>

# [Construct Binary Tree from Preorder and Inorder Traversal](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/)
#### Difficulty: Medium

### Intuition
Using 2 facts, 
1. First element in preorder is always the root
2. When partitioning first element in the inorder array, the left side is the left subtree and the right side is  the right subtree

### Contraints
- $1\leqslant$ length of preorder array $\leqslant 3000$ 
- length of preorder array == length of inorder array
 
## Approach
1. If preorder array is empty, return None
2. Initialise root, where the value of root is the first element of preorder array
3. Find the index of the first element of preorder array in the inorder array
4. Set the left and right child of root to buildTree with updated preorder array and inorder array
5. Return root

### Complexity
#### Time Complexity: O($n^2$)
Ultimately, we are performing build tree on every element in the array. <br>
For every build tree, we are using linear time to search for the index in the inorder array. <br>
#### Space Complexity: O(n)
For the recursive stack. 
### Solution
<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def buildTree(self, preorder: List[int], inorder: List[int]) -> Optional[TreeNode]:
        if not preorder:
            return None
        root = TreeNode(preorder[0])
        inorder_index = inorder.index(preorder[0])
        root.left = self.buildTree(preorder[1: inorder_index + 1], inorder[:inorder_index])
        root.right = self.buildTree(preorder[inorder_index + 1: ], inorder[inorder_index + 1:])
        return root
```
</panel>

