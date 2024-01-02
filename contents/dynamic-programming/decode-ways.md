<frontmatter>
  title: Dynamic Programming - Decode Ways
</frontmatter>

# [Decode Ways](https://leetcode.com/problems/decode-ways/)
#### Difficulty: Medium

### Intuition
Start from the back, and use DP to solve each subproblem, where the subproblem is the number of ways to to group the string. Need to take note of how the value `0` is handled.

### Contraints
- $0\leqslant$ length of string $\leqslant 100$ 
- String may start with `0`s.

## Approach
1. Initialise array of (length of string + 1) to memoise subproblems
2. Set the last element of array to 1 
3. Iterate every index starting from the back
    1. If the element of the index is 0, set the array of index to 0
    2. Else, set the array of index to array of index+1 
    3. If index+1 is still in bound and string of index to index + 1 is between 10 and 26, increment the array of index to array of index+2 
4. Return first element of array

### Complexity
#### Time Complexity: O(n)
Iterating through every element once.
#### Space Complexity: O(n)
Required for the array. 

<box type="info" header="##### Special Tips">
  <md>
    Space complexity can be optimised to O(1). Since only dp[i+1] and dp[i+2] is required.
  </md> 
</box>

### Solution
<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def numDecodings(self, s: str) -> int:
        dp = [0 for _ in range(len(s) + 1)]
        dp[len(s)] = 1
        for i in range(len(s) - 1, -1, -1):
            if s[i] == "0":
                dp[i] = 0
            else:
                dp[i] = dp[i + 1]
            if (i + 1 < len(s) and (s[i] == '1' or (s[i] == '2' and s[i+1] in "0123456"))):
                dp[i] += dp[i + 2]
        return dp[0]
```
</panel>

