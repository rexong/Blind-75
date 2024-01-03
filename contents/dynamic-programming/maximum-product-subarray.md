<frontmatter>
  title: Dynamic Programming - Maximum Product Subarray
</frontmatter>

# [Maximum Product Subarray](https://leetcode.com/problems/maximum-product-subarray/)
#### Difficulty: Medium

### Intuition
For every element, keep track of the maximum and minimum product of the subarray up to the element. <br>

### Contraints 
- $0\leqslant$ length of array $\leqslant 10^4$ 

## Approach
1. Initialise result, currMax and currMin to the maximum of array, 1 and 1 respectively
2. For every number in array
    1. Set temp to currMax * current number
    2. Update currMax to temp, currMin * current number and current number
    3. Update currMin to temp, currMin * current number and current number
    4. Update the result with the currMax or result
4. Return return

### Complexity
#### Time Complexity: O(n)
Visit every element in array once and only once.
#### Space Complexity: O(1)
No additional data structure required.
### Solution
<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def maxProduct(self, nums: List[int]) -> int:
        maxProd = max(nums)
        currMin, currMax = 1, 1
        for num in nums:
            temp = currMax * num
            currMax = max(temp, currMin * num, num)
            currMin = min(temp, currMin * num, num)
            maxProd = max(maxProd, currMax)
        return maxProd
```
</panel>

