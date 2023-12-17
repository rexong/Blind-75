<frontmatter>
  title: Sliding Window - Longest Repeating Character Replacement
</frontmatter>

# [Longest Repeating Character Replacement](https://leetcode.com/problems/longest-repeating-character-replacement/)
#### Difficulty: Medium

### Intuition
Keep a dictionary that counts the frequency of alphabet in the sliding window. <br>
If the difference between length of the window and the maximum frequency of alphabet is less than or equal to k, expand the window from the right. <br>
Else, shorten the window from the left, and update the frequency of the dictionary accordingly.

### Contraints
- $1\leqslant$ Length of string $\leqslant 10^5$ 
 
## Approach
1. Initialise a count dictionary
2. Initialise left pointer and result to 0
3. Iterate every character in the string
    1. Increment the character's frequency in count
    2. While the difference between the length of the window and the max frequency in count > k
        1. Decrement the left pointer's character frequency in count
        2. Increment left pointer by 1
4. Return result

### Complexity
#### Time Complexity: O(n)
Each pointers will visit each element once and only once. 
#### Space Complexity: O(n)
Required for the dictionary
### Solution
<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def characterReplacement(self, s: str, k: int) -> int:
        count = defaultdict(int)
        l, result = 0, 0
        for r in range(len(s)):
            count[s[r]] += 1
            while (r - l + 1) - max(count.values()) > k:
                count[s[l]] -= 1
                l += 1
            result = max(r - l + 1, result)
        return result
```
</panel>
