<frontmatter>
  title: Linked List - Remove Nth Node from End of List 
</frontmatter>

# [Remove Nth Node from End of List](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)
#### Difficulty: Medium

### Intuition
Need to use a dummy node. <br>
In addition, we set the left and right pointers and make sure the left and right pointers distance is of `n`. <br>
Then move the left and right pointers until right pointer reaches the end of the list. 

### Contraints
- $1\leqslant$ length of list $\leqslant 30$
- $1\leqslant$ n $\leqslant length of list$
 
## Approach
1. Initialise a dummy node, pointing to head
2. Initialise left pointer to dummy and right pointer to head
3. While n
    1. Shift right pointer to the next node
    2. Decrement n by 1 
4. While right pointer is not None
    1. Shift left pointer and right pointer to their respective next node
5. Set the next node of left pointer to the next, next node of left pointer
6. Return the next node of dummy

### Complexity
#### Time Complexity: O(n)
The right pointer will visit each node once and only once. 
#### Space Complexity: O(1)
Only require one extra dummy node
### Solution
<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def removeNthFromEnd(self, head: Optional[ListNode], n: int) -> Optional[ListNode]:
        dummy = ListNode(0, head)
        l = dummy
        r = head
        while n:
            r = r.next
            n -= 1
        while r:
            l = l.next
            r = r.next
        l.next = l.next.next
        return dummy.next
```
</panel>

