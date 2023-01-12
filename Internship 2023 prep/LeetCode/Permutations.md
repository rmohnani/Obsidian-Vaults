---
tags:
- leetcode
---
**Title**: 46. Permutations
**Link**: https://leetcode.com/problems/permutations/
**Difficulty**: #leetcode/difficulty/medium 
**Special tags**: #neetcode/area/backtracking #leetcode/got_best_solution 
**Status**: #leetcode/status/completed  
**Time**: 00 : 12 : 34

---
# Problem Statement
Given an array `nums` of distinct integers, return _all the possible permutations_. You can return the answer in **any order**.

---
# My Solution
```python
class Solution:
    def permute(self, nums: List[int]) -> List[List[int]]:
        permutations = []

        def backtrack(nums_i, poss):
            if nums_i >= len(nums):
                permutations.append(poss.copy())
                return 
            for j in range(len(poss) + 1):
                poss.insert(j, nums[nums_i])
                backtrack(nums_i + 1, poss)
                poss.pop(j)
        backtrack(1, [nums[0]])
        return permutations
```
notes: 
time complexity: 
space complexity: 

---
# Best Solution
```python
class Solution:
    def permute(self, nums: List[int]) -> List[List[int]]:
        res = []

        # base case
        if len(nums) == 1:
            return [nums[:]]  # nums[:] is a deep copy

        for i in range(len(nums)):
            n = nums.pop(0)
            perms = self.permute(nums)

            for perm in perms:
                perm.append(n)
            res.extend(perms)
            nums.append(n)
        return res
```
notes: 
time complexity: 
space complexity: 

---

