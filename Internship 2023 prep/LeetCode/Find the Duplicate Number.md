---
tags:
- leetcode
---
**Title**: 287. Find the Duplicate Number
**Link**: https://leetcode.com/problems/find-the-duplicate-number/
**Difficulty**: #leetcode/difficulty/medium 
**Special tags**: #neetcode/area/linked_list #leetcode/couldnt_solve 
**Status**: #leetcode/status/completed  
**Time**: 

---
# Problem Statement
Given an array of integers `nums` containing `n + 1` integers where each integer is in the range `[1, n]` inclusive.

There is only **one repeated number** in `nums`, return _this repeated number_.

You must solve the problem **without** modifying the array `nums` and uses only constant extra space.

---
# My Solution
first sol:
```python
class Solution:
    def findDuplicate(self, nums: List[int]) -> int:
        hash
        hashset = set()
        for i in range(len(nums)):
            if nums[i] in hashset:
                return nums[i]
            else:
                hashset.add(nums[i])
```

notes: 
time complexity: 
space complexity: 

---
# Best Solution
```python
class Solution:
    def findDuplicate(self, nums: List[int]) -> int:
        slow, fast = 0, 0
        while True:
            slow = nums[slow]
            fast = nums[nums[fast]]
            if slow == fast:
                break
        slow2 = 0
        while True:
            slow2 = nums[slow2]
            slow = nums[slow]
            if slow == slow2:
                break

        return slow
```
notes: 
time complexity: 
space complexity: 

---

