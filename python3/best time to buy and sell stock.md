# Best Time to Buy and Sell Stock

#### Problem Link: https://leetcode.com/problems/best-time-to-buy-and-sell-stock/

## Approach 1 [Not Accepted]

### Solution:
* 

```py
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        profit =  0
        max = 0
        for i in range(len(prices)):
            for j in range(i+1, len(prices)):
                if prices[j]> prices[i] and (prices[j]-prices[i])>max:
                    max = prices[j] - prices[i]
                    profit = max
        return profit
```

### Time Complexity:

### Space Complexity:
<br>

## Approach 2 

### Solution:

```py
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        l = 0
        r = 1
        max_profit = 0
        while r < len(prices):
            current_profit = prices[r] - prices[l]
            if prices[l] < prices[r]:
                max_profit = max(max_profit, current_profit)
            else:
                l = r
            r += 1
        return max_profit
```

### Time Complexity:

### Space Complexity: