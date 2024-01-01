<frontmatter>
  title: Dynamic Programming - Palindromic Substrings
</frontmatter>

# [Palindromic Substrings](https://leetcode.com/problems/palindromic-substrings/)
#### Difficulty: Medium

### Intuition
Similar to [Longest Palindromic Substrings]({{ baseUrl }}/contents/dynamic-programming/longest-palindromic-substring.html)

### Contraints 
- $1\leqslant$ Length of String $\leqslant 1000$
- Only contains lower case alphabets

## Approach
1. Similar to Longest Palindromic Substring, replace `res` with `count`

### Complexity
#### Time Complexity: O($n^2$)
For every character, perform palindrome check. 
#### Space Complexity: O(1)
Does not require additional data structure.
### Solution
<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def countSubstrings(self, s: str) -> int:
        count = 0
        for i, char in enumerate(s):
            l, r = i, i
            while l >= 0 and r < len(s) and s[l] == s[r]:
                count += 1
                l -= 1
                r += 1

            l, r = i, i + 1
            while l >= 0 and r < len(s) and s[l] == s[r]:
                count += 1
                l -= 1
                r += 1
        return count
```
</panel>

