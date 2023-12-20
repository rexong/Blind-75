<frontmatter>
  title: Arrays & Hashing - Group Anagrams
</frontmatter>

# [Group Anagrams](https://leetcode.com/problems/group-anagrams/)
#### Difficulty: Medium

### Intuition
Use an array as a count for the alphabets in the word. 

### Contraints
- Elements in the array are in lower case
- $1\leqslant$ Length of the array $\leqslant 10^4$ 
 
## Approach
1. Initialise a dictionary
2. Iterate every word in the array
    1. Initialise a count array of size 26
    2. Count the frequency of each character in the word and update the count array
    3. Append the word to the dictionary where the key is the count array
3. Return the values of the dictionary

### Complexity
#### Time Complexity: O(m * n)
`n` is the average length of a word in the array
`m` is the length of the array
#### Space Complexity: O(m)
Length of dictionary in the worse case is of size `m`<br>
For every word, we created a count array of size 26, since the size is constant, it can be ignored under big-O. But since there is an array for every word, there will be `m` arrays created. 
### Solution
<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        d = defaultdict(list)
        for word in strs:
            count = [0 for _ in range(26)]
            for char in word:
                count[ord(char) - ord('a')] += 1
            d[tuple(count)].append(word)
        return d.values()
```
</panel>
