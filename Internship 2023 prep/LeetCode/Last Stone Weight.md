---
tags:
- leetcode
---
**Title**: 1046. Last Stone Weight
**Link**: https://leetcode.com/problems/last-stone-weight/
**Difficulty**: #leetcode/difficulty/easy 
**Special tags**: #neetcode/area/heap_pq #leetcode/got_best_solution 
**Status**: #leetcode/status/completed  
**Time**: 00 : 10 : 25

---
# Problem Statement
You are given an array of integers `stones` where `stones[i]` is the weight of the `ith` stone.

We are playing a game with the stones. On each turn, we choose the **heaviest two stones** and smash them together. Suppose the heaviest two stones have weights `x` and `y` with `x <= y`. The result of this smash is:

-   If `x == y`, both stones are destroyed, and
-   If `x != y`, the stone of weight `x` is destroyed, and the stone of weight `y` has new weight `y - x`.

At the end of the game, there is **at most one** stone left.

Return _the weight of the last remaining stone_. If there are no stones left, return `0`.

---
# My Solution
```python
class Solution:
    def lastStoneWeight(self, stones: List[int]) -> int:
        stone_heap = [-x for x in stones]
        heapq.heapify(stone_heap)
        while len(stone_heap) > 1:
            y = heapq.heappop(stone_heap)
            x = heapq.heappop(stone_heap)
            if x != y:
                heapq.heappush(stone_heap, y - x)
                
        if stone_heap:
            return -stone_heap[0]
        else:
            return 0
```
notes: 
time complexity: 
space complexity: 

---
# Best Solution
```python
class Solution:
    def lastStoneWeight(self, stones: List[int]) -> int:
        stones = [-s for s in stones]
        heapq.heapify(stones)

        while len(stones) > 1:
            first = heapq.heappop(stones)
            second = heapq.heappop(stones)
            if second > first:
                heapq.heappush(stones, first - second)

        stones.append(0)
        return abs(stones[0])
```
notes: better handling of two cases whether len is 0 or 1, by adding 0 to list so list will always have at least one element and if len 0, we add 0 and get 0, and if len 1 we add 0 and get back the element that was already there regardless
time complexity: 
space complexity: 

---

