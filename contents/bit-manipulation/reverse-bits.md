<frontmatter>
  title: Bit Manipulation - Reverse Bits
</frontmatter>

# [Reverse Bits](https://leetcode.com/problems/reverse-bits/)
#### Difficulty: Easy

### Intuition
Initialise a number to 0 <br>
Go bit by bit from the LSB, perform **and** on LSB with 1 and append it to the number.

### Contraints
- Length of binary string is 32
 
## Approach
1. Initialise a number, `reverse`, to 0
2. Iterate 32 times
    1. Shift `reverse` bit to the left by 1
    2. Add the result of performing n & 1 to `reverse`
    3. Shift `n` bit to the right by 1
4. Return `reverse`

### Complexity
#### Time Complexity: O(1)
Only have to go through 32 bits, which is constant.
#### Space Complexity: O(1)
No additional space is required.
### Solution
<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def reverseBits(self, n: int) -> int:
        reverse = 0
        for _ in range(32):
            reverse <<= 1
            reverse += n & 1
            n >>= 1
        return reverse
```
</panel>
