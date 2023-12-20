<frontmatter>
  title: Bit Manipulation - Counting Bits
</frontmatter>

# [Counting Bits](https://leetcode.com/problems/counting-bits/)
#### Difficulty: Easy

### Intuition
#### Idea 1
For every number in [0, n], find the number of ones using [Number of 1 Bits]({{ baseUrl }}/contents/bit-manipulation/number-of-1-bits.html)
#### Idea 2
Using 1D Dynamic Programming, every string of bits will only have their MSB incremented by 1 for every power of 2.
Suppose the MSB is at n, ie the number is $2^n$, for every number from $[2^n, 2^{n+1} - 1]$, the bit from n - 1 to 0 is the same as the numbers in $[0, 2^n - 1]$ <br>
As such, we can use dp to get the number of ones for every number. 

### Contraints
- $0\leqslant$ n $\leqslant 10^5$ 
 
## Approach
#### Idea 1
1. Initialise an array of length n + 1 with each element as 0
2. For every number, `i`, in [0, n]
    1. Initialise count to 0
    2. Set `j` as `i`
    3. While `j` is not 0
        1. Add the remainder of `j` divide by 2 to count
        2. Integer Divide `j` by 2
3. Return the array

#### Idea 2
1. Initialise an array of length n + 1 with each element as 0
2. Set `offset` to 1
3. For every number `i`, in [1, n]
    1. if `offset` is even, update `offset` to `i`
    2. set `array[i]` to `1 + array[i - offset]`
4. Return the array

### Complexity
#### Time Complexity: 
#### Idea 1: O(n log n) 
For every number, which has a length of n, we halve each number until it gets to 0. 

#### Idea 2: O(n)
For every number, we compute the count by using what has already been computed. Hence, no extra time required, just the O(1) lookup time for the array.

#### Space Complexity: O(n)
For either approach, only one list of size n is required to store the count, hence linear time. 

### Solution
#### Idea 1
<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def countBits(self, n: int) -> List[int]:
        ans = [0 for _ in range(n+1)]
        for i in range(n+1):
            count = 0
            j = i
            while j:
                count += j & 1
                j = j >> 1
            ans[i] = count
        return ans
```
</panel>

#### Idea 2
<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def countBits(self, n: int) -> List[int]:
        dp = [0 for _ in range(n+1)]
        offset = 1
        for i in range(1, n+1):
            if offset * 2 == i:
                offset = i
            dp[i] = 1 + dp[i - offset]
        return dp
```
</panel>
