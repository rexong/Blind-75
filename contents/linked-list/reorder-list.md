<frontmatter>
  title: Linked List - Reorder List 
</frontmatter>

# [Reorder List](https://leetcode.com/problems/reorder-list/)
#### Difficulty: Medium

### Intuition
1. Find the half point of the list 
    1. Use fast and slow pointer. 
    2. Fast pointer moves 2 steps, while slow pointer moves 1 step for every iteration.
2. Flip the pointers of the second half of the list.
    1. Terminate the first half of the list.  
3. Start reordering

### Contraints
- $1\leqslant$ length of list $\leqslant 5 * 10^4$ 
 
## Approach
1. Set `slow` pointer to head and `fast` pointer to `head.next`
2. While `fast` and `fast.next` is not None
    1. Move `fast` pointer twice
    2. Move `slow` pointer once
3. Initialise the second half of the list to `head2`
4. Terminate the first half of the list
5. Initialise `prev` to None
6. While `head2` is not None
    1. Flip the pointers in the second half of the list.  
7. Initialise `first` and `second` pointers to the first and second half of the list 
8. While `second` is not None (by the `fast` and `slow` pointers, the second half of the list is shorter than or equal to the first half of the list)
    1. Insert node in the second half of the list in between the first and second node in the first half of the list 

### Complexity
#### Time Complexity: O(n)
For every steps mentioned in Intuition, the run time is linear.
#### Space Complexity: O(1)
Finite and constant number of pointers are used.
### Solution
<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def reorderList(self, head: Optional[ListNode]) -> None:
        """
        Do not return anything, modify head in-place instead.
        """
        # Find the half of the list
        slow = head
        fast = head.next
        while fast and fast.next:
            fast = fast.next.next
            slow = slow.next
        # Flip the other half of the list
        head2 = slow.next
        slow.next = None
        prev = None
        while head2:
            temp = head2.next
            head2.next = prev
            prev = head2
            head2 = temp
        # Start reordering
        first, second = head, prev
        while second:
            temp1, temp2 = first.next, second.next
            first.next = second
            second.next = temp1
            first, second = temp1, temp2
```
</panel>

