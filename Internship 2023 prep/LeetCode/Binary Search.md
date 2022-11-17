---
tags:
- leetcode
---
**Title**: 704. Binary Search
**Link**: https://leetcode.com/problems/binary-search/
**Difficulty**: #leetcode/difficulty/easy 
**Special tags**: #neetcode/area/binary_search #leetcode/got_best_solution 
**Status**: #leetcode/status/completed  

---
# Problem Statement
Given an array of integers `nums` which is sorted in ascending order, and an integer `target`, write a function to search `target` in `nums`. If `target` exists, then return its index. Otherwise, return `-1`.

You must write an algorithm with `O(log n)` runtime complexity.

---
# My Solution
```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        
        left, right = 0, len(nums) - 1

        while left <= right:
            middle = left + ((right - left) // 2)
            if nums[middle] > target:
                right = middle - 1
            elif nums[middle] < target:
                left = middle + 1
            else:
                return middle
        return -1
```
notes: 
time complexity: 
space complexity: 

---
# Best Solution

notes: 
time complexity: 
space complexity: 

---

