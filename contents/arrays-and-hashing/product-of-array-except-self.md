<frontmatter>
  title: Arrays & Hashing - Product of Array Except Self
</frontmatter>

# [Product of Array Except Self](https://leetcode.com/problems/product-of-array-except-self/)
#### Difficulty: Medium

### Intuition
Compute 2 arrays, prefix and postfix, <br>
where prefix is the product of array from 0 to i, <br>
and postfix is the product of array from i to n, where n is the index of the last element. 

### Contraints 
- $2\leqslant$ length of array $\leqslant 10^5$ 

## Approach
1. Initialise results, prefix and postfix array
2. Iterate and fill up the prefix and postfix array
3. Iterate the array
    1. Suppose at `i`th element, take `i-1`th element from prefix and `i+1` element from postfix
    2. Multiply and append the values to results.
4. Return results

### Complexity
#### Time Complexity: O(n)
3 Iteration, one to fill up prefix, one to fill up postfix and one to calculate the results.
#### Space Complexity: O(n)
3 additional data structure required for prefix, postfix and results.
### Solution
<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        results = [0 for _ in range(len(nums))]
        prefix = [1 for _ in range(len(nums) + 1)]
        postfix = [1 for _ in range(len(nums) + 1)]
        for i in range(1, len(prefix)):
            prefix[i] = nums[i - 1] * prefix[i - 1]
        for i in range(len(postfix) - 2, -1, -1):
            postfix[i] = nums[i] * postfix[i + 1]
        for i in range(len(nums)):
            result = prefix[i] * postfix[i + 1]
            results[i] = result
        return results
```
</panel>

