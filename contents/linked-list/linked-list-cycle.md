<frontmatter>
  title: Linked List - Linked List Cycle
</frontmatter>

# [Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/)
#### Difficulty: Easy

### Intuition
Use 2 pointer, one fast pointer and one slow pointer.
<br>
If there is a cycle the fast pointer will eventually catch up to the slow pointer. 

### Contraints
- $0\leqslant$ number of nodes $\leqslant 10^4$ 
 
## Approach
1. If the first node or the second node is null, return `True`
2. Initialise the fast pointer to the second node and the slow pointer to the first node.
3. Initialise count to 1
4. Iterate repeatedly while there exist a fast pointer
    1. if the fast pointer points to the same memory location as the slow pointer, return `True`
    2. Move the fast pointer to the next.
    3. Increment the count by 1
    4. if count is divisible by 2, move slow pointer to the next. (so that fast pointer is always 2 steps ahead of slow)
5. If the iteration ended, return `False`

### Complexity
#### Time Complexity: O(n)
All node will be be traversed to. <br>
If there is no cycle, it will traverse only once.<br>
If there exist a cycle, it will traverse the list k times, where k is the number of loops it takes for fast pointer to meet the slow pointer. Since k is a constant term, it is subsume by big-O.
#### Space Complexity: O(1)
Only require 2 pointers and no other additional data sturcture. Hence, constant space. 
### Solution
<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def hasCycle(self, head: Optional[ListNode]) -> bool:
        if not head or not head.next:
            return False
        count = 1
        fast = head.next
        slow = head
        while fast:
            if fast == slow:
                return True
            fast = fast.next
            count += 1
            if count % 2 == 0:
                slow = slow.next
        return False
```
</panel>
