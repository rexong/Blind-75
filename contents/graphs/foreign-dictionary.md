<frontmatter>
  title: Graphs - Foreign Dictionary
</frontmatter>

# [Foreign Dictionary](https://neetcode.io/problems/foreign-dictionary/)

#### Difficulty: Difficult

### Intuition

Construct adjacency list for every character.<br>
Perform post order DFS, ie update result only after DFS on neighbours, on every character in the adjacency list, keep track of visited characters and characters that are on the current path. <br>

Question specific:

- If length of word[i] > length of word[j], where i < j and substring of word[i] and substring of word[j] up the the shorter length between word[i] and word[j] is the same, then it is immediately invalid.
- For every pair of words, the adjacency list of character is made up of the first letter they are different.

### Contraints

- Consists only lower case English alphabet
- $1\leqslant$ Length of words $\leqslant 100$

## Approach

1. Create an adjacency list for every character found in words, initialise every key to an empty set
2. For every index from 0 to length of words - 1
   1. Set word1 and word2 to words[i] and words[i + 1]
   2. Set minLength to the length of the shorter word, word1 or word2
   3. If length of word1 > length of word2 and substring of word1 and word2 up to minLength is the same, return empty string
   4. For every index from 0 to minLength
      1. If word1[j] not the same as word2[j], add word2[j] to adjacency list with word1[j] as key
      2. Break the iteration
   5. Initialise visited as empty dictionary
      - Note that if character in visited means it is visited, if value of character is true, it is in the current path.
   6. Initialise result as an empty array
   7. Define DFS
      1. If character in visited, return visited[character]
      2. Set visited[character] to True
      3. For every neighbour of character
         1. If DFS on neighbour is True, there is a loop, return True
      4. Set visited[character] to False
      5. Append character to result
   8. For every character in adjacency list
      1. If DFS on character is True, return empty string
   9. Reverse result
   10. Return result as a string

### Complexity

#### Time Complexity: O(n)

n is every single character in words.

#### Space Complexity: O(n)

For the adjacency list

### Solution

<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def foreignDictionary(self, words: List[str]) -> str:
        adj = {char: set() for word in words for char in word}

        for i in range(len(words) - 1):
            w1, w2 = words[i], words[i + 1]
            minLen = min(len(w1), len(w2))
            if len(w1) > len(w2) and w1[:minLen] == w2[:minLen]:
                return ""
            for j in range(minLen):
                if w1[j] != w2[j]:
                    adj[w1[j]].add(w2[j])
                    break

        visited = {}
        res = []

        def dfs(c):
            if c in visited:
                return visited[c]
            visited[c] = True

            for neighbour in adj[c]:
                # Loop detected
                if dfs(neighbour):
                    return True

            visited[c] = False
            res.append(c)

        for c in adj:
            if dfs(c):
                return ""

        res.reverse()
        return "".join(res)

```
