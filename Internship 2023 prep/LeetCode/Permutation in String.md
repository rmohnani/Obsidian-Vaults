---
tags:
- leetcode
---
**Title**: 567. Permutation in String
**Link**: https://leetcode.com/problems/permutation-in-string/
**Difficulty**: #leetcode/difficulty/medium  
**Special tags**: #neetcode/area/sliding_window 
**Status**: #leetcode/status/completed  
**Time**: 17 m 39 s

---
# Problem Statement

Given two strings `s1` and `s2`, return `true` _if_ `s2` _contains a permutation of_ `s1`_, or_ `false` _otherwise_.

In other words, return `true` if one of `s1`'s permutations is the substring of `s2`.

---
# My Solution
```python
class Solution:
    def checkInclusion(self, s1: str, s2: str) -> bool:
        s1_hash = dict()
        for char in s1:
            s1_hash[char] = 1 + s1_hash.get(char, 0)
        
        left = 0
        right = 0
        curr_hash = s1_hash.copy()
        while right < len(s2):
            # print(curr_hash, left, right)
            if s2[right] not in curr_hash:
                if s2[left] in s1_hash:
                    curr_hash[s2[left]] = 1 + curr_hash.get(s2[left], 0)
                    left += 1
                else:
                    right += 1
                    left = right 
                    curr_hash = s1_hash.copy()

            else:
                curr_hash[s2[right]] -= 1
                if curr_hash[s2[right]] == 0:
                    curr_hash.pop(s2[right])
                if not curr_hash:
                    return True
                right += 1
        return False
```
notes: 
time complexity: 
space complexity: 

---
# Best Solution

notes: 
time complexity: 
space complexity: 

---

