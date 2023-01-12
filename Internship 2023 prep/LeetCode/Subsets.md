---
tags:
- leetcode
---
**Title**: 78. Subsets
**Link**: https://leetcode.com/problems/subsets/
**Difficulty**: #leetcode/difficulty/medium 
**Special tags**: #neetcode/area/backtracking 
**Status**: #leetcode/status/completed  
**Time**: 00 : 07 : 51

---
# Problem Statement
Given an integer array `nums` of **unique** elements, return _all possible_ 
_subsets_ _(the power set)_.

The solution set **must not** contain duplicate subsets. Return the solution in **any order**.

---
# My Solution
```python
class Solution:
    def subsets(self, nums: List[int]) -> List[List[int]]:
        power_set = [[]]
        for i in range(len(nums)):
            # print(i, nums[i])
            for j in range(len(power_set)):
                # print(j, power_set)
                new_subset = power_set[j].copy()
                new_subset.append(nums[i])
                # print(new_subset)
                power_set.append(new_subset)
        return power_set
```

successfully able to implement backtracking version after seeing sol
```python
class Solution:
    def subsets(self, nums: List[int]) -> List[List[int]]:
        power_set = []

        subset = []
        def backtrack(i):
            if i >= len(nums):
                # need to make copy so that new list created
                power_set.append(subset.copy())
                return None
            
            # choice 1: add element to subset
            subset.append(nums[i])
            backtrack(i + 1)

            # choice 2: remove added element (backtrack element addition) and do another backtrack
            subset.pop()
            backtrack(i + 1)

        backtrack(0)
        return power_set
```
notes: This was not a backtracking solution.
time complexity: 
space complexity: 

---
# Best Solution
```python
class Solution:
    def subsets(self, nums: List[int]) -> List[List[int]]:
        res = []

        subset = []

        def dfs(i):
            if i >= len(nums):
                res.append(subset.copy())
                return
            # decision to include nums[i]
            subset.append(nums[i])
            dfs(i + 1)
            # decision NOT to include nums[i]
            subset.pop()
            dfs(i + 1)

        dfs(0)
        return res
```
notes: This is a backtracking solution. At each step in the dfs we choose to either add or not add the element in the nums list to the subset. at the end we will have made 8 different dfs calls and return 8 unique subsets which we then add to the result powerset.
time complexity: 
space complexity: 

---

