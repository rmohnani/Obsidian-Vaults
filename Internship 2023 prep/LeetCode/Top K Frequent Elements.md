---
tags:
- leetcode
---
**Title**: 347. Top K Frequent Elements
**Link**: https://leetcode.com/problems/top-k-frequent-elements/
**Difficulty**: #leetcode/difficulty/medium 
**Special tags**: #neetcode/area/arrays_hashing 
**Status**: #leetcode/status/completed  

---
# Problem Statement

Given an integer array `nums` and an integer `k`, return _the_ `k` _most frequent elements_. You may return the answer in **any order**.

---
# My Solution

```python
class Solution1:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        freq = {}
        for num in nums:
            freq[num] = 1 + freq.get(num, 0)
        
        output = sorted(freq.items(), key = lambda x: x[1], reverse = True)
        return [output[i][0] for i in range(k)]
```
notes:  Create a dictionary of frequencies of each num in nums list, then sorts dictionary based on frequency counts stored as values in dict in descending order, and outputs the first k corresponding keys.

time complexity: O(n) to create freq dict + O(n log n) to sort in the worst case n items in dict => O(n log n)
space complexity: O(n) for dict

---
# Best Solution

```python
class Solution: 
	def topKFrequent(self, nums: List[int], k: int) -> List[int]:
		count = {}
		freq = [[] for i in range(len(nums) + 1)] 
		for n in nums: 
			count[n] = 1 + count.get(n, 0)
		for n, c in count.items():
			freq[c].append(n)
			
		res = [] 
		for i in range(len(freq) - 1, 0, -1):
			for n in freq[i]:
				res.append(n)
				if len(res) == k:
					return res
		
		# O(n)
```
notes: Instead of sorting it just creates a list to store frequency in increasing order and reads list backwards to get the results. Smart
time complexity: O(n)
space complexity: O(n)

---

