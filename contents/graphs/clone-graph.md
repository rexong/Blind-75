<frontmatter>
  title: Graphs - Clone Graph
</frontmatter>

# [Clone Graph](https://leetcode.com/problems/clone-graph/)
#### Difficulty: Medium

### Intuition
Use a dictionary to map the old node to new node. Then perform DFS on each node to clone.

### Contraints
- $0\leqslant$ Number of nodes $\leqslant 100$
- $1\leqslant$ Node's value $\leqslant 100$
- Nodes' value are unique.

## Approach
1. If node is None, return empty list 
2. Initialise empty dictionary
3. Define DFS with `old` and `new` node
    1. Iterate every neighbour in `old`'s neighbour
        1. If neighbour's value in dictionary, add the new neighbour's node into `new`'s neighbour
        2. Create new Node, add new node to dictionary with key as the node's value
        3. Add new Node in step 3.2 to `new`'s neighbour
        4. Perform dfs on the neighbour's old and new node
4. Create new node for the first node
5. Add the node in step 4 into dictionary with key as the node's value
6. Perform dfs on the old and new first node

### Complexity
#### Time Complexity: O(V + 2*E)
Clone every node takes V time, and each node iterates through each edge twice.

#### Space Complexity: O(V)
For the recursive stack, stack call is required for every node to be cloned.
### Solution
<panel header="Don't cheat yourself" type="dark">

```python
from typing import Optional
class Solution:
    def cloneGraph(self, node: Optional['Node']) -> Optional['Node']:
        if not node:
            return None
        d = {}

        def dfs(old, new):
            for node in old.neighbors:
                if node.val in d:
                    new.neighbors.append(d[node.val])
                else:
                    newNode = Node(node.val, [])
                    new.neighbors.append(newNode)
                    d[node.val] = newNode
                    dfs(node, newNode)
            return
        
        newNode = Node(node.val, [])
        d[node.val] = newNode
        dfs(node, newNode)
        return newNode
```
</panel>

