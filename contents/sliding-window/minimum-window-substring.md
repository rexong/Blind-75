<frontmatter>
  title: Sliding Window - Minimum Window Substring
</frontmatter>

# [Minimum Window Substring](https://leetcode.com/problems/minimum-window-substring/)

#### Difficulty: Difficult

### Intuition

Use sliding window on s, extend the window until the substring contains t. <br>
Then shorten the window until just after the substring does not contains t.

### Contraints

- $1\leqslant$ Length of s and t $\leqslant 10^5$

## Approach

1. Initialise tD and sD as empty dictionaries
2. Update tD with t
3. Initialise have and need to 0 and length of tD
4. Initialise prev and curr as 0
5. Initialise minWindow to a tuple (0, length of s - 1)
6. Initialise substringExist to False
7. While curr < length of s
   1. Set char to s[curr]
   2. Increment sD[char] by 1
   3. If char in tD and sD[char] == tD[char], increment have by 1
   4. While have == need
      1. Set substringExist to True
      2. If current Window's length < minWindow's length, update minWindow
      3. Decrement sD[s[prev]] by 1
      4. If s[prev] in tD and sD[s[prev]] < tD[s[prev]], decrement have by 1
      5. Increment prev by 1
   5. Increment curr by 1
8. Return the substring with minWindow or empty string if substring does not exist

### Complexity

#### Time Complexity: O(n)

With the have and need variables, the lookup time would be O(1). <br>
Hence the heavy lifting would be on string s. Every character in s would be visited linearly.

#### Space Complexity: O(m)

The space required for tD and sD, which is the length of t.

### Solution

<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def minWindow(self, s: str, t: str) -> str:
        tD, sD = defaultdict(int), defaultdict(int)
        for char in t:
            tD[char] += 1

        have, need = 0, len(tD)
        prev, curr = 0, 0
        minWindow = (0, len(s) - 1)
        substringExist = False

        while curr < len(s):
            char = s[curr]
            sD[char] += 1
            if char in tD and sD[char] == tD[char]:
                have += 1
            while have == need:
                substringExist = True
                if curr - prev + 1 < minWindow[1] - minWindow[0] + 1:
                    minWindow = (prev, curr)
                sD[s[prev]] -= 1
                if s[prev] in tD and sD[s[prev]] < tD[s[prev]]:
                    have -= 1
                prev += 1
            curr += 1
        return s[minWindow[0] : minWindow[1] + 1] if substringExist else ""
```

</panel>
