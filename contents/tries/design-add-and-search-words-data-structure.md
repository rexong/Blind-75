<frontmatter>
  title: Tries - Design Add and Search Words Data Structure
</frontmatter>

# [Design Add and Search Words Data Structure](https://leetcode.com/problems/design-add-and-search-words-data-structure/)
#### Difficulty: Medium

### Intuition
Implement using trie.

### Contraints
- $1\leqslant$ length of word $\leqslant 25$
- Only lower case alphabet and full stop
- At most 2 full stops in a word

## Approach
1. Create a Node class with end word and a empty dictionary as attributes
2. Initialise a node in the __ init __ method
3. Define addWord method
    1. Similar to insert method in [Implement Trie]({{ baseUrl }}/contents/tries/implement-trie.html)
4. Define searchWord method
    1. Similar to search method in [Implement Trie]({{ baseUrl }}/contents/tries/implement-trie.html)
    2. For the wildcard, `.`, can handle using dfs, every time there is a `.`, perform dfs on the current node's dictionary's value.

### Complexity
#### Time Complexity: O(n)
n is the length of the word
#### Space Complexity: O(1)
No additional data structure is required
### Solution
<panel header="Don't cheat yourself" type="dark">

```python
class Node:
    def __init__(self):
        self.end = False
        self.d = {}

class WordDictionary:

    def __init__(self):
        self.node = Node()

    def addWord(self, word: str) -> None:
        curr = self.node
        for char in word:
            if char not in curr.d:
                curr.d[char] = Node()
            curr = curr.d[char]
        curr.end = True

    def search(self, word: str) -> bool:
        curr = self.node
        for i, char in enumerate(word):
            if char == '.':
                for key in curr.d.keys():
                    newWord = word[:i] + key + word[i + 1: ]
                    if self.search(newWord):
                        return True
            if char not in curr.d:
                return False
            curr = curr.d[char]
        return curr.end
        
```
</panel>

