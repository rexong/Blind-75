<frontmatter>
  title: Trees - Serialize and Deserialize Binary Tree
</frontmatter>

# [Serialize and Deserialize Binary Tree](https://leetcode.com/problems/serialize-and-deserialize-binary-tree/)

#### Difficulty: Difficult

### Intuition

Serialize with DFS using comma as a delimiter and N to represent None. <br>
Deserialize can be done with DFS as well, need a global pointer to keep track of the current element in the serialize string.

### Contraints

- $0\leqslant$ number of nodes $\leqslant 10^4$
- $-1000\leqslant$ node's value $\leqslant 1000$

## Approach

1. Implement Serialize
   1. Initialise result as an empty array
   2. Define DFS
      1. If node is None, append 'N' to result
      2. Append node's val to result
      3. Perform DFS on node's left child
      4. Perform DFS on node's right child
   3. Perform DFS on root
   4. Return result as a string with comma separating each element
2. Implement Deserialize
   1. Initialise i to 0
   2. Split data by comma
   3. Define DFS
      1. If data[i] is 'N', increment i by 1 and return None
      2. Create node with data[i] as value
      3. Increment i by 1
      4. Perform DFS to get node's left child
      5. Perform DFS to get node's right child
      6. Return node
   4. Return DFS

### Complexity

#### Time Complexity: O(n)

Serializing and deserializing will only visit each node once and only once.

#### Space Complexity:

##### Serialize - O(n)

For the result array.

##### Deserialize - O(1)

No additional data structure required.

### Solution

<panel header="Don't cheat yourself" type="dark">

```python
class Codec:

    def serialize(self, root):
        """Encodes a tree to a single string.

        :type root: TreeNode
        :rtype: str
        """
        res = []

        def dfs(node):
            if not node:
                res.append('N')
                return
            res.append(str(node.val))
            dfs(node.left)
            dfs(node.right)

        dfs(root)

        return ",".join(res)


    def deserialize(self, data):
        """Decodes your encoded data to tree.

        :type data: str
        :rtype: TreeNode
        """
        self.i = 0
        data = data.split(',')

        def dfs():
            if data[self.i] == 'N':
                self.i += 1
                return None
            node = TreeNode(int(data[self.i]))
            self.i += 1
            node.left = dfs()
            node.right = dfs()
            return node

        return dfs()
```

</panel>
