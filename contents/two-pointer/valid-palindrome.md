<frontmatter>
  title: Two Pointer - Valid Palindrome 
</frontmatter>

# [Valid Palindrome](https://leetcode.com/problems/valid-palindrome/)
#### Difficulty: Easy

### Intuition
Have two pointer, one at the start, one at the end.
<br>
Compare both pointers' characters.  

### Contraints
- $1\leqslant$ Length of string $\leqslant 2 * 10^5$ 
- The string can contain any ASCII characters. 
 
## Approach
1. Convert the string to lower case. 
2. Initialise 2 pointer, 1 for the first element (start), 1 for the last element (end).
3. Iterate while start > end
    1. While start pointer's character is not alphanumeric, increment start pointer
    2. While end pointer's character is not alphanumeric, decrement end pointer
    3. If start and end pointers' character is not the same, return `False`
    4. If start and end pointers' character is the same, increment start and decrement end pointer
4. If finish iteration, return `True`

### Complexity
#### Time Complexity: O(n)
Since all characters in the string has to be checked, it will be of linear time. 
#### Space Complexity: O(1)
No extra data structure is required. Only need 2 pointer, hence constant space. 
### Solution
<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def isPalindrome(self, s: str) -> bool:
        s = s.lower()
        start = 0
        end = len(s) - 1
        while start <= end:
            if not s[start].isalnum():
                start += 1
                continue
            if not s[end].isalnum():
                end -= 1
                continue
            if s[start] != s[end]:
                return False
            start += 1
            end -= 1
        return True
```
</panel>
