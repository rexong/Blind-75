<frontmatter>
  title: Sliding Window - Best Time To Buy And Sell Stock
</frontmatter>

# [Best Time To Buy And Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)
#### Difficulty: Easy

### Intuition
Since we can only move forward with time and not backwards, sliding window would be a ideal solution. 
Sliding window can be done with 1 pointer. 

### Contraints
- $1\leqslant$ Length of array $\leqslant 10^5$ 
- $0\leqslant$ price $\leqslant 10^4$ 
 
## Approach
1. Initialise profit to 0
2. Initialise a buy pointer to the first index
3. Iterate through the prices starting with the second index
    1. if buy > price, set buy to price
    2. else, take the max between profit and the difference between price and buy
4. Return profit

### Complexity
#### Time Complexity: O(n)
Every element in the array has to be accessed once and only once, hence linear time.
#### Space Complexity: O(1)
No extra data structure introduced. Only need to keep track of the profit. Hence constant space.
### Solution
<panel header="Don't cheat yourself" type="dark">

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        profit = 0
        buy = prices[0]
        for price in prices[1:]:
            if buy > price:
                buy = price
            else:
                profit = max(profit, price - buy)
        return profit
```
</panel>
