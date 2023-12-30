<frontmatter>
  title: Dynamic Programming - Longest Palindromic Substring
</frontmatter>

# [Longest Palindromic Substring](https://leetcode.com/problems/longest-palindromic-substring/)
#### Difficulty: Medium

### Intuition
Brute Force method
- Get every substring - O($n^2$)
- For every substring, perform palindrome check - O(n)
**Time Complexity - O($n^3$)**

Optimised Method
- For every character, treat it as center of palindrome and expand while it is a palindrome
**If the palindrome is even length, take each character and the character to its right**

### Contraints 
- $1\leqslant$ Length of String $\leqslant 1000$

## Approach
1. Initialise result and length as empty string and 0 respectively
2. For every character in string
    1. Search Palindrome that has odd length
        1. Set left and right pointer to the current character index and left and right pointer's element are the same
        2. If the length between left and right pointer is more then the current length, update the current length and result
        3. Decrement left pointer and increment right pointer by 1 
    2. Search Palindrome that has even length
        1. Similar to step 2.1 but left pointer is the current character index and right pointer is the right of the current character index
3. Return result

### Complexity
#### Time Complexity: O($n^2$)
Iterate every character takes linear time, and for each search of palindrome for the character is also linear time. 
#### Space Complexity: O(1)
No additional data structure required
### Solution
<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def longestPalindrome(self, s: str) -> str:
        res = ''
        length = 0
        for i in range(len(s)):
            left, right = i, i
            while left >= 0 and right < len(s) and s[left] == s[right]:
                if (right - left + 1) > length:
                    length = right - left + 1
                    res = s[left : right + 1]
                left -= 1
                right += 1
        
            left, right = i, i+1
            while left >= 0 and right < len(s) and s[left] == s[right]:
                if (right - left + 1) > length:
                    length = right - left + 1
                    res = s[left : right + 1]
                left -= 1
                right += 1
        return res
```
</panel>

