<frontmatter>
  title: Trees - Subtree of Another Tree
</frontmatter>

# [Subtree of Another Tree](https://leetcode.com/problems/subtree-of-another-tree/)
#### Difficulty: Easy

### Intuition
_Pre-requisites: [Same Tree]({{ baseUrl }}/contents/trees/same-tree.html)_ <br>
If the value of corresponding node in both tree is not the same, check is subtree using either the left **or** right child with the subroot. <br>
If the value of corresponding node in both tree is the same, it does not mean that it definately contain the subtree. Hence, we have to check either the remaining tree is same as the subroot, or check is subtree using either the left **or** right child with the subroot

### Contraints
- $0\leqslant$ number of nodes in root $\leqslant 2000$ 
- $0\leqslant$ number of nodes in subroot $\leqslant 1000$ 
 
## Approach
1. If root and subroot are both null, return `True`
2. If either root or subroot is null, return `False`
3. If value of root and value of subroot is not the same, check and return if subroot is in the left or right child
4. Else, check and return if the root is same as subroot, or if subroot is in the left or right child

### Complexity
#### Time Complexity: O(n * m)
Suppose the size of the root tree is n and size of the subroot tree is m. <br>
In the worse case, for every node in root, we have to check it with every node in the subroot
#### Space Complexity: O(h)
h is the height of the call stack due to recursion. 
### Solution
<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def isSubtree(self, root: Optional[TreeNode], subRoot: Optional[TreeNode]) -> bool:
        if not root and not subRoot:
            return True
        if not root or not subRoot:
            return False
        if root.val != subRoot.val:
            return self.isSubtree(root.left, subRoot) or self.isSubtree(root.right, subRoot)
        return self.isSameTree(root, subRoot) or (self.isSubtree(root.left, subRoot) or self.isSubtree(root.right, subRoot))
    
    def isSameTree(self, tree1: Optional[TreeNode], tree2: Optional[TreeNode]) -> bool:
        if not tree1 and not tree2:
            return True
        if not tree1 or not tree2:
            return False
        if tree1.val != tree2.val:
            return False
        return self.isSameTree(tree1.left, tree2.left) and self.isSameTree(tree1.right, tree2.right)
```
</panel>
