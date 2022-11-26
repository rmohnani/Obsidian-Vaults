---
tags:
- leetcode
---
**Title**: 33. Search in Rotated Sorted Array
**Link**: https://leetcode.com/problems/search-in-rotated-sorted-array/
**Difficulty**: #leetcode/difficulty/medium 
**Special tags**: #neetcode/area/binary_search #leetcode/got_best_solution 
**Status**: #leetcode/status/completed  

---
# Problem Statement
There is an integer array `nums` sorted in ascending order (with **distinct** values).

Prior to being passed to your function, `nums` is **possibly rotated** at an unknown pivot index `k` (`1 <= k < nums.length`) such that the resulting array is `[nums[k], nums[k+1], ..., nums[n-1], nums[0], nums[1], ..., nums[k-1]]` (**0-indexed**). For example, `[0,1,2,4,5,6,7]` might be rotated at pivot index `3` and become `[4,5,6,7,0,1,2]`.

Given the array `nums` **after** the possible rotation and an integer `target`, return _the index of_ `target` _if it is in_ `nums`_, or_ `-1` _if it is not in_ `nums`.

You must write an algorithm with `O(log n)` runtime complexity.

---
# My Solution
```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        left = 0
        right = len(nums) - 1

        while left <= right:
            # print(left, right)
            middle = (left + right) // 2
            if nums[middle] == target:
                return middle
            elif nums[middle] < nums[left]:
                if nums[left] <= target or target < nums[middle]:
                    right = middle - 1
                else:
                    left = middle + 1
            elif nums[right] < nums[middle]:
                if nums[right] >= target or nums[middle] < target:
                    left = middle + 1
                else:
                    right = middle - 1
            else:
                if target < nums[middle]:
                    right = middle - 1
                else:
                    left = middle + 1
        return -1
```
notes: 
time complexity: 
space complexity: 

---
# Best Solution
```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        l, r = 0, len(nums) - 1

        while l <= r:
            mid = (l + r) // 2
            if target == nums[mid]:
                return mid

            # left sorted portion
            if nums[l] <= nums[mid]:
                if target > nums[mid] or target < nums[l]:
                    l = mid + 1
                else:
                    r = mid - 1
            # right sorted portion
            else:
                if target < nums[mid] or target > nums[r]:
                    r = mid - 1
                else:
                    l = mid + 1
        return -1
```
notes: cleaner but mine also worked
time complexity: 
space complexity: 

---

