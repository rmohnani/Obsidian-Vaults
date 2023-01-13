---
tags:
- leetcode
---
**Title**: 17. Letter Combinations of a Phone Number
**Link**: https://leetcode.com/problems/letter-combinations-of-a-phone-number/
**Difficulty**: #leetcode/difficulty/medium 
**Special tags**: #neetcode/area/backtracking #leetcode/got_best_solution 
**Status**: #leetcode/status/completed  
**Time**: 00 : 07 : 44

---
# Problem Statement
Given a string containing digits from `2-9` inclusive, return all possible letter combinations that the number could represent. Return the answer in **any order**.

A mapping of digits to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.

---
# My Solution
```python
class Solution:
    def letterCombinations(self, digits: str) -> List[str]:
        res = []
        if len(digits) == 0:
            return res
            
        digitmap = {'2': "abc", '3': "def", '4': "ghi", '5':"jkl", '6': "mno", '7': "pqrs", '8': "tuv", '9': "wxyz"}

        curr_comb = ""
        def backtrack(i, curr_comb):
            if i >= len(digits):
                res.append(curr_comb)
                return
            
            poss_letters = digitmap[digits[i]]
            for j in range(len(poss_letters)):
                curr_comb += poss_letters[j]
                backtrack(i + 1, curr_comb)
                curr_comb = curr_comb[:-1]
        backtrack(0, curr_comb)
        return res
```
notes: 
time complexity: 
space complexity: 

---
# Best Solution
```python
class Solution:
    def letterCombinations(self, digits: str) -> List[str]:
        res = []
        digitToChar = {
            "2": "abc",
            "3": "def",
            "4": "ghi",
            "5": "jkl",
            "6": "mno",
            "7": "qprs",
            "8": "tuv",
            "9": "wxyz",
        }

        def backtrack(i, curStr):
            if len(curStr) == len(digits):
                res.append(curStr)
                return
            for c in digitToChar[digits[i]]:
                backtrack(i + 1, curStr + c)

        if digits:
            backtrack(0, "")

        return res
```
notes: just better style. logically the same.
time complexity: 
space complexity: 

---

