---
tags:
- leetcode
---
**Title**: 20. Valid Parentheses
**Link**: https://leetcode.com/problems/valid-parentheses/
**Difficulty**: #leetcode/difficulty/easy  
**Special tags**: #neetcode/area/stack #leetcode/got_best_solution 
**Status**: #leetcode/status/completed  
**Time**:  00 : 06 : 09

---
# Problem Statement
Given a string `s` containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.

An input string is valid if:

1.  Open brackets must be closed by the same type of brackets.
2.  Open brackets must be closed in the correct order.
3.  Every close bracket has a corresponding open bracket of the same type.
---
# My Solution
```python
class Solution:
    def isValid(self, s: str) -> bool:
        stack = []
        bracks = {"(": ")", "{": "}", "[": "]"}
        for char in s:
            if char in bracks:
                stack.append(char)
            if char in bracks.values():
                if not stack or bracks[stack.pop()] != char:
                    return False
        return not stack
```
notes: 
time complexity: 
space complexity: 

---
# Best Solution
```python
class Solution:
    def isValid(self, s: str) -> bool:
        Map = {")": "(", "]": "[", "}": "{"}
        stack = []

        for c in s:
            if c not in Map:
                stack.append(c)
                continue
            if not stack or stack[-1] != Map[c]:
                return False
            stack.pop()

        return not stack
```
notes: Optimized because question says strings only consist of parens I didn't optimize for this because I thought they could have other things.
time complexity: 
space complexity: 

---

