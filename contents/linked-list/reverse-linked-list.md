<frontmatter>
  title: Linked List - Reverse Linked List
</frontmatter>

# [Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/)
#### Difficulty: Easy

### Intuition
Start another new list.
For every node in the original list, flip the next pointer of every node to the new list. 

### Contraints
- $0\leqslant$ number of nodes $\leqslant 5000$  
 
## Approach
1. If the list is null or there is only one node in the list, return the same list. 
2. Initialise a null pointer, `newList`
3. Iterate through the list
    1. Set temp pointer to head
    2. Set head to the next node in the list
    3. Set the next node of temp to `newList`
    4. Set `newList` to temp
4. Return temp

### Complexity
#### Time Complexity: O(n)
Every node in the list needs its pointers to be flip. Every node will be accessed once and only once. Hence, linear time.
#### Space Complexity: O(1)
No extra data sturcture is required, hence constant space.
### Solution
<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        if not head or not head.next:
            return head
        newList = None
        while head:
            temp = head
            head = head.next
            temp.next = newList
            newList = temp
        return temp
```
</panel>
