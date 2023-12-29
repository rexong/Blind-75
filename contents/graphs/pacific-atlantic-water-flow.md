<frontmatter>
  title: Graphs - Pacific Atlantic Water Flow
</frontmatter>

# [Pacific Atlantic Water Flow](https://leetcode.com/problems/pacific-atlantic-water-flow/)
#### Difficulty: Medium

### Intuition
Break the question into 2 parts, cells that can flow to pacific ocean and cells that can flow to atlantic ocean.
For each cell `c`, determine if it can flow to either oceans, if it can, perform DFS on the adjacent cells to see if they can flow into the oceans using cell `c`. <br>
Then take the cells that can flow in both oceans.

### Contraints 
- $1\leqslant$ m, n$\leqslant 200$

## Approach
1. Initialise 2 sets, pacific and atlantic.
2. Initialise the number of rows and columns
3. Define the search for pacific
    1. If cell is out of bound or cell is already in pacific, return
    2. If cell is adjacent to pacific ocean or value of cell more than previous height
        1. Add cell into pacific
        2. Perform DFS on every neighbour
4. Define the search for atlantic, similar to step 3 
5. Perform pacific search on the top left cell.
6. Perform atlantic search on the bottom right cell. 
7. Initialise results array.
8. For every cell,
    1. If cell is in both oceans, add to results
9. Return results

### Complexity
#### Time Complexity: O(m * n)
Search for both oceans will iterate every cell.
Search for the cell that is in both oceans will also iterate through every cell.
#### Space Complexity: O(m * n)
2 sets for each oceans, could potentially contain every cell. 
### Solution
<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def pacificAtlantic(self, heights: List[List[int]]) -> List[List[int]]:
        ROWS, COLS = len(heights), len(heights[0])
        visitPacific = set()
        visitAtlantic = set()

        def checkPacific(r, c, prevHeight):
            if (
                r < 0
                or c < 0
                or r >= ROWS
                or c >= COLS
                or (r, c) in visitPacific
            ):
                return
            if r == 0 or c == 0 or heights[r][c] >= prevHeight:
                visitPacific.add((r, c))
                checkPacific(r - 1, c, heights[r][c])
                checkPacific(r + 1, c, heights[r][c])
                checkPacific(r, c - 1, heights[r][c])
                checkPacific(r, c + 1, heights[r][c])
                return
            return
        
        def checkAtlantic(r, c, prevHeight):
            if (
                r < 0
                or c < 0
                or r >= ROWS
                or c >= COLS
                or (r, c) in visitAtlantic
            ):
                return
            if r == ROWS - 1 or c == COLS - 1 or heights[r][c] >= prevHeight:
                visitAtlantic.add((r, c))
                checkAtlantic(r - 1, c, heights[r][c])
                checkAtlantic(r + 1, c, heights[r][c])
                checkAtlantic(r, c - 1, heights[r][c])
                checkAtlantic(r, c + 1, heights[r][c])
                return

        checkPacific(0, 0, 0)
        checkAtlantic(ROWS-1, COLS-1, 0)
        results = []
        for r in range(ROWS):
            for c in range(COLS):
                if (r,c) in visitPacific and (r,c) in visitAtlantic:
                    results.append([r,c])
        return results
```
</panel>

