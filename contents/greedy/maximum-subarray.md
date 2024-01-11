<frontmatter>
  title: Greedy - Maximum Subarray
</frontmatter>

# [Maximum Subarray](https://leetcode.com/problems/maximum-subarray/)

#### Difficulty: Medium

### Intuition

Since it is a subarray, we need a set that is contiguous. <br>
We can keep track of the current sum up to each element. If the current sum is negative, restart the count from the current index

### Contraints

- $1\leqslant$ length of nums $\leqslant 10^5$

## Approach

1. Initialise count and maxCount to the first element
2. For every number in nums starting from second element
   1. If count < 0, set count to number
   2. Else, set count to number + count
   3. Update maxCount to either maxCount or count, whichever is higher
3. Return maxCount

### Complexity

#### Time Complexity: O(n)

Visit each element once and only once.

#### Space Complexity: O(1)

No additional data structure required.

### Solution

<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def maxSubArray(self, nums: List[int]) -> int:
        count, maxCount = nums[0], nums[0]
        for i in range(1, len(nums)):
            if count < 0:
                count = nums[i]
            else:
                count += nums[i]
            maxCount = max(maxCount, count)
        return maxCount
```

</panel>
