---
tags:
- leetcode
---
**Title**: 90. Subsets II
**Link**: https://leetcode.com/problems/subsets-ii/
**Difficulty**: #leetcode/difficulty/medium 
**Special tags**: #neetcode/area/backtracking #leetcode/couldnt_solve 
**Status**: #leetcode/status/todo 
**Time**: 00 : 31 : 52

---
# Problem Statement
Given an integer array `nums` that may contain duplicates, return _all possible_ 

_subsets_

 _(the power set)_.

The solution set **must not** contain duplicate subsets. Return the solution in **any order**.

---
# My Solution
```python
class Solution:
    def subsetsWithDup(self, nums: List[int]) -> List[List[int]]:
        power_set = []

        subset = []
        def backtrack(i, seen):
            print(i, subset, power_set, seen)
            if i >= len(nums):
                power_set.append(subset.copy())
                return
            if nums[i] not in seen:
                seen.add(nums[i])
                # choice 1 : include
                subset.append(nums[i])
                backtrack(i + 1, seen)

                #choice 2 : exclude
                subset.pop()
                backtrack(i+1, seen)
            else:
                if nums[i] in subset:
                    subset.append(nums[i])
                    backtrack(i+1, seen)
                    subset.pop()
                    backtrack(i+1, seen)
                else:
                    backtrack(i+1, seen)
        backtrack(0, set())
        return power_set
```
notes: couldn't figure it out
time complexity: 
space complexity: 

---
# Best Solution

notes: 
time complexity: 
space complexity: 

---

