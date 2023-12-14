<frontmatter>
  title: Bit Manipulation - Number of 1 Bits 
</frontmatter>

# [Number of 1 Bits](https://leetcode.com/problems/number-of-1-bits/)
#### Difficulty: Easy

### Intuition
This question is also known as _Hamming Weight_.<br>
Find the remainder by dividing by 2.
Then add up all the remainder

### Contraints
- The input is a binary string of length 32
 
## Approach
1. Initialise count to 0
2. Iterate while the input is not 0
    1. **And** the input with 1 and add it to count
    2. Shift the input bit to the right by 1 bit.
3. Return count

<box type="info" header="##### Special Tips">
  <md>
    The code snippet shows 2 equivalent operation of finding remainder of 2 and integer division by 2.<br>
    The operation is equivalent in the sense that they both yield the same result.<br>
    However, manipulating integer by its bit is more efficient in terms of computation.
  </md>

  ```python
  def example(n: int):
    n1 = n
    n2 = n
    
    # Mod 2 is equivalent to and operation with 1
    remainder1 = n1 % 2
    reminder2 = n2 & 1

    # Integer division is equivalent to shift 1 bit to right 
    n1 = n1 // 2
    n2 = n2 >> 1
  ```
</box>

### Complexity
#### Time Complexity: O(log(n)) or O(1)
Both are acceptable.
log(n) is the number of time the input could be halved.
Constant time as there is at most 32 bit to shift, which is constant.
#### Space Complexity: O(1)
No extra memory allocation is required, hence constant space.
### Solution
<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def hammingWeight(self, n: int) -> int:
        count = 0
        while n:
            count += n&1
            n = n >> 1
        return count
```
</panel>

### Going the Extra Mile
We can shorten the time even further by using the formula `n & (n-1)`. <br>
Using this formula, we are removing 1 bit from n every single time. <br>
For every iteration, increment count and perform the formula on n until n reaches 0.<br>
This formula can prevents the unnecessary bit shifts.

_This algorithm is slightly more efficient, but is still in constant time_