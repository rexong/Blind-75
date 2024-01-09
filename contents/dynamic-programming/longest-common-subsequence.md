<frontmatter>
  title: Dynamic Programming - Longest Common Subsequence
</frontmatter>

# [Longest Common Subsequence](https://leetcode.com/problems/longest-common-subsequence/)

#### Difficulty: Medium

### Intuition

Can Solve using 2D DP method. <br>
Identify subproblem: <br>
Say we are matching the characters from the start 1. If characters matches, we need to find the LCS of both string excluding the matched characters 2. If characters not matches, we need to find the max of either (LCS of text1 without the first character and text2) or (LCS of text1 and text2 without the first character)

With this, we can construct a 2D table and apply a bottom up approach.

### Contraints

- $1\leqslant$ length of texts $\leqslant 1000$
- Only consists of lower case English

## Approach

1. Initialise length of `row` to length of text1 and length of `column` to length of text2
2. Initialise a 2D array with `row + 1` rows and `column + 1` columns where every cell is 0
3. Start from the cell (row, col), work on every column before moving up the row
   1. If text1[r] == text2[c], update cell with 1 + bottom right cell
   2. Update cell with the right cell or bottom cell, whichever is higher
4. Return the origin cell

### Complexity

#### Time Complexity: O(m \* n)

m and n are length of text1 and text2 respectively.

#### Space Complexity: O(m \* n)

For the 2D array.

### Solution

<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def longestCommonSubsequence(self, text1: str, text2: str) -> int:
        row = len(text1)
        col = len(text2)
        dp = [[0 for _ in range(col + 1)] for _ in range(row + 1)]
        for r in range(row - 1, -1, -1):
            for c in range(col - 1, -1, -1):
                if text1[r] == text2[c]:
                    dp[r][c] = 1 + dp[r + 1][c + 1]
                else:
                    dp[r][c] = max(dp[r + 1][c], dp[r][c + 1])

        return dp[0][0]
```

</panel>
