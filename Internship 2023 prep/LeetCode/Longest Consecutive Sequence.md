---
tags:
- leetcode
---
**Title**: 128. Longest Consecutive Sequence
**Link**: https://leetcode.com/problems/longest-consecutive-sequence/
**Difficulty**: #leetcode/difficulty/medium 
**Special tags**: #neetcode/area/arrays_hashing 
**Status**: #leetcode/status/completed 

---
# Problem Statement

Given an unsorted array of integers `nums`, return _the length of the longest consecutive elements sequence._

You must write an algorithm that runs in `O(n)` time.

---
# My Solution
#leetcode/couldnt_solve 
This is stupid

notes: 
time complexity: 
space complexity: 

---
# Best Solution
```python
class Solution:
	def longestConsecutive(self, nums: List[int]) -> int:
		numSet = set(nums)
		longest = 0
		for n in nums: 
		# check if its the start of a sequence
			if (n - 1) not in numSet:
				length = 1
				while (n + length) in numSet:
					length += 1
				longest = max(length, longest)
		return longest
```
notes: Creates a set of the nums. Looks for a starting num with no previous then simply checks if the next num is in set and so on then store the max.
time complexity: O(n)
space complexity: O(n) because of the set

---

