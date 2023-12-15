<frontmatter>
  title: Bit Manipulation - Missing Number
</frontmatter>

# [Missing Number](https://leetcode.com/problems/missing-number/)
#### Difficulty: Easy

### Intuition
#### Idea 1
Sum of 0 to n - Sum of all elements in the array

#### Idea 2
xor every element in the array<br>
xor every number from 0 to n <br>
xor the results

### Contraints
- $1\leqslant$ n $\leqslant 10^4$
 
## Approach
#### Idea 1
1. Initialise 2 variable, one for sum of n, one for sum of array. Set both to 0
2. Sum up the values from 0 to n
3. Sum up the values in the array
4. Return the difference of 2 sums

#### Idea 2
1. Initialise 2 variable, one for xor of n, one for xor of array. Set both to 0
2. XOR the values from 0 to n
3. XOR the values in the array
4. Return the XOR of the 2 results

### Complexity
#### Time Complexity: O(n)
Iterate from 0 to n once for both situation. <br>
Then iterate the array once for both situation, where the length of array is n - 1. <br>
Hence, linear time.
#### Space Complexity: O(1)
No additional memory allocation required beside initialising 2 variables. 
### Solution
#### Idea 1
<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def missingNumber(self, nums: List[int]) -> int:
        total = 0
        arrayTotal = 0
        for i in range(len(nums)):
            arrayTotal += nums[i]
            total += i
        total += len(nums)
        return total - arrayTotal
```
</panel>

#### Idea 2
<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def missingNumber(self, nums: List[int]) -> int:
        xornum = 0
        xortotal = 0
        for num in nums:
            xornum ^= num
        for i in range(len(nums)+1):
            xortotal ^= i
        return xortotal ^ xornum
```
</panel>
