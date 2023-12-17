<frontmatter>
  title: Arrays & Hashing - Top K Frequent Element
</frontmatter>

# [Top K Frequent Element](https://leetcode.com/problems/top-k-frequent-element/)
#### Difficulty: Medium

### Intuition
Use bucket sort.
Have a count array, which is a list of a list. <br>
Count the frequency of each element, save it in a dictionary where the element is the key and the freq is the value.
Then for every key-value pair, append the key to the index of the value in count.

### Contraints
- $1\leqslant$ Length of array $\leqslant 10^5$ 
- There is a unique solution
 
## Approach
1. Initialise a count array of empty array with the size of the length of the input array + 1. 
2. Initialise a dictionary
3. Initialise a empty array, `results`
4. Count and update the dictionary with the frequency of every unique element
5. For every key-value pair
    1. Append the key to the count array of index value
6. Iterate count from the back, and get the first k list.

### Complexity
#### Time Complexity: O(n)

#### Space Complexity: O(n)

### Solution
<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        count = [[] for _ in range(len(nums) + 1)]
        d = defaultdict(int)
        results = []
        for num in nums:
            d[num] += 1
        for key, value in d.items():
            count[value].append(key)
        for i in range(len(count) - 1, -1 , -1):
            for num in count[i]:
                results.append(num)
                if len(results) == k:
                    return results 
```
</panel>
