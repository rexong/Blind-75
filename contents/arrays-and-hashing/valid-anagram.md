<frontmatter>
  title: Arrays & Hashing - Valid Anagram
</frontmatter>

# [Valid Anagram](https://leetcode.com/problems/valid-anagram/)
#### Difficulty: Easy 

### Intuition
Given string `s`, **map** every character to its count.
<br>
Given string `t`, for each character, decrement the count in the map by 1.

<box type="info" header="##### Special Tips">
  <md>
    Python provides `defaultdict` which is a dictionary that would not raise a KeyError.
    It should be initialised with a function that returns the default value when the key is not found.
  </md> 

  ```python
  # creates dictionary that will set value to 0 if key not found
  int_dict = defaultdict(int)

  # creates dictionary that will set value to "Not Present" if key not found
  not_present_dict = defaultdict(lambda: "Not Present")  
  ```
</box>

### Contraints
- Strings are all in lowercase
- $1\leqslant$ Length of string $\leqslant 5 * 10^4$ 
 
## Approach
1. Initialise a dictionary
2. Iterate through the first string, increment value by 1
3. Iterate through the second string
    1. if character not in dictionary, return `False`
    2. if character in dictionary, decrement value by 1
        1. if value is 0, remove the key from the dictionary
4. Check if dictionary is empty, if empty return `True` else return `False`

### Complexity
#### Time Complexity: O(n+m)
Suppose length of first string is n, the first iteration will be O(n).
<br>
Suppose length of second string is m, the second iteration will be O(m).
<br>
Removing and updating the dictionary is in O(1) time. 
<br>
Hence, time complexity is O(n+m).

#### Space Complexity: O(n)
Since we only add the first string's characters into the dictionary, we only require `n` number of spaces in the worst case.
### Solution
<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        d = {}
        for char in s:
            d[char] = d.get(char, 0) + 1
        for char in t:
            if char in d:
                d[char] = d[char] - 1
                if d[char] == 0:
                    d.pop(char)
            else:
                return False
        return len(d) == 0
```
</panel>

