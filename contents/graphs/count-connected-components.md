<frontmatter>
  title: Graphs - Count Connected Components
</frontmatter>

# [Count Connected Components](https://neetcode.io/problems/count-connected-components/)

#### Difficulty: Medium

### Intuition

Run DFS on all nodes until every node is visited. Every time the DFS stops, increment count.

### Contraints

- $1\leqslant$ n $\leqslant 100$
- $0\leqslant$ Length of edges $\leqslant n * (n-1) / 2$

## Approach

1. Construct adjacency list from the edges
2. Initialise visited as empty set and count as 0
3. Define DFS
   1. If node is visited, skip this node
   2. Add node to visited
   3. For every adjacent node
      1. If adjacent node == prev, return
      2. recurse DFS on adjacent node
4. For every node
   1. If node is visited, skip this node
   2. DFS on node
   3. Increment count by 1
5. Return count

### Complexity

#### Time Complexity: O(V + E)

DFS take number of nodes and edges.

#### Space Complexity: O(V + E)

For the adjacency list.

### Solution

<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def countComponents(self, n: int, edges: List[List[int]]) -> int:
        adjList = [[] for _ in range(n)]
        for node1, node2 in edges:
            adjList[node1].append(node2)
            adjList[node2].append(node1)

        visited = set()
        count = 0

        def dfs(node, prev):
            if node in visited:
                return
            visited.add(node)
            adjNodes = adjList[node]
            for adjNode in adjNodes:
                if adjNode == prev:
                    continue
                dfs(adjNode, node)

        for node in range(n):
            if node in visited:
                continue
            dfs(node, -1)
            count += 1
        return count

```

</panel>
