<frontmatter>
  title: Math & Geometry - Set Matrix Zeroes
</frontmatter>

# [Set Matrix Zeroes](https://leetcode.com/problems/set-matrix-zeroes/)
#### Difficulty: Medium

### Intuition
Changing the values immediately after spotting 0 will lead to cells changing to 0 even when it is not necessary.<br>
Instead, go through the matrix, find out which rows and columns need to update to 0. <br>
To do it in place, use the first row and first column to keep track of which row and columns need to be updated.
<br>
However, there will be one overlapping cell, for this cell, we will keep it as column flag. We use another boolean to keep track of the row flag.<br>

### Contraints
- $1\leqslant$ m, n $\leqslant 200$ 
 
## Approach
1. Set the `0`th row flag to 1
2. Initialise the row and column length
3. Iterate every cell in the matrix
    1. If cell is 0
        1. Update the `0`th row and the cell's column to 0
        2. If the row is 0, update the row flag to 0
        3. Else, Update the `0`th col and cell's row to 0
4. Iterate every cell in the matrix, skipping the first row and column
    1. If either the `0`th row of the cell's column or the `0`th column of the cell's row is 0, update cell to 0
5. If the top left cell is 0, set the first column to 0.
6. If the row flag is 0, set the first row to 0.

### Complexity
#### Time Complexity: O(m*n)
Iterate through every cell twice in the worst case. <br>
Once to find out which row and column to update, once to update the cell
#### Space Complexity: O(1)
As required by question, only one boolean is required. 
### Solution
<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def setZeroes(self, matrix: List[List[int]]) -> None:
        """
        Do not return anything, modify matrix in-place instead.
        """
        flag = 1
        numRow = len(matrix)
        numCol = len(matrix[0])
        for row in range(numRow):
            for col in range(numCol):
                if matrix[row][col] == 0:
                    matrix[0][col] = 0
                    if row == 0:
                        flag = 0
                    else:
                        matrix[row][0] = 0
        for row in range(1, numRow):
            for col in range(1, numCol):
                if matrix[0][col] == 0 or matrix[row][0] == 0:
                    matrix[row][col] = 0
        if matrix[0][0] == 0:
            for row in range(numRow):
                matrix[row][0] = 0
        if flag == 0:
            for col in range(numCol):
                matrix[0][col] = 0
```
