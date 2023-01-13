---
tags:
- leetcode
---
**Title**: 51. N-Queens
**Link**: https://leetcode.com/problems/n-queens/
**Difficulty**: #leetcode/difficulty/hard  
**Special tags**: #neetcode/area/backtracking 
**Status**: #leetcode/status/todo 
**Time**: 00 : 06 : 21

---
# Problem Statement
The **n-queens** puzzle is the problem of placing `n` queens on an `n x n` chessboard such that no two queens attack each other.

Given an integer `n`, return _all distinct solutions to the **n-queens puzzle**_. You may return the answer in **any order**.

Each solution contains a distinct board configuration of the n-queens' placement, where `'Q'` and `'.'` both indicate a queen and an empty space, respectively.

---
# My Solution
solution so far, think I can do it but will take time I don't necessarily have rn
```python
class Solution:
    def solveNQueens(self, n: int) -> List[List[str]]:
        possible_spaces = set([(i,j) for i in range(n) for j in range(n)])
        def remove_spaces(row,col,poss_spaces):
            hv_spaces = set()
            for j in range(n):
                hv_spaces.add((row,j))
            for i in range(n):
                hv_spaces.add((i,col))
            new_row, new_col = row, col
            while new_row < n and new_col < n:
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

