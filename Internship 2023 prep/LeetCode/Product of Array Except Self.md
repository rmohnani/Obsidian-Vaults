---
tags:
- leetcode
---
**Title**: 238. Product of Array Except Self
**Link**: https://leetcode.com/problems/product-of-array-except-self/
**Difficulty**: #leetcode/difficulty/medium 
**Special tags**: #neetcode/area/arrays_hashing  
**Status**: #leetcode/status/completed 

---
# Problem Statement

Given an integer array `nums`, return _an array_ `answer` _such that_ `answer[i]` _is equal to the product of all the elements of_ `nums` _except_ `nums[i]`.

The product of any prefix or suffix of `nums` is **guaranteed** to fit in a **32-bit** integer.

You must write an algorithm that runs in `O(n)` time and without using the division operation.

---
# My Solution

seems like some bit operation bullshit
turns out it wasn't
#leetcode/couldnt_solve


notes: 
time complexity: 
space complexity: 

---
# Best Solution

```python
class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        answer = [1] * len(nums)
        
        prefix = 1
        for i in range(len(nums)):
            answer[i] = prefix
            prefix *= nums[i]
            
        postfix = 1
        for j in range(len(nums) - 1, -1, -1):
            answer[j] *= postfix
            postfix *= nums[j]
        
        return answer
```

notes: Compute product of all numbers before ith position and store it in ith position of answer array looping from beginning. Then compute the product of all numbers after ith position and multiply ith position value by the post product looping from end to beginning.
time complexity: O(n) because two for loops over length of array
space complexity: O(1) because answer array not included

---

