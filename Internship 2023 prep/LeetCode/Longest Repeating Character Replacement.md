---
tags:
- leetcode
---
**Title**: 424. Longest Repeating Character Replacement
**Link**: https://leetcode.com/problems/longest-repeating-character-replacement/
**Difficulty**: #leetcode/difficulty/medium 
**Special tags**: #neetcode/area/sliding_window 
**Status**: #leetcode/status/completed  

---
# Problem Statement

You are given a string `s` and an integer `k`. You can choose any character of the string and change it to any other uppercase English character. You can perform this operation at most `k` times.

Return _the length of the longest substring containing the same letter you can get after performing the above operations_.

---
# My Solution
```python
class Solution:
    def characterReplacement(self, s: str, k: int) -> int:
        hash_map = dict()
        left = 0
        ans = 0
        for right in range(len(s)):
            hash_map[s[right]] = 1 + hash_map.get(s[right], 0)

            while (right - left + 1) - max(hash_map.values()) > k:
                hash_map[s[left]] -= 1
                left += 1
            ans = max(ans, right - left + 1)
        return ans
```
notes: 
time complexity: 
space complexity: 

---
# Best Solution
```python
class Solution:
    def characterReplacement(self, s: str, k: int) -> int:
        count = {}
        res = 0

        l = 0
        maxf = 0
        for r in range(len(s)):
            count[s[r]] = 1 + count.get(s[r], 0)
            maxf = max(maxf, count[s[r]])

            if (r - l + 1) - maxf > k:
                count[s[l]] -= 1
                l += 1

            res = max(res, r - l + 1)
        return res
```
notes: optimizes by using maxf and not decrementing the max count when we remove something that was the character with max count as you don't need to. so don't need to iterate over hashmap to find the new maximum value everytime.
time complexity: 
space complexity: 

---

