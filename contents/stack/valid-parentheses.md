<frontmatter>
  title: Stack - Valid Parentheses
</frontmatter>

# [Valid Parentheses](https://leetcode.com/problems/valid-parentheses/)
#### Difficulty: Easy

### Intuition
Given a string of brackets, we want to match each open bracket with its corresponding close bracket.
The brackets should be in order, ie open bracket should come first before the close bracket. 
To approach this questions, we can use a **stack** data structure.

### Contraints
- There are only 3 types of brackets, `()`, `{}` and `[]`
- $1\leqslant$ Length of string $\leqslant 10^4$ 

## Approach
1. Create a map from close bracket to open bracket. 
2. Initialise an empty stack
3. Iterate through the string
    1. if the bracket is not hashed in the map (ie. open bracket), add it to the top of the stack
    2. if the bracket is hashed in the map (ie. close bracket)
        1. if the stack is not empty and the corresponding open bracket matched the top of the stack, pop the bracket of the stack
        2. else, return `False`
4. If iteration finished, check if stack is empty. Return `True` if empty else `False` 

### Complexity
#### Time Complexity: O(n)
We have to iterate through the whole string but only once. 
#### Space Complexity: O(n)
We have to allocate memory for the stack. In the worst case, all brackets in the string will be in the stack
### Solution
<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def isValid(self, s: str) -> bool:
        d = {"]" : "[", "}" : "{", ")" : "("}
        stack = []
        for bracket in s:
            if bracket not in d: #open bracket
                stack.append(bracket)
            else:
                if len(stack) != 0 and d[bracket] == stack[-1]:
                    stack.pop()
                else:
                    return False
        return len(stack) == 0
```
</panel>
