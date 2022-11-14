---
tags:
- leetcode
---
**Title**: 121. Best Time to Buy and Sell Stock
**Link**: https://leetcode.com/problems/best-time-to-buy-and-sell-stock/
**Difficulty**: #leetcode/difficulty/easy 
**Special tags**: #neetcode/area/sliding_window
**Status**: #leetcode/status/completed 

---
# Problem Statement

You are given an array `prices` where `prices[i]` is the price of a given stock on the `ith` day.

You want to maximize your profit by choosing a **single day** to buy one stock and choosing a **different day in the future** to sell that stock.

Return _the maximum profit you can achieve from this transaction_. If you cannot achieve any profit, return `0`.

---
# My Solution
```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        if len(prices) < 2:
            return 0
        left = 0
        right = 1
        max_profit = 0
        while left < len(prices) and right < len(prices):
            curr_profit = prices[right] - prices[left]
            if curr_profit > max_profit:
                print(prices[right], prices[left])
                max_profit = curr_profit
                right += 1
            elif curr_profit < 0:
                left += 1
                right = left + 1
            else:
                if right < len(prices):
                    right += 1
                else:
                    left += 1
                    right = left + 1
            print(left, right)
        return max_profit
```
notes: 
time complexity: 
space complexity: 

---
# Best Solution
```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        left = 0
        right = 1
        max_profit = 0
        while right < len(prices):
            if prices[right] > prices[left]:
                curr_profit = prices[right] - prices[left]
                max_profit = max(max_profit, curr_profit)
            else:
                left = right
            right += 1
        return max_profit
```
notes: 
time complexity: 
space complexity: 

---

