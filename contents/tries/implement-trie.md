<frontmatter>
  title: Tries - Implement Trie (Prefix Tree)
</frontmatter>

# [Implement Trie (Prefix Tree)](https://leetcode.com/problems/implement-trie-prefix-tree/)
#### Difficulty: Medium

### Intuition
Just implement trie, can be done using fix length array or dictionary. <br>
Need to indicate where a word ends.  

### Contraints
- $1\leqslant$ length of word/prefix $\leqslant 2000$

## Approach
#### __ init __ method
1. Initialise end to false 
2. Initialise array to a fix length of 26

#### Insert method
1. Set curr to point to the start of trie
2. For every character in word
    1. Find the character index in the array
    2. If the index in the array is None, initialise a trie at that index
    3. Set curr to the trie of the array's index
3. Set curr's end to True

#### Search method
1. Set curr to point to the start of trie
2. For every character in word
    1. Find the character index in the array
    2. If the index in the array is None, return False
    3. Set curr to the trie of the array's index
3. Return curr's end

#### StartsWith method
1. Set curr to point to the start of trie
2. For every character in word
    1. Find the character index in the array
    2. If the index in the array is None, return False
    3. Set curr to the trie of the array's index
3. Return True

### Complexity
#### Time Complexity: O(n)
n is the length of word/prefix
#### Space Complexity: O(n)
n is the length of word/prefix
### Solution
<panel header="Don't cheat yourself" type="dark">

```python
class Trie:

    def __init__(self):
        self.end = False
        self.array = [None for i in range(26)]
        
    def insert(self, word: str) -> None:
        curr = self
        for char in word:
            i = ord(char) - ord('a')
            if not curr.array[i]:
                curr.array[i] = Trie()
            curr = curr.array[i]
        curr.end = True
        

    def search(self, word: str) -> bool:
        curr = self
        for char in word:
            i = ord(char) - ord('a')
            if not curr.array[i]:
                return False
            curr = curr.array[i]
        return curr.end

    def startsWith(self, prefix: str) -> bool:
        curr = self
        for char in prefix:
            i = ord(char) - ord('a')
            if not curr.array[i]:
                return False
            curr = curr.array[i]
        return True
```
</panel>

