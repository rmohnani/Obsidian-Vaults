---
tags:
- leetcode
---
**Title**: 242. Valid Anagram
**Link**: https://leetcode.com/problems/valid-anagram/
**Difficulty**: #leetcode/difficulty/easy 
**Special tags**: #neetcode/area/arrays_hashing  
**Status**: #leetcode/status/completed 

---
# Problem Statement
Given two strings `s` and `t`, return `true` _if_ `t` _is an anagram of_ `s`_, and_ `false` _otherwise_.

An **Anagram** is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

---
# My Solution

```python
class Solution1:
    def isAnagram(self, s: str, t: str) -> bool:
        if len(s) != len(t):
            return False
        s_dict = {}
        t_dict = {}
        for i in range(len(s)):
            s_dict[s[i]] = 1 + s_dict.get(s[i], 0)
            t_dict[t[i]] = 1 + t_dict.get(t[i], 0)
        
        return s_dict == t_dict
```

notes: create 2 dictionaries and compare for equality
time complexity: O(s)
space complexity: O(s + t)

```python
class Solution2:
    def isAnagram(self, s: str, t: str) -> bool:
        s_dict = {}
        for char in s:
            if char not in s_dict:
                s_dict[char] = 1
            else:
                s_dict[char] += 1

        for char in t:
            if char not in s_dict:
                return False
            else:
                if s_dict[char] <= 0:
                    return False
                else:
                    s_dict[char] -= 1
        
        for char in s_dict:
            if s_dict[char] != 0:
                return False
        return True
```

notes: create 1 dictionary for s and modifies it based on t
time complexity: O(s + t)
space complexity: O(s)

---
# Best Solution
#leetcode/got_best_solution 
notes: 
time complexity: 
space complexity: 

---

