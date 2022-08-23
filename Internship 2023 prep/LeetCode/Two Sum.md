---
tags:
- leetcode
---
**Title**: 1. Two Sum
**Link**: https://leetcode.com/problems/two-sum/
**Difficulty**: #leetcode/difficulty/easy 
**Special tags**: #neetcode/area/arrays_hashing 
**Status**: #leetcode/status/completed

---
# Problem Statement

Given an array of integers `nums` and an integer `target`, return _indices of the two numbers such that they add up to `target`_.

You may assume that each input would have **_exactly_ one solution**, and you may not use the _same_ element twice.

You can return the answer in any order.

---
# My Solution

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        num_dict = {}
        for i in range(len(nums)):
            if nums[i] in num_dict:
                return [num_dict[nums[i]], i]
            else:
                num_dict[target - nums[i]] = i
```

notes:  build dict with (target - curr_num) as key and index as value. If the number we're on is in the dictionary it means there was a number when added with that gives target so condition is satisfied.
time complexity: O(n)
space complexity: O(n)

---
# Best Solution
#leetcode/gotBestSolution 
```python
```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        prevMap = {}  # val -> index

        for i, n in enumerate(nums):
            diff = target - n
            if diff in prevMap:
                return [prevMap[diff], i]
            prevMap[n] = i
```

notes: same as my solution but uses enumerate instead
time complexity: 
space complexity: 

---

