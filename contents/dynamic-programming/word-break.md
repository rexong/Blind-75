<frontmatter>
  title: Dynamic Programming - Word Break
</frontmatter>

# [Word Break](https://leetcode.com/problems/word-break/)

#### Difficulty: Medium

### Intuition

We work from the last character with a pointer. <br>
For every word in wordDict, we check if the pointer until the length of the word matches the word.

### Contraints

- $1\leqslant$ length of string $\leqslant 300$
- $1\leqslant$ length of wordDict $\leqslant 1000$
- Only consists of lower case English
- Every element in wordDict is unique

## Approach

1. Initialise a DP array of size (length of s + 1) with False
2. Set the last element to True
3. Iterate starting from the last character
   1. For every word in wordDict
      1. If i + length of word is in range and the substring from i to i + length of word matches the word, update DP of i to DP of i + length of word
      2. If DP of i is True, end the iteration
4. Return the first element in DP

### Complexity

#### Time Complexity: O(n \* m)

n and m is the length of s and wordDict respectively.

#### Space Complexity: O(s)

For the array

### Solution

<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def wordBreak(self, s: str, wordDict: List[str]) -> bool:
        dp = [False for _ in range(len(s) + 1)]
        dp[len(s)] = True

        for i in range(len(s) - 1, -1, -1):
            for word in wordDict:
                if i + len(word) <= len(s) and s[i : i + len(word)] == word:
                    dp[i] = dp[i + len(word)]
                if dp[i]:
                    break
        return dp[0]

```

</panel>
