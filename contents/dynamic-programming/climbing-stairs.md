<frontmatter>
  title: Dynamic Programming = Climbing Stairs
</frontmatter>

# [Climbing Stairs](https://leetcode.com/problems/climbing-stairs/)
#### Difficulty: Easy

### Intuition
For the `0`th and `1`th step, the number of distinct ways is 0 and 1.
Given `n`, every `i`th steps, the number of distinct ways is the sum of the previous 2 steps.

### Contraints
- $1\leqslant$ n $\leqslant 45$ 
 
## Approach
1. Initialise `prev` and `curr` to 0 and 1 respectively.
2. Iterate n times
    1. Set `temp` to `prev`
    2. Update  `prev` to `curr`
    3. Update `curr` to the sum of `curr` and temp
3. Return `curr`

### Complexity
#### Time Complexity: O(n)
We calculate each step incrementally, using information where we have computed before.
#### Space Complexity: O(1)
Only require 2 integers to store the previous values. 
### Solution
<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def climbStairs(self, n: int) -> int:
        prev, curr = 0, 1
        for i in range(n):
            temp = prev
            prev = curr
            curr = curr + temp
        return curr
```
</panel>
