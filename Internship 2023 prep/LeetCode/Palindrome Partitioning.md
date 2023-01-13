---
tags:
- leetcode
---
**Title**: 131. Palindrome Partitioning
**Link**: https://leetcode.com/problems/palindrome-partitioning/
**Difficulty**: #leetcode/difficulty/medium 
**Special tags**: #neetcode/area/backtracking #leetcode/got_best_solution 
**Status**: #leetcode/status/completed  
**Time**: 00 : 15 : 29

---
# Problem Statement
Given a string `s`, partition `s` such that every substring of the partition is a  **palindrome**. Return _all possible palindrome partitioning of_ `s`.

---
# My Solution
```python
class Solution:
    def is_palindrome(self, s: str) -> bool:
        l = 0
        r = len(s) - 1
        while l < r:
            if s[l] != s[r]:
                return False
            l += 1
            r -= 1
        return True

    def is_all_palindrome(self, partition: List[str]) -> bool:
        for item in partition:
            if not self.is_palindrome(item):
                return False
        return True

    def partition(self, s: str) -> List[List[str]]:
        parts = []

        curr_part = [s[0]]
        def backtrack(i, curr_part):
            print(i, curr_part)
            if i >= len(s):
                if self.is_all_palindrome(curr_part):
                    parts.append(curr_part.copy())
                return
            
            # parition before curr_letter
            curr_part.append(s[i])
            backtrack(i+1, curr_part)


            # parititon after curr_letter
            curr_part.pop()
            curr_part[-1] += s[i]
            backtrack(i+1, curr_part)
            curr_part[-1] = curr_part[-1][:-1]
        backtrack(1,curr_part)
        return parts    
```
notes: Kind of a cheat. Just found all partitions and checked if each is palindrome and if so added it to solution set. Oherwise discarded partition. Must be a way to build only the palindromic partitions. 
time complexity: 
space complexity: 

---
# Best Solution
```python
class Solution:
    def partition(self, s: str) -> List[List[str]]:
        res, part = [], []

        def dfs(i):
            if i >= len(s):
                res.append(part.copy())
                return
            for j in range(i, len(s)):
                if self.isPali(s, i, j):
                    part.append(s[i : j + 1])
                    dfs(j + 1)
                    part.pop()

        dfs(0)
        return res

    def isPali(self, s, l, r):
        while l < r:
            if s[l] != s[r]:
                return False
            l, r = l + 1, r - 1
        return True
```
notes: This is better because for each character we check against every other character if the partition that makes them one part is palindromic, and if so we call dfs starting on the next character, so its better.
time complexity: 
space complexity: 

---

