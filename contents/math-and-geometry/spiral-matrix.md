<frontmatter>
  title: Math & Geometry - Spiral Matrix 
</frontmatter>

# [Spiral Matrix](https://leetcode.com/problems/spiral-matrix/)
#### Difficulty: Medium

### Intuition
Set left, right, top and bottom pointers. <br>
Iterate in the order,
  1. Top Left to Top Right
  2. Top Right to Bottom Right
  3. Bottom Right to Bottom Left
  4. Bottom Left to Top Left

**After step 1 and 2, need to check if pointers are still valid.**

### Contraints
- $1\leqslant$ n $\leqslant 45$ 
 
## Approach
1. Initialise an array for the results
2. Initialise the pointers to their respective corners
3. While left < right and top < bottom
    1. Append elements from top left to top right and update top
    2. Append elements from top right to bottom right and update right
    3. Check if pointers is out of range (same as step 3). If True, break the iteration
    4. Append elements from bottom right to bottom left and update bottom
    5. Append elements from bottom left to top left and update top
4. Return the array

### Complexity
#### Time Complexity: O(m * n)
Every element in the matrix will be visited once and only once.
#### Space Complexity: O(m * n)
Store the elements in the matrix to the result array
### Solution
<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def spiralOrder(self, matrix: List[List[int]]) -> List[int]:
        results = []
        l, t = 0, 0
        r, b = len(matrix[0]) - 1, len(matrix) - 1
        while l <= r and t <= b:
            for i in range(l, r + 1):
                results.append(matrix[t][i])
            t += 1
            for i in range(t, b + 1):
                results.append(matrix[i][r])
            r -= 1
            if not (l <= r and t <= b):
                break
            for i in range(r, l - 1 , -1):
                results.append(matrix[b][i])
            b -= 1
            for i in range(b, t - 1, -1):
                results.append(matrix[i][l])
            l += 1
        return results
```
</panel>

