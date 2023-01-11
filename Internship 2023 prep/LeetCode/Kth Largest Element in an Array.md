---
tags:
- leetcode
---
**Title**: 215. Kth Largest Element in an Array
**Link**: https://leetcode.com/problems/kth-largest-element-in-an-array/
**Difficulty**: #leetcode/difficulty/medium 
**Special tags**: #neetcode/area/heap_pq 
**Status**: #leetcode/status/completed  
**Time**: 00 : 03 : 28

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
```python
# Solution: Sorting
# Time Complexity:
#   - Best Case: O(n)
#   - Average Case: O(n*log(n))
#   - Worst Case:O(n*log(n))
# Extra Space Complexity: O(n)
class Solution1:
    def findKthLargest(self, nums: List[int], k: int) -> int:
        nums.sort()
        return nums[len(nums) - k]


# Solution: QuickSelect
# Time Complexity:
#   - Best Case: O(n)
#   - Average Case: O(n)
#   - Worst Case: O(n^2)
# Extra Space Complexity: O(1)
class Solution2:
    def partition(self, nums: List[int], left: int, right: int) -> int:
        pivot, fill = nums[right], left

        for i in range(left, right):
            if nums[i] <= pivot:
                nums[fill], nums[i] = nums[i], nums[fill]
                fill += 1

        nums[fill], nums[right] = nums[right], nums[fill]

        return fill

    def findKthLargest(self, nums: List[int], k: int) -> int:
        k = len(nums) - k
        left, right = 0, len(nums) - 1

        while left < right:
            pivot = self.partition(nums, left, right)

            if pivot < k:
                left = pivot + 1
            elif pivot > k:
                right = pivot - 1
            else:
                break

        return nums[k]
```
notes: Better average case time complexity but worse worst case. 
time complexity: 
space complexity: 

---

