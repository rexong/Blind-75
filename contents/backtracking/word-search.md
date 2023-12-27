<frontmatter>
  title: Backtracking - Word Search
</frontmatter>

# [Word Search](https://leetcode.com/problems/word-search/)
#### Difficulty: Medium

### Intuition
Can only use bruteforce method. <br>
For every cell, perform DFS. <br>
For DFS search up, down, left and right cell <br>
**Need to keep track of the path when doing DFS**
### Contraints
- $1\leqslant$ m, n$\leqslant 6$
- board only contains lower case alphabets.

## Approach
1. Find the length of row and column
2. Initialise a path as an empty set 
3. Define DFS with cell coordinates and word's index
    1. If word's index equals length of word, return True
    2. If coordinates out of range, coordinate already in path, or the character at word's index is not the same as the character in the cell, return False
    3. Add coordinate to path
    4. Perform DFS on up, down, left and right cell.
    5. Remove coordinate from path
    6. Return results
4. For every cell in board
    1. Perform DFS on the cell with word's index as 0
    2. If DFS return True, return True
5. Return False

### Complexity
#### Time Complexity: O(m * n * $4^{len(word)}$)
(m * n) to iterate the whole board. $4^{len(word)}$ for the DFS, base 4 as there are 4 directions.
#### Space Complexity: O(m * n * $4^{len(word)}$)
DFS recursive stack requires $4^{len(word)}$ call stack. And we are doing DFS on every cell, hence multiply by (m * n)
### Solution
<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def exist(self, board: List[List[str]], word: str) -> bool:
        ROWS, COLS = len(board), len(board[0])
        path = set()

        def dfs(r, c, i):
            if i == len(word):
                return True
            if (
                r < 0
                or c < 0
                or r == ROWS
                or c == COLS
                or word[i] != board[r][c]
                or (r, c) in path
            ):
                return False
            path.add((r, c))
            result = (
                dfs(r - 1, c, i + 1)
                or dfs(r + 1, c, i + 1)
                or dfs(r, c - 1, i + 1)
                or dfs(r, c + 1, i + 1)
            )
            path.remove((r, c))
            return result

        for r in range(ROWS):
            for c in range(COLS):
                if dfs(r, c, 0):
                    return True
        return False
```
</panel>

