---
tags:
- leetcode
---
**Title**: 973. K Closest Points to Origin
**Link**: https://leetcode.com/problems/k-closest-points-to-origin/
**Difficulty**: #leetcode/difficulty/medium 
**Special tags**: #neetcode/area/heap_pq #leetcode/got_best_solution 
**Status**: #leetcode/status/completed  
**Time**: 00 : 05 : 12

---
# Problem Statement
Given an array of `points` where `points[i] = [xi, yi]` represents a point on the **X-Y** plane and an integer `k`, return the `k` closest points to the origin `(0, 0)`.

The distance between two points on the **X-Y** plane is the Euclidean distance (i.e., `√(x1 - x2)2 + (y1 - y2)2`).

You may return the answer in **any order**. The answer is **guaranteed** to be **unique** (except for the order that it is in).

---
# My Solution
```python
class Solution:
    def kClosest(self, points: List[List[int]], k: int) -> List[List[int]]:
        points_heap = [(-(sqrt(((point[0]) ** 2) + (point[1] ** 2))), point) for point in points]
        heapq.heapify(points_heap)
        print(points_heap)
        while len(points_heap) > k:
            heapq.heappop(points_heap)
        return [point[1] for point in points_heap]
        
```
notes: 
time complexity: 
space complexity: 

---
# Best Solution
```python
class Solution:
    def kClosest(self, points: List[List[int]], k: int) -> List[List[int]]:
        pts = []
        for x, y in points:
            dist = (abs(x - 0) ** 2) + (abs(y - 0) ** 2)
            pts.append([dist, x, y])

        res = []
        heapq.heapify(pts)
        for i in range(k):
            dist, x, y = heapq.heappop(pts)
            res.append([x, y])
        return res
```
notes: stylistically different, but effectively the same.
time complexity: 
space complexity: 

---

