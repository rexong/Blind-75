<frontmatter>
  title: Graphs - Number of Islands
</frontmatter>

# [Number of Islands](https://leetcode.com/problems/number-of-islands/)
#### Difficulty: Medium

### Intuition
When we encounter the number `1`, increment the number of islands found by 1 and perform a BFS/DFS to find the remaining area of the island. Update the found island value to some other values.

### Contraints
- $1\leqslant$ m, n$\leqslant 300$
- grid is either 1 or 0, but mutable

## Approach
1. Get length of rows and columns
2. Initialise count to 0
3. Define BFS with the cell coordinate
    1. If coordinate out of bound, coordinate already visited, or coordinate references 0, return False
    2. Update the element of the cell to `v`
    3. Perform BFS on up, down, left and right cell
4. For every cell in grid
    1. If cell references `1`, increment count by 1 and perform BFS on cell
5. Return count

### Complexity
#### Time Complexity: O(m * n)
Need to iterate every cell. If BFS need to be executed, at the worse case, the whole grid is an island, then only need to visit the cell one more time. 
#### Space Complexity: O(1)
No additional data structure required.
### Solution
<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def numIslands(self, grid: List[List[str]]) -> int:
        ROWS, COLS = len(grid), len(grid[0])
        count = 0

        def bfs(r, c):
            if (r < 0 or c < 0 or r >= ROWS or c >= COLS or grid[r][c] == 'v' or grid[r][c] == "0"):
                return 
            grid[r][c] = 'v'
            bfs(r + 1, c)
            bfs(r - 1, c)
            bfs(r, c + 1)
            bfs(r, c - 1)

        for r in range(ROWS):
            for c in range(COLS):
                if grid[r][c] == '1':
                    count += 1
                    bfs(r, c)
        return count
```
</panel>

