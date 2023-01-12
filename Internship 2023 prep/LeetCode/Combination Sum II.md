---
tags:
- leetcode
---
**Title**: 40. Combination Sum II
**Link**: https://leetcode.com/problems/combination-sum-ii/
**Difficulty**: #leetcode/difficulty/medium 
**Special tags**: #neetcode/area/backtracking 
**Status**: #leetcode/status/completed  
**Time**: 00 : 06 : 45

---
# Problem Statement
Given a collection of candidate numbers (`candidates`) and a target number (`target`), find all unique combinations in `candidates` where the candidate numbers sum to `target`.

Each number in `candidates` may only be used **once** in the combination.

**Note:** The solution set must not contain duplicate combinations.

---
# My Solution
```python
class Solution:
    def combinationSum2(self, candidates: List[int], target: int) -> List[List[int]]:
        combs = []
        candidates.sort()

        def backtrack(i, curr_sum, subset):
            if curr_sum == target:
                combs.append(subset.copy())
                return
            if curr_sum > target or i >= len(candidates):
                return
            
            # choice 1: include nums[i]
            subset.append(candidates[i])
            backtrack(i+1, curr_sum + candidates[i], subset)
            subset.pop()

            # choice 2: exclude nums[i]
            while i + 1 < len(candidates) and candidates[i] == candidates[i+1]:
                i += 1
            backtrack(i+1, curr_sum, subset)
        
        backtrack(0, 0, [])
        return combs
```
notes: similar to subset II. Need to group the duplicates together and then have one branch always exclude the duplicate num and one branch always include. 
time complexity: 
space complexity: 

---
# Best Solution
```python
class Solution:
    def combinationSum2(self, candidates: List[int], target: int) -> List[List[int]]:
        candidates.sort()

        res = []

        def backtrack(cur, pos, target):
            if target == 0:
                res.append(cur.copy())
                return
            if target <= 0:
                return

            prev = -1
            for i in range(pos, len(candidates)):
                if candidates[i] == prev:
                    continue
                cur.append(candidates[i])
                backtrack(cur, i + 1, target - candidates[i])
                cur.pop()
                prev = candidates[i]

        backtrack([], 0, target)
        return 
```
notes: 
time complexity: 
space complexity: 

---

