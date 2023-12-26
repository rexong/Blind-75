<frontmatter>
  title: Arrays & Hashing - Longest Consecutive Sequence
</frontmatter>

# [Longest Consecutive Sequence](https://leetcode.com/problems/longest-consecutive-sequence/)
#### Difficulty: Medium

### Intuition
For the start of any sequence, it would not have a left neighbour.<br>
Hence, we only start counting the length of a sequence if it does not have a left neighbour.<br>
In order to check if there is a left neighbour or to check if the next number in the sequence exists, we need to use a set, utilising its constant look up time.

### Contraints
- $0\leqslant$ length of array $\leqslant 10^5$ 
 
## Approach
1. Initialise an empty set 
2. Initialise result to 0
3. Put every element in the array into the set 
4. Iterate every element in array
    1. Initialise count to 0
    2. If there exist a left neighbour, ie element - 1 is in set, skip this iteration
    3. Else, while the element is in set,
        1. Increment count by 1 
        2. Increment the element by 1 
    4. Set the result to either itself or the current calculated sequence, whichever is larger
5. Return result

### Complexity
#### Time Complexity: O(n)
Every element is accessed twice in the array. <br>
Once to add everything into the set. <br>
Once to calculate the length of sequence. <br>
Any other lookup is in the set, which has constant runtime. 
#### Space Complexity: O(n)
The length of the set.
### Solution
<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def longestConsecutive(self, nums: List[int]) -> int
        s = set()
        result = 0
        for num in nums:
            s.add(num)
        for num in nums:
            count = 0
            if num - 1 in s:
                continue
            while num in s:
                count += 1 
                num += 1 
            result = max(result, count)
        return result
```
</panel>

