<frontmatter>
  title: Trees - Binary Tree Level Order Traversal
</frontmatter>

# [Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal/)
#### Difficulty: Medium

### Intuition
Need to use BFS. <br>
Every time we access the queue, it indicates that it is a new level and every element in the queue belongs to that level.

### Contraints
- $0\leqslant$ number of nodes $\leqslant 2000$
 
## Approach
1. Initialise an empty array for the results
2. Initialise a queue with the root of the tree as the first element
3. While the queue is not empty
    1. Initialise an empty array for the current level
    2. Find out the length of the current queue
    3. Iterate every element in the queue
        1. Pop the first element in the queue
        2. If the element is None, skip the element
        3. Append the value of first element into the level's array
        4. Append the left and right child into the queue
    4. If the level's array is not empty, append it to the results array
4. Return the results array

### Complexity
#### Time Complexity: O(n)
BFS requires to traverse through every node in the tree.
#### Space Complexity: O(n)
Requires queue which at the worst case contains every node in the tree.
### Solution
<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def levelOrder(self, root: Optional[TreeNode]) -> List[List[int]]:
        results = []
        queue = [root]
        while queue:
            result = []
            queueLength = len(queue)
            for i in range(queueLength):
                node = queue.pop(0)
                if node:
                    result.append(node.val)
                    queue.append(node.left)
                    queue.append(node.right)
            if result:
                results.append(result)
        return results
```
</panel>

