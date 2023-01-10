---
tags:
- leetcode
---
**Title**: 703. Kth Largest Element in a Stream
**Link**: https://leetcode.com/problems/kth-largest-element-in-a-stream/
**Difficulty**: #leetcode/difficulty/easy 
**Special tags**: #neetcode/area/heap_pq #leetcode/couldnt_solve 
**Status**: #leetcode/status/completed  
**Time**: 

---
# Problem Statement
Design a class to find the `kth` largest element in a stream. Note that it is the `kth` largest element in the sorted order, not the `kth` distinct element.

Implement `KthLargest` class:

-   `KthLargest(int k, int[] nums)` Initializes the object with the integer `k` and the stream of integers `nums`.
-   `int add(int val)` Appends the integer `val` to the stream and returns the element representing the `kth` largest element in the stream.

---
# My Solution

notes: 
time complexity: 
space complexity: 

---
# Best Solution
```python
import heapq
class KthLargest:

    def __init__(self, k: int, nums: List[int]):
        self.minheap = nums
        heapq.heapify(self.minheap)
        self.k = k
        while len(self.minheap) > k:
            heapq.heappop(self.minheap)

    def add(self, val: int) -> int:
        heapq.heappush(self.minheap, val)
        if len(self.minheap) > self.k:
            heapq.heappop(self.minheap)
        return self.minheap[0]

        


# Your KthLargest object will be instantiated and called as such:
# obj = KthLargest(k, nums)
# param_1 = obj.add(val)
```
notes: 
time complexity: 
space complexity: 

---

