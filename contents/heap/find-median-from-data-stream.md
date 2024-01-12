<frontmatter>
  title: Heap - Find Median from Data Stream
</frontmatter>

# [Find Median from Data Stream](https://leetcode.com/problems/find-median-from-data-stream/)

#### Difficulty: Difficult

### Intuition

Use 2 heap, maxheap and minheap.
Need to ensure this few things 1. Always add to maxHeap first 2. If max of maxHeap is more than min of minHeap, pop max of maxHeap and add into minHeap 3. If difference between heaps' length is more than 1, balance the heaps.

<box type="info" header="##### Special Tips">
  <md>
    Some notes about heap in python. <br>
        1. Heap in python are only implemented as maxHeap. Hence to get minHeap, negate the number.<br>
        2. Push and pop heap takes log n time.
        3. In python, heap is declared as empty list, any operation using heap should be done through the class `heapq`
  </md>

```python
def someFunction():
  array = []
  heapq.heappush(array, 1) # add 1 to heap
  heapq.heappush(array, 2) # add 2 to heap
  print(array[0])          # peek at the max of heap, in this case 2
  heapq.heappop(array)     # remove max from heap, in this case 2
```

</box>
### Contraints

- $-10^5\leqslant$ num $\leqslant 10^5$
- $0 \leqslant$ Number of calls on MedianFinder $\leqslant 10^5$

## Approach

1. Implement MedianFinder init
   1. Set small and large to empty list
2. Implement addNum
   1. Push num to small
   2. If max of small > min of large and both list are not empty, pop max of small and push to large
   3. If length of small - length of large > 1, pop max of small and push to large
   4. If length of large - length of small > 1, pop min of large and push to small
3. Implement findMedian
   1. If length of small > length of large, return max of small
   2. If length of large > length of small, return min of large
   3. Return half of (max of small + min of large)

### Complexity

#### Time Complexity:

##### addNum - O(log n)

Any heap operation for pop and push takes log n.

##### findMedian - O(1)

Peeking at max and min of heap take constant time.

#### Space Complexity: O(n)

n is the length of small and large array.

### Solution

<panel header="Don't cheat yourself" type="dark">

```python
class MedianFinder:

    def __init__(self):
        self.small, self.large = [], []

    def addNum(self, num: int) -> None:
        heapq.heappush(self.small, -1 * num)

        if self.small and self.large and -1 * self.small[0] > self.large[0]:
            val = -1 * heapq.heappop(self.small)
            heapq.heappush(self.large, val)

        if len(self.small) - len(self.large) > 1:
            val = -1 * heapq.heappop(self.small)
            heapq.heappush(self.large, val)

        if len(self.large) - len(self.small) > 1:
            val = heapq.heappop(self.large)
            heapq.heappush(self.small, -1 * val)

    def findMedian(self) -> float:
        if len(self.small) > len(self.large):
            return -1 * self.small[0]
        if len(self.large) > len(self.small):
            return self.large[0]
        return (-1 * self.small[0] + self.large[0]) / 2
```

</panel>
