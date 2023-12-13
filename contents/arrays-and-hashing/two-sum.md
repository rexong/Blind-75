<frontmatter>
  title: Array & Hashing - Two Sum 
</frontmatter>

# [Two Sum](https://leetcode.com/problems/two-sum/)
#### Difficulty: Easy 

### Intuition
For every number in the array, subtract it from the target.
<br>
Use the remainder and search a set to see if the remainder exist.
<br>
If it does not exist, add it to the set. 

### Contraints
- There exist a unique solution
- Same number cannot be used twice
- $2\leqslant$ length of array $\leqslant 10^4$ 
- $-10^9\leqslant$ number $\leqslant 10^9$ 
 
## Approach
1. Initialise a dictionary that maps the number to its index
2. Iterate through the array
    1. Get the remainder by subtracting target and the element
    2. If remainder is in dictionary, return element's index and remainder's value
    3. If remainder is not in dictionary, add `element : index` to dictionary

### Complexity
#### Time Complexity: O(n)
Every element in the array has to be examined once and only once.
#### Space Complexity: O(n)
Memory is required for the dictionary. In the wose case, the dictionary will contain all element and their index mapping. 
### Solution
<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        d = {}
        for i in range(len(nums)):
            other_num = target - nums[i]
            if other_num in d:
                return [i, d[other_num]]
            d[nums[i]] = i
```
</panel>
