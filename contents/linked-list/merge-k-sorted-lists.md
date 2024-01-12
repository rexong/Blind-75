<frontmatter>
  title: Linked List - Merge K Sorted Lists
</frontmatter>

# [Merge K Sorted Lists](https://leetcode.com/problems/merge-k-sorted-lists/)

#### Difficulty: Difficult

### Intuition

Can make use of [Merge Two Sorted Lists]({{ baseUrl }}/contents/linked-list/merge-two-sorted-lists.html). For every list in lists, use merge two sorted lists starting with an empty list. <br>

To optimise the time complexity, we can take reference to how merge sort does its combination. Merging pair by pair at every level.

### Contraints

- $0\leqslant$ K $\leqslant 10^4$
- Every list in lists are sorted

## Approach

1. If lists is empty, return None
2. While len(lists) > 1
   1. Initialise mergedLists to empty list
   2. For every pair of list in lists
      1. Initialise list1 to the first list of the pair
      2. Initialise list2 to the second list of the pair or empty list, if second list is out of bound
      3. Merge list1 and list2
      4. Add the merge list to mergedLists
   3. Update lists to mergedLists
3. Return the first element in lists

### Complexity

#### Time Complexity: O(n logk)

n is the total number of nodes, k is the length of lists. <br>
log k occurs when we apply merge sort concept to the solution, every time we merge, we half the number of lists to merge in the next iteration.

#### Space Complexity: O(1)

No additional data structure required.

### Solution

<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def mergeKLists(self, lists: List[Optional[ListNode]]) -> Optional[ListNode]:
        if not len(lists):
            return None

        def mergeTwoLists(list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:
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

        while len(lists) > 1:
            mergedLists = []
            for i in range(0, len(lists), 2):
                list1 = lists[i]
                list2 = lists[i + 1] if i + 1 < len(lists) else None
                mergedLists.append(mergeTwoLists(list1, list2))
            lists = mergedLists

        return lists[0]
```

</panel>
