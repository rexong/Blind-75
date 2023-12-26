<frontmatter>
  title: Trees - Kth Smallest Element in a BST
</frontmatter>

# [Kth Smallest Element in a BST](https://leetcode.com/problems/kth-smallest-element-in-a-bst/)
#### Difficulty: Medium

### Intuition
Iterative Inorder Traversal.

### Contraints
- $1\leqslant$ number of nodes $\leqslant 10^4$
- $1\leqslant$ k $\leqslant$ number of nodes

## Approach
1. Initialise n to 0
2. Initialise empty stack
3. Initialise pointer to root
4. While pointer or stack not None
    1. While pointer not None, add node to stack and go left
    2. Pop element off stack, set pointer to the element
    3. Increment n by 1 
    4. If n == k, return the pointer's value
    5. Set pointer to the right child of the node.

### Complexity
#### Time Complexity: O(n)
Suppose the worst case, every node would have to be visited once.
#### Space Complexity: O(log n)
Worst case occurs when half of the tree is in the stack. The stack would not have linear space because it will iterate through the left sides first, and pop off the stack before moving to the right.
### Solution
<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def kthSmallest(self, root: Optional[TreeNode], k: int) -> int:
        n = 0
        stack = []
        ptr = root
        while ptr or stack:
            while ptr:
                stack.append(ptr)
                ptr = ptr.left
            ptr = stack.pop()
            n += 1
            if n == k:
                return ptr.val
            ptr = ptr.right
        return -1
```
</panel>

