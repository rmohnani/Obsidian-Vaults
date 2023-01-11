---
tags:
- leetcode
---
**Title**: 215. Kth Largest Element in an Array
**Link**: https://leetcode.com/problems/kth-largest-element-in-an-array/
**Difficulty**: #leetcode/difficulty/medium 
**Special tags**: #neetcode/area/heap_pq 
**Status**: #leetcode/status/todo 
**Time**: 

---
# Problem Statement
Given an integer array `nums` and an integer `k`, return _the_ `kth` _largest element in the array_.

Note that it is the `kth` largest element in the sorted order, not the `kth` distinct element.

You must solve it in `O(n)` time complexity.

---
# My Solution
```python
class Solution:
    def findKthLargest(self, nums: List[int], k: int) -> int:
        num_heap = nums
        heapq.heapify(num_heap)
        while len(num_heap) > k:
            heapq.heappop(num_heap)
        return num_heap[0]
        
```
notes: heapq.heapify is in-place and linear in time.
time complexity: 
space complexity: 

---
# Best Solution

notes: 
time complexity: 
space complexity: 

---

