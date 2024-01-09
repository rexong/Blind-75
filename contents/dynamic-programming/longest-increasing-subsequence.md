<frontmatter>
  title: Dynamic Programming - Longest Increasing Subsequence
</frontmatter>

# [Longest Increasing Subsequence](https://leetcode.com/problems/longest-increasing-subsequence/)

#### Difficulty: Medium

### Intuition

The recurrance relation is dp[i] = max(1, dp[i + 1], dp[i + 2]...dp[j]...dp[-1]) where we include dp[j] if and only if element i < element j

### Contraints

- $1\leqslant$ length of nums $\leqslant 2500$

## Approach

1. Initialise an empty array, dp, of size (length of nums) with 1
2. Iterate i from the last element in nums
   1. Iterate j from i + 1 to len of nums
      1. If num[i] < num[j], update dp[i] to either dp[i] or 1 + dp[j], whichever is higher
3. Return the max of dp

### Complexity

#### Time Complexity: O($n^2$)

For every element, we iterate the subarray from the element to the last element

#### Space Complexity: O(n)

For the array.

### Solution

<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def lengthOfLIS(self, nums: List[int]) -> int:
        dp = [1 for i in range(len(nums))]
        for i in range(len(nums) - 1, -1, -1):
            for j in range(i + 1, len(nums)):
                if nums[i] < nums[j]:
                    dp[i] = max(dp[i], 1 + dp[j])
        return max(dp)
```

</panel>
