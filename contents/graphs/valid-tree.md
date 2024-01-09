<frontmatter>
  title: Graphs - Valid Tree
</frontmatter>

# [Valid Tree](https://neetcode.io/problems/valid-tree/)

#### Difficulty: Medium

### Intuition

To check for valid tree, ensure

1.  No loops in graph
2.  Graph is connected

### Contraints

- $1\leqslant$ n $\leqslant 100$
- $0\leqslant$ number of edges $\leqslant n * (n - 1)/2$

## Approach

1. Create a adjacency list for every node
2. Initialise an empty set, `visited`
3. Define DFS with `node` and `prev` parameters
   1. If `node` is in visited, return False
   2. Add `node` into visited
   3. For every adjacent node from `node`
      1. If adjacent node == `prev`, skip this adjacent node
      2. Recurse DFS on adjacent node and `node`
      3. If DFS is False, return False
   4. Return True
4. If DFS(0, -1) is True, return True if length of visited = n
5. Return False

### Complexity

#### Time Complexity: O(V + E)

V for the number of nodes and E for the number of edges. <br>
To initialise the adjacency list, need to visit every edge. <br>
For DFS, it will go through every node and every edge.

#### Space Complexity: O(V + E)

For the adjacency list.

### Solution

<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def validTree(self, n: int, edges: List[List[int]]) -> bool:
        adjList = [[] for _ in range(n)]
        for node1, node2 in edges:
            adjList[node1].append(node2)
            adjList[node2].append(node1)

        visited = set()

        def dfs(node, prev):
            if node in visited:
                return False
            visited.add(node)
            adjNodes = adjList[node]
            for adjNode in adjNodes:
                if adjNode == prev:
                    continue
                if not dfs(adjNode, node):
                    return False
            return True

        if dfs(0, -1):
            return len(visited) == n
        return False
```

</panel>
