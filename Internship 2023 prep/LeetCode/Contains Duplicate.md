---
tags:
- leetcode
---
**Title**: 217. Contains Duplicate
**Link**: https://leetcode.com/problems/contains-duplicate/
**Difficulty**: #leetcode/difficulty/easy 
**Special tags**: #neetcode/area/arrays_hashing
**Status**: #leetcode/status/completed 

---
# Problem Statement

Given an integer array `nums`, return `true` if any value appears **at least twice** in the array, and return `false` if every element is distinct.

---
# My Solution

```python
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        hashset = set()
        for num in nums:
            if num in hashset:
                return True
			hashset.add(num)
        return False
```

notes: needed to reference [set methods](https://www.w3schools.com/python/python_ref_set.asp)
time complexity: O(n)
	- for loop goes over every element in list once
space complexity: O(n)
	- hashset can potentially contain all elements in list if distinct

---
# Best Solution

#leetcode/gotBestSolution

notes: 
time complexity: 
space complexity:

---
