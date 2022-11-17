---
tags:
- leetcode
---
**Title**: 22. Generate Parentheses
**Link**: https://leetcode.com/problems/generate-parentheses/
**Difficulty**: #leetcode/difficulty/medium 
**Special tags**: #neetcode/area/stack #leetcode/couldnt_solve 
**Status**: #leetcode/status/completed  

---
# Problem Statement
Given `n` pairs of parentheses, write a function to _generate all combinations of well-formed parentheses_.

---
# My Solution
```python
class Solution:
    def generateParenthesis(self, n: int) -> List[str]:
        ans = []
        
        def backtrack(stack = [], open_parens = 0, close_parens = 0):
            if open_parens == close_parens == n:
                ans.append("".join(stack))
                return
            
            if open_parens < n:
                stack.append("(")
                backtrack(stack, open_parens + 1, close_parens)
                stack.pop()
            
            if close_parens < open_parens:
                stack.append(")")
                backtrack(stack, open_parens, close_parens + 1)
                stack.pop()
        backtrack()
        return ans
```
notes: 
time complexity: 
space complexity: 

---
# Best Solution
```python
class Solution:
    def generateParenthesis(self, n: int) -> List[str]:
        stack = []
        res = []

        def backtrack(openN, closedN):
            if openN == closedN == n:
                res.append("".join(stack))
                return

            if openN < n:
                stack.append("(")
                backtrack(openN + 1, closedN)
                stack.pop()
            if closedN < openN:
                stack.append(")")
                backtrack(openN, closedN + 1)
                stack.pop()

        backtrack(0, 0)
        return res
```
notes: 
time complexity: 
space complexity: 

---

