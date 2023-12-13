<frontmatter>
  title: Arrays & Hashing - Contains Duplicate
</frontmatter>

# [Contains Duplicate](https://leetcode.com/problems/contains-duplicate/)
#### Difficulty: Easy

### Intuition
Since we just need to know if element is repeated, we can use a **set** to check for repetition. 

### Contraints
- $1\leqslant$ Length of array $\leqslant 10^5$ 
- $-10^9\leqslant$ element $\leqslant 10^9$ 
 
## Approach
1. Initialise a set
2. Iterate through the array
    1. if element not in set, add element to set
    2. if element in set, return `True`
3. Iteration finished, return `False`

### Complexity
#### Time Complexity: O(n)
We have to iterate through every element in the array at least once. 
#### Space Complexity: O(n)
We have to allocate memory for the set. In the worst case, every element in the array is in the set.
### Solution
<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        s = set()
        for num in nums:
            if num in s:
                return True
            s.add(num)
        return False
```
</panel>

