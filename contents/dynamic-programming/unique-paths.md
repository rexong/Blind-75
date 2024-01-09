<frontmatter>
  title: Dynamic Programming - Unique Paths
</frontmatter>

# [Unique Paths](https://leetcode.com/problems/unique-paths/)

#### Difficulty: Medium

### Intuition

Use Bottom Up 2D DP to solve this. <br>
Every cell in DP represents the number of path to the bottom right corner. <br>
For every cell in the last row and last column, the number of path is 1. <br>
For every other cells, the number of path is the sum of the cell to the right and bottom of the cell.

### Contraints

- $1\leqslant$ m, n $\leqslant 100$

## Approach

1. Initialise a 2D array with m as rows and n as column where every element is 0
2. Set every cell in the last row and column to 1
3. Starting from the bottom right cell that does not include the last row and column, iterate every columns first, then move up the row
   1. Update the cell to the sum of cell to the right and bottom
4. Return the origin cell

### Complexity

#### Time Complexity: O(m \* n)

Visiting every cell once and only once

#### Space Complexity: O(m \* n)

For the 2D array

### Solution

<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def uniquePaths(self, m: int, n: int) -> int:
        dp = [[0 for _ in range(n)] for _ in range(m)]
        for i in range(0, m):
            dp[i][n - 1] = 1
        for j in range(0, n):
            dp[m - 1][j] = 1

        for r in range(m - 2, -1, -1):
            for c in range(n - 2, -1, -1):
                dp[r][c] = dp[r + 1][c] + dp[r][c + 1]

        return dp[0][0]

```

</panel>
