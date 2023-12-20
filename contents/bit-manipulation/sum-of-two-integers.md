<frontmatter>
  title: Bit Manipulation - Sum of Two Integers
</frontmatter>

# [Sum of Two Integers](https://leetcode.com/problems/sum-of-two-integers/)
#### Difficulty: Medium

### Intuition
Use xor to add without carry.
To handle carry, and both a and b and shift it to the right.

### Contraints
- $-1000\leqslant$ a, b $\leqslant 1000$ 
 
## Approach
1. While b 
    1. Set a to the xor of a and b and b to the and of a and b shift right.
2. Return a

### Complexity
#### Time Complexity: O(1)
Manipulating bits which is of length 32
#### Space Complexity: O(1)
No additional data structure required.

<box type="info" header="##### Special Tips">
  <md>
    Use Java instead of python for this case.<br>
    Python integer is not 32bit. It is dynamic and will update to higher bits if required. <br>
    Use Java will allow for only 32 bits if `int` is used. <br>
    This is required to handle negative numbers.
  </md> 
</box>

### Solution
<panel header="Don't cheat yourself" type="dark">

```java
class Solution {
    public int getSum(int a, int b) {
        while (b != 0) {
            int temp = (a & b) << 1;
            a = a ^ b;
            b = temp;
        }
        return a;
    }
}
```
</panel>

