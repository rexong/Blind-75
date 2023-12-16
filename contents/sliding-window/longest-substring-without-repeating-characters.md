<frontmatter>
  title: Sliding Window - Longest Substring without Repeating Characters
</frontmatter>

# [Longest Substring without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/)
#### Difficulty: Medium

### Intuition
Use two pointer, `curr` and `prev` and initialise a set. <br>
If `curr` points to a new character, add it to the set and move `curr` forward. <br>
If `curr` points to a repeated character, remove the character `prev` points to until the repeated character is not in the set. 

### Contraints
- The string can contain any ASCII characters
- $0\leqslant$ length of string $\leqslant 5 * 10^4$
 
## Approach
1. Initialise a set
2. Initialise maximum length, `curr` and `prev` to 0
3. Iterate while `curr` less than length of string
    1. If the character pointed by `curr` is not in set
        1. Add the character to set
        2. Calculate the distance between the 2 pointers, take the maximum of this distance and the current maximum length
        3. Increment `curr` by 1
    2. If the character is in set
        1. while the character is in the set
            1. Remove the character that `prev` points to
            2. Increment `prev` by 1
4. Return the maximum length

### Complexity
#### Time Complexity: O(n)
In the worse case, both pointers will visit each element once and only once.
#### Space Complexity: O(n)
A set is required. In the worse case, every character in the string will be an element in the set. 
### Solution
<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        include = set()
        maxLength = 0
        curr = 0
        prev = 0
        while curr < len(s):
            if s[curr] not in include:
                include.add(s[curr])
                maxLength = max(maxLength, curr - prev + 1)
                curr += 1
            else: 
                while s[curr] in include:
                    include.remove(s[prev])
                    prev += 1
        return maxLength
```
</panel>
