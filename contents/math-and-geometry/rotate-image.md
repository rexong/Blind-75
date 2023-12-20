<frontmatter>
  title: Math & Geometry - Rotate Image
</frontmatter>

# [Rotate Image](https://leetcode.com/problems/rotate-image/)
#### Difficulty: Medium

### Intuition
We define the matrix as layers.
Use 4 pointer, each pointing to one corner of the layer.
The actual values in each cells does not mean much.

### Contraints
- $1\leqslant$ n $\leqslant 20$
 
## Approach
1. Initialise left and right pointer to the start and end columns
2. Initialise top and write pointer to the start and end rows
3. While left pointer < right pointer
    1. Iterate left - right times (number of times to swap one layer)
        1. Swap the top left cell with an offset of the layer with the top right cell with an offset.
        2. Swap the top left cell with an offset of the layer with the bottom right cell with an offset.
        2. Swap the top left cell with an offset of the layer with the bottom left cell with an offset. 
    2. Increment both left and top pointers
    3. Decrement both right and bottom pointers

### Complexity
#### Time Complexity: O($n^2$)
The algorithm will visit every cell once and only once.
#### Space Complexity: O(1)
Stated as requirement by question. Algorithm is done in place.
### Solution
<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def rotate(self, matrix: List[List[int]]) -> None:
        """
        Do not return anything, modify matrix in-place instead.
        """
        l, r = 0, len(matrix) - 1
        t, b = 0, len(matrix[0]) - 1
        while l < r:
            for i in range(r - l):
                matrix[t][l+i], matrix[t+i][r] = matrix[t+i][r], matrix[t][l+i]
                matrix[t][l+i], matrix[b][r-i] = matrix[b][r-i], matrix[t][l+i]
                matrix[t][l+i], matrix[b-i][l] = matrix[b-i][l], matrix[t][l+i]
            l += 1
            r -= 1
            t += 1
            b -= 1
```
</panel>
