<frontmatter>
  title: Arrays & Hashing - String Encode and Decode
</frontmatter>

# [String Encode and Decode](https://neetcode.io/problems/string-encode-and-decode/)

#### Difficulty: Medium

### Intuition

Encode is simple, it is decode that is more challenging. <br>
To decode, if we just use a special character as delimiter, it will not work as the special character could be in the list of strings as well. <br>
To find this, we add a number in front of the delimiter, specifing the length of word to read.

### Contraints

- $0\leqslant$ length of string $\leqslant 100$
- Characters are elements in UTF-8 characters.

## Approach

### Encode

1. Initialise result to an empty string
2. For every string in strs
   1. Concatenate the lenght of the string, "#", and string to result
3. Return result

### Decode

1. Initialise result to an empty list
2. Initialise i to 0 and nextWordLength to 0
3. While i < length of string
   1. Set j to i
   2. Increment j until it reaches the first "#"
   3. Read the length of the word from i to j
   4. Append the word to result
   5. Update i to the index after the word
4. Return result

### Complexity

#### Time Complexity: O(n)

n is the number of string in strings

#### Space Complexity: O(1)

No additional data structure required.

### Solution

<panel header="Don't cheat yourself" type="dark">

```python
class Solution:

    def encode(self, strs: List[str]) -> str:
        res = ''
        for word in strs:
            res += str(len(word)) + '#' + word
        return res

    def decode(self, s: str) -> List[str]:
        res = []
        i = 0
        nextWordLen = 0
        while i < len(s):
            j = i
            while s[j] != '#':
                j += 1
            wordLength = int(s[i: j])
            res.append(s[j + 1: j + 1 + wordLength])
            i = j + 1 + wordLength
        return res
```

</panel>
