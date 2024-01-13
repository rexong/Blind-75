<frontmatter>
  title: Trees - Binary Tree Maximum Path Sum
</frontmatter>

# [Binary Tree Maximum Path Sum](https://leetcode.com/problems/binary-tree-maximum-path-sum/)

#### Difficulty: Difficult

### Intuition

For any path, only one node in the path can be split, ie the node's left and right children are included in the path. For every other nodes in the path, either the left or right children is included in the path. <br>

With the above intuition, visit every node in the tree and treat the node as the node that can be split. Then recurse on the left and right subtree to find the maximum sum from the left and right subtree without spliting. <br>

Note that for every node, we want to compute the maximum path with the node as the splitting node and also the maximum path of the node with either of its children.

### Contraints

- $1\leqslant$ number of nodes $\leqslant 3 * 10^4$
- $-1000\leqslant$ node's value $\leqslant 1000$

## Approach

1. Initialise result to the root's vale
2. Define DFS
   1. If node is None, return 0
   2. Set leftMax to DFS on node's left child
   3. If leftMax < 0, set leftMax to 0
   4. Set rightMax to DFS on node's right child
   5. If rightMax < 0, set rightMax to 0
   6. Update result with node's value + leftMax + rightMax if the sum is more than result
   7. Return node's value with leftMax or rightMax, whichever is higher
3. Run DFS on root
4. Return result

### Complexity

#### Time Complexity: O(n)

Performing DFS on every node once and only once.

#### Space Complexity: O(1)

Constant space required for result.

### Solution

<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def maxPathSum(self, root: Optional[TreeNode]) -> int:
        self.res = root.val

        def helper(node):
            if not node:
                return 0
            leftMax = helper(node.left)
            leftMax = max(0, leftMax)
            rightMax = helper(node.right)
            rightMax = max(0, rightMax)
            self.res = max(self.res, node.val + leftMax + rightMax)
            return node.val + max(leftMax, rightMax)

        helper(root)
        return self.res
```

</panel>
