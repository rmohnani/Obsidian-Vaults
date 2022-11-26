---
tags:
- leetcode
---
**Title**: 153. Find Minimum in Rotated Sorted Array
**Link**: https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/
**Difficulty**: #leetcode/difficulty/medium 
**Special tags**: #neetcode/area/binary_search #leetcode/got_best_solution 
**Status**: #leetcode/status/completed  
**Time**: 00 : 08 : 25

---
# Problem Statement
Suppose an array of length `n` sorted in ascending order is **rotated** between `1` and `n` times. For example, the array `nums = [0,1,2,4,5,6,7]` might become:

-   `[4,5,6,7,0,1,2]` if it was rotated `4` times.
-   `[0,1,2,4,5,6,7]` if it was rotated `7` times.

Notice that **rotating** an array `[a[0], a[1], a[2], ..., a[n-1]]` 1 time results in the array `[a[n-1], a[0], a[1], a[2], ..., a[n-2]]`.

Given the sorted rotated array `nums` of **unique** elements, return _the minimum element of this array_.

You must write an algorithm that runs in `O(log n) time.`

---
# My Solution
```python
class Solution:
    def findMin(self, nums: List[int]) -> int:
        left = 0
        right = len(nums) - 1
        min_num = nums[0]

        while left <= right:
            mid = (left + right) // 2
            min_num = min(min_num, nums[mid])
            
            if nums[left] <= nums[mid]:
                min_num = min(min_num, nums[left])
                left = mid + 1
            else:
                min_num = min(min_num, nums[mid])
                right = mid - 1
        return min_num
```
notes: 
time complexity: 
space complexity: 

---
# Best Solution
```python
class Solution:
    def findMin(self, nums: List[int]) -> int:
        start , end = 0 ,len(nums) - 1 
        curr_min = float("inf")
        
        while start  <  end :
            mid = (start + end ) // 2
            curr_min = min(curr_min,nums[mid])
            
            # right has the min 
            if nums[mid] > nums[end]:
                start = mid + 1
                
            # left has the  min 
            else:
                end = mid - 1 
                
        return min(curr_min,nums[start])
```
notes: 
time complexity: 
space complexity: 

---

