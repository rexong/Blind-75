<frontmatter>
  title: Linked List - Merge Two Sorted Lists
</frontmatter>

# [Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/)
#### Difficulty: Easy

### Intuition
Requires a **dummy node** to start.<br>
As long as there are nodes in both list, compare the nodes and add node to the list with the dummy node.<br>
Given that both lists might have different lenghts, when one list finishes, append the rest of the list to the list with the dummy node.

### Contraints
- $0\leqslant$ number of nodes $\leqslant 50$ 
- $-100\leqslant$ node's value $\leqslant 100$ 
- Both list are sorted in non-decreasing order
 
## Approach
1. Initialise a new list with a dummy node
2. Set another pointer, `curr`, to point to the new list
3. Iterate while both lists have nodes
    1. if list1 value is less than list2 value, set `curr.next` to `list1` and set `list1` to `list1.next`
    2. else, set `curr.next` to `list2` and set `list2` to `list2.next`
    3. set `curr` to `curr.next`
4. After iteration ended,
    1. if list1 is not empty, set `curr.next` to the remaining of `list1`
    2. if list2 is not empty, set `curr.next` to the remaining of `list2`
5. Return the new list but skip the dummy node

### Complexity
#### Time Complexity: O(n + m)
Suppose list1 and list2 has a length of n and m respectively, since list1 and list2 elements would be visited once and only once, the time is linear
#### Space Complexity: O(1)
Since only dummy node is newly created, where every other nodes are in place, it is constant space.
### Solution
<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def mergeTwoLists(self, list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:
        start = ListNode()
        curr = start
        while list1 and list2:
            if list1.val <= list2.val:
                curr.next = list1
                list1 = list1.next
            else:
                curr.next = list2
                list2 = list2.next
            curr = curr.next
        if not list1:
            curr.next = list2
        if not list2:
            curr.next = list1
        return start.next
```
</panel>
