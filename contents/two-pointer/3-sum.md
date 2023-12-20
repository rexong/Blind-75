<frontmatter>
  title: Two Pointer - 3Sum
</frontmatter>

# [3Sum](https://leetcode.com/problems/3sum/)
#### Difficulty: Medium

### Intuition
Sort the list.
For every number in the list, use [two sum]({{ baseUrl }}/contents/arrays-and-hashing/two-sum.html) on the remaining array with the number as the target. Since the array is sorted, two sum can be done in linear time, by setting the start pointer to the left of the number and end pointer to the end of the list. Suppose the sum of start pointer and end pointer is less than the target, shift left pointer. Else, shift right pointer. 

### Contraints
- $3\leqslant$ Length of array $\leqslant 3000$ 
 
## Approach
1. Initialise an empty list to record the results
2. Sort the array
3. Iterate through all the numbers
    1. If i > 0 and the current number is the same as the previous number, skip this iteration
    2. Initialise left pointer to the number to the right and right pointer to the end of the list.
    3. While the left pointer is less than the right pointer,
        1. Create the result array with the current number, number pointed by left and right pointer
        2. Sum the result created
        3. If the sum > 0, decrement right by 1
        4. If the sum < 0, increment left by 1
        5. if sum = 0, append the result array to results and shift the left pointer to the next unique number in the list. 
4. Return results

### Complexity
#### Time Complexity: O($n^2$)
Sort takes $nlogn$ time, but computation of 3Sum has run time of $n^2$<br>
For every element, we scan the remaining length of the array, hence qudratic time. 
#### Space Complexity: O(n)
Data structure required for the results array. 
### Solution
<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def threeSum(self, nums: List[int]) -> List[List[int]]:
        results = []
        nums.sort()

        for i, value in enumerate(nums):
            if i > 0 and value == nums[i - 1]:
                continue
            left, right = i + 1, len(nums) - 1
            while left < right:
                result = [value, nums[left], nums[right]]
                threeSum = sum(result)
                if threeSum > 0:
                    right -= 1
                elif threeSum < 0:
                    left += 1
                else:
                    results.append(result)
                    left += 1
                    while nums[left] == nums[left - 1] and left < right:
                        left += 1
        return results
```
</panel>
