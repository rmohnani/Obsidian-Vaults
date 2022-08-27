---
tags:
- leetcode
---
**Title**: 11. Container With Most Water
**Link**: https://leetcode.com/problems/container-with-most-water/
**Difficulty**: #leetcode/difficulty/medium 
**Special tags**: #neetcode/area/two_pointers 
**Status**: #leetcode/status/completed  

---
# Problem Statement

You are given an integer array `height` of length `n`. There are `n` vertical lines drawn such that the two endpoints of the `ith` line are `(i, 0)` and `(i, height[i])`.

Find two lines that together with the x-axis form a container, such that the container contains the most water.

Return _the maximum amount of water a container can store_.

**Notice** that you may not slant the container.

---
# My Solution
```python
class Solution:
    def maxArea(self, height: List[int]) -> int:
        left = 0
        right = len(height) - 1
        
        max_vol = 0
        while left < right:
            curr_vol = min(height[left], height[right]) * (right - left)
            max_vol = max(max_vol, curr_vol)
            # print(left, right, curr_vol, max_vol)
            
            if height[left] < height[right]:
                left += 1
            
            else:
                if height[right] <= height[left]:
                    right -= 1
                
        return max_vol
        
```
notes: Pointer at beginning and end since max width. Compute vol and store it. If left pointer height less increment left pointer and similarly for right pointer but decrease. Greedy choice to take the next height. pointers meet in middle and loop ends.
time complexity: O(n)
space complexity: O(1)

---
# Best Solution
#leetcode/got_best_solution 
```python
class Solution:
    def maxArea(self, height: List[int]) -> int:
        l, r = 0, len(height) - 1
        res = 0

        while l < r:
            res = max(res, min(height[l], height[r]) * (r - l))
            if height[l] < height[r]:
                l += 1
            elif height[r] <= height[l]:
                r -= 1
        return res
```
notes: 
time complexity: 
space complexity: 

---

