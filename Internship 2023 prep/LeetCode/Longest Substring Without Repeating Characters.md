---
tags:
- leetcode
---
**Title**: 3. Longest Substring Without Repeating Characters
**Link**: https://leetcode.com/problems/longest-substring-without-repeating-characters/
**Difficulty**: #leetcode/difficulty/medium  
**Special tags**: #neetcode/area/sliding_window 
**Status**: #leetcode/status/completed 
**Time**: 

---
# Problem Statement

Given a string `s`, find the length of the **longest substring** without repeating characters.

---
# My Solution
```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        if len(s) < 2:
            return len(s)
        curr_set = set()
        left = 0
        right = 1
        max_len = 0
        curr_set.add(s[left])
        while right < len(s):
            # print(curr_set)
            if s[right] in curr_set:
                curr_set.remove(s[left])
                left += 1
            else:
                curr_set.add(s[right])
                max_len = max(right - left + 1, max_len)
                right += 1
        return max_len
```
notes: 
time complexity: 
space complexity: 

---
# Best Solution
```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        curr_set = set()
        left, right, max_len = 0, 0, 0
        while right < len(s):
            while s[right] in curr_set:
                curr_set.remove(s[left])
                left += 1
            curr_set.add(s[right])
            max_len = max(max_len, right - left + 1)
            right += 1
        return max_len
```
notes: slightly better cuz it has an internal loop to move left pointer until the right pointers value is no longer inside it.
time complexity: 
space complexity: 

---



