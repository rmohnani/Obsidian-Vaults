---
tags:
- leetcode
---
**Title**: 875. Koko Eating Bananas
**Link**: https://leetcode.com/problems/koko-eating-bananas/
**Difficulty**: #leetcode/difficulty/medium 
**Special tags**: #neetcode/area/binary_search #leetcode/couldnt_solve 
**Status**: #leetcode/status/completed  

---
# Problem Statement
Koko loves to eat bananas. There are `n` piles of bananas, the `ith` pile has `piles[i]` bananas. The guards have gone and will come back in `h` hours.

Koko can decide her bananas-per-hour eating speed of `k`. Each hour, she chooses some pile of bananas and eats `k` bananas from that pile. If the pile has less than `k` bananas, she eats all of them instead and will not eat any more bananas during this hour.

Koko likes to eat slowly but still wants to finish eating all the bananas before the guards return.

Return _the minimum integer_ `k` _such that she can eat all the bananas within_ `h` _hours_.

---
# My Solution
```python
class Solution:
    def minEatingSpeed(self, piles: List[int], h: int) -> int:
        left = 1
        right = max(piles)
        best_k = right
        
        while left <= right:
            curr_k = (left + right) // 2
            curr_hours = 0
            
            for pile in piles:
                curr_hours += ceil(pile / curr_k)
                
            if curr_hours <= h:
                right = curr_k - 1
                best_k = min(best_k, curr_k)
            else:
                left = curr_k + 1
        return best_k
                
```
notes: 
time complexity: 
space complexity: 

---
# Best Solution
```python
class Solution:
    def minEatingSpeed(self, piles: List[int], h: int) -> int:
        l, r = 1, max(piles)
        res = max(piles)

        while l <= r:
            k = (l + r) // 2

            totalTime = 0
            for p in piles:
                totalTime += math.ceil(p / k)
            if totalTime <= h:
                res = min(res, k)
                r = k - 1
            else:
                l = k + 1
        return res
```
notes: 
time complexity: 
space complexity: 

---

