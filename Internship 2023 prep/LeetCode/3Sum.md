---
tags:
- leetcode
---
**Title**: 15. 3Sum
**Link**: https://leetcode.com/problems/3sum/
**Difficulty**: #leetcode/difficulty/medium 
**Special tags**: #neetcode/area/two_pointers 
**Status**: #leetcode/status/completed  

---
# Problem Statement

Given an integer array nums, return all the triplets `[nums[i], nums[j], nums[k]]` such that `i != j`, `i != k`, and `j != k`, and `nums[i] + nums[j] + nums[k] == 0`.

Notice that the solution set must not contain duplicate triplets.

---
# My Solution
#leetcode/couldnt_solve 
```python
class Solution:
    def threeSum(self, nums: List[int]) -> List[List[int]]:
        result = set()
        target_sum = 0
        
        for i in range(len(nums)):
            curr_target = target_sum - nums[i]
            dic = {}
            for j in range(len(nums)):
                if j != i:
                    if nums[j] not in dic:
                        dic[curr_target - nums[j]] = nums[j]
                    else:
                        ans = sorted([nums[i], dic[nums[j]], nums[j]])
                        result.add(tuple(ans))
        return result
                
```
notes: Too slow. Also has a bandaid way to solve duplicate problem
time complexity: 
space complexity: 

---
# Best Solution
```python
class Solution:
    def threeSum(self, nums: List[int]) -> List[List[int]]:
        res = []
        nums.sort()

        for i, a in enumerate(nums):
            if i > 0 and a == nums[i - 1]:
                continue

            l, r = i + 1, len(nums) - 1
            while l < r:
                threeSum = a + nums[l] + nums[r]
                if threeSum > 0:
                    r -= 1
                elif threeSum < 0:
                    l += 1
                else:
                    res.append([a, nums[l], nums[r]])
                    l += 1
                    while nums[l] == nums[l - 1] and l < r:
                        l += 1
        return res
```
notes: Sort the numbers first. Then fix the first number and do two sum, skip the next number if its the same as the previous one. Since sorted this avoid duplicates. 
time complexity: O(n^2) because doing two sum for each  num and sorting is O(n log n)
space complexity: O(1) if you dont count the result array

---

