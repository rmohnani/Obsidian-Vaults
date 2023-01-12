---
tags:
- leetcode
---
**Title**: 39. Combination Sum
**Link**: https://leetcode.com/problems/combination-sum/
**Difficulty**: #leetcode/difficulty/medium 
**Special tags**: #neetcode/area/backtracking #leetcode/couldnt_solve 
**Status**: #leetcode/status/completed  
**Time**: 00 : 31 : 17

---
# Problem Statement
Given an array of **distinct** integers `candidates` and a target integer `target`, return _a list of all **unique combinations** of_ `candidates` _where the chosen numbers sum to_ `target`_._ You may return the combinations in **any order**.

The **same** number may be chosen from `candidates` an **unlimited number of times**. Two combinations are unique if the frequency of at least one of the chosen numbers is different.

The test cases are generated such that the number of unique combinations that sum up to `target` is less than `150` combinations for the given input.

---
# My Solution
```python
class Solution:
    def combinationSum(self, candidates: List[int], target: int) -> List[List[int]]:
        combs = []

        def backtrack(i, curr_sum, subset):
            if curr_sum == target:
                combs.append(subset.copy())
                return
            if curr_sum > target or i >= len(candidates):
                return 
            subset.append(candidates[i])
            backtrack(i, curr_sum + candidates[i], subset)
            subset.pop()
            backtrack(i+1, curr_sum, subset)

        backtrack(0, 0, [])
        return combs
            
```
notes: was close but figured it out only after looking at solution. There isn't a case of adding or not adding like in the subsets question. here it is about adding the curr element or moving on to the next one. I was trying to blend these two together which wasnt working. but i was close cuz i knew i had to do 2 backtracks with i and i + 1.
time complexity: 
space complexity: 

---
# Best Solution
```python
class Solution:
    def combinationSum(self, candidates: List[int], target: int) -> List[List[int]]:
        res = []

        def dfs(i, cur, total):
            if total == target:
                res.append(cur.copy())
                return
            if i >= len(candidates) or total > target:
                return

            cur.append(candidates[i])
            dfs(i, cur, total + candidates[i])
            cur.pop()
            dfs(i + 1, cur, total)

        dfs(0, [], 0)
        return res
```
notes: 
time complexity: 
space complexity: 

---

