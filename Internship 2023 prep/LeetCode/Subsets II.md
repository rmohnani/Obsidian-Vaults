---
tags:
- leetcode
---
**Title**: 90. Subsets II
**Link**: https://leetcode.com/problems/subsets-ii/
**Difficulty**: #leetcode/difficulty/medium 
**Special tags**: #neetcode/area/backtracking #leetcode/couldnt_solve 
**Status**: #leetcode/status/completed  
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
```python
class Solution:
    def subsetsWithDup(self, nums: List[int]) -> List[List[int]]:
        res = []
        nums.sort()

        def backtrack(i, subset):
            if i == len(nums):
                res.append(subset[::])
                return

            # All subsets that include nums[i]
            subset.append(nums[i])
            backtrack(i + 1, subset)
            subset.pop()
            # All subsets that don't include nums[i]
            while i + 1 < len(nums) and nums[i] == nums[i + 1]:
                i += 1
            backtrack(i + 1, subset)

        backtrack(0, [])
        return res
```
notes: key is to sort the array so that all duplicate numbers are next to each other. I understoof that when we see a duplicate of a number, we only want to add it to the subset if the subset already contains it. Because if we add it to a subset that has already seen the two (the subset fromt the branch that chose to exclude the number initialy), we are guaranteeing that if we add this number now we will create a duplicate of the initial branch when we chose to include the number. 

But I wasn't able to figure out how to keep track of which numbers had been seen and what should be done. Here since the dups are next to each other, in the case where we want to exclude all instances of the number, we simply increment i until we reach a different number.

time complexity: 
space complexity: 

---

