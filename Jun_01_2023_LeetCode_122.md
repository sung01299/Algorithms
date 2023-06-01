# 122. Best Time to Buy and Sell Stock II

**Difficulty: Medium**

*Related Topics: Array, Dynamic Programming, Greedy*

You are given an integer array prices where prices[i] is the price of a given stock on the ith day.

On each day, you may decide to buy and/or sell the stock. You can only hold at most one share of the stock at any time. However, you can buy it then immediately sell it on the same day.

Find and return the maximum profit you can achieve.

Example 1:

Input: prices = [7,1,5,3,6,4]
Output: 7
Explanation: Buy on day 2 (price = 1) and sell on day 3 (price = 5), profit = 5-1 = 4.
Then buy on day 4 (price = 3) and sell on day 5 (price = 6), profit = 6-3 = 3.
Total profit is 4 + 3 = 7.

Example 2:

Input: prices = [1,2,3,4,5]
Output: 4
Explanation: Buy on day 1 (price = 1) and sell on day 5 (price = 5), profit = 5-1 = 4.
Total profit is 4.

Example 3:

Input: prices = [7,6,4,3,1]
Output: 0
Explanation: There is no way to make a positive profit, so we never buy the stock to achieve the maximum profit of 0.

## Code:

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        # Dynamic Programming Solution
        dp = [0 for _ in range(len(prices))]
        
        profit = buy = sell = 0
        for i in range(len(prices)):
            if i == 1:
                profit = prices[i] - prices[buy]
                if profit >= 0:
                    dp[i] = profit
                if prices[buy] >= prices[i]:
                    buy = i
            else:
                profit = prices[i] - prices[i-1]
                if profit <= 0: profit = 0
                dp[i] = max(dp[i-1]+profit, prices[i]-prices[buy])
        return dp[-1]
        
        # Greedy Solution (Need Study)
        ans = 0
        for i in range(1, len(prices)):
            diff = prices[i] - prices[i-1]
            if diff > 0:
                ans += diff
        return ans

```
