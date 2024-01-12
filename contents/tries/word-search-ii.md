<frontmatter>
  title: Tries - Word Search II 
</frontmatter>

# [Word Search II](https://leetcode.com/problems/word-search-ii/)

#### Difficulty: Difficult

### Intuition

Implement Tries and build a Tries for words. <br>
For every cell, perform DFS and compare it to the Tries built.

### Contraints

- Every character is lower case English alphabet
- $1\leqslant$ m, n $\leqslant 12$
- $1\leqslant$ Length of words $\leqslant 3 * 10^4$
- $1\leqslant$ Average length of word $\leqslant 10$

## Approach

1. Implement Tries
   1. Initialise it with children as dictionary and isWord as boolean
   2. Implement addWord
      1. Takes in a word and build the tries, when word reaches the end, set isWord to True
2. Implement findWords
   1. Initialise root as Trie
   2. For every word, build the trie by using addWord
   3. Initialise ROWS and COLS
   4. Initialise results as set
   5. Define DFS with cell coordinates, node, and word
      1. If coordinates out of range, or cell is None or cell is not in node's children, return
      2. Set char to cell
      3. Set cell to None
      4. Set node to node's children[char]
      5. Concatenate char to the back of word
      6. If node is a word, add word to results
      7. Perform DFS on all 4 adjacent cell, top, right, bottom, and left
      8. Set cell back to char
   6. For every cell, perform DFS
   7. Return results as list

### Complexity

#### Time Complexity: O($m * n * (4 * 3^{L - 1})$)

m \* n for every cell in the board. <br>
The last part is for the DFS. For the first cell, it will visit all 4 neighbours, and subsequent cell will only visit 3 neighbours, and this will occur for the remaining length of the word.

#### Space Complexity: O(N)

N is the total number of characters in all the words. This is for the number of trienode required.

### Solution

<panel header="Don't cheat yourself" type="dark">

```python
class TrieNode:
    def __init__(self):
        self.children = {}
        self.isWord = False

    def addWord(self, word):
        curr = self
        for c in word:
            if c not in curr.children:
                curr.children[c] = TrieNode()
            curr = curr.children[c]
        curr.isWord = True

class Solution:
    def findWords(self, board: List[List[str]], words: List[str]) -> List[str]:
        root = TrieNode()
        for w in words:
            root.addWord(w)

        ROWS, COLS = len(board), len(board[0])
        res = set()

        def dfs(r, c, node, word):
            if (r < 0 or c < 0 or
                r == ROWS or c == COLS or
                not board[r][c] or
                board[r][c] not in node.children):
                return

            char = board[r][c]
            board[r][c] = None
            node = node.children[char]
            word += char
            if node.isWord:
                res.add(word)

            dfs(r + 1, c, node, word)
            dfs(r - 1, c, node, word)
            dfs(r, c + 1, node, word)
            dfs(r, c - 1, node, word)
            board[r][c] = char

        for r in range(ROWS):
            for c in range(COLS):
                dfs(r, c, root, '')

        return list(res)
```

</panel>
