<frontmatter>
  title: Dynamic Programming - Coin Change
</frontmatter>

# [Coin Change](https://leetcode.com/problems/coin-change/)
#### Difficulty: Medium

### Intuition
Bottom Up DP approach. Memoise the fewest coin change for every dollar from 0 to amount.

### Contraints  
- $0\leqslant$ length of coins $\leqslant 12$ 
- $0\leqslant$ amount $\leqslant 10^4$ 

## Approach
1. Initialise dp array of length `amount`. Each element is the maximum number of coin change + 1 
    - _Maximum number is the case where every coin is 1_
2. Set the first element in array to 0
3. Iterate every integer `a` from 0 to `amount`
    1. Iterate every coin `c`
        1. If `a - c` is greater than or equal to 0, update array at index `a` to the minimum between the element at index `a` or 1 + element at index `a - c`
4. Return the last element in the array, but return -1 if the last element is maximum number of coin change + 1 

### Complexity
#### Time Complexity: O(amount * n)
n is the length of coins. 
#### Space Complexity: O(amount)
Require an array to memoise repeated recurrance. 
### Solution
<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def coinChange(self, coins: List[int], amount: int) -> int:
        dp = [amount + 1 for _ in range(amount + 1)]
        dp[0] = 0
        for a in range(amount + 1):
            for c in coins:
                if a - c >= 0:
                    dp[a] = min(dp[a], 1 + dp[a - c])
        return dp[amount] if dp[amount] != amount + 1 else -1
```
</panel>

