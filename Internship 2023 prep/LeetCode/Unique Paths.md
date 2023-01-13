---
tags:
- leetcode
---
**Title**: 62. Unique Paths
**Link**: https://leetcode.com/problems/unique-paths/description/
**Difficulty**: #leetcode/difficulty/medium 
**Special tags**: #neetcode/area/dp_2d 
**Status**: #leetcode/status/completed 
**Time**:   00 : 04 : 38

---
# Problem Statement
There is a robot on an `m x n` grid. The robot is initially located at the **top-left corner** (i.e., `grid[0][0]`). The robot tries to move to the **bottom-right corner** (i.e., `grid[m - 1][n - 1]`). The robot can only move either down or right at any point in time.

Given the two integers `m` and `n`, return _the number of possible unique paths that the robot can take to reach the bottom-right corner_.

The test cases are generated so that the answer will be less than or equal to `2 * 109`.

---
# My Solution
```python
class Solution:
    def uniquePaths(self, m: int, n: int) -> int:
        grid = [[0 for i in range(n)] for j in range(m)]
        
        for r in range(m):
            grid[r][n-1] = 1
        for c in range(n):
            grid[m-1][c] = 1
        
        for i in range(m-2, -1, -1):
            for j in range(n-2, -1, -1):
                grid[i][j] = grid[i+1][j] + grid[i][j+1]
        return grid[0][0]
        
```
notes: 
time complexity: 
space complexity: 

---
# Best Solution
```python
class Solution:
    def uniquePaths(self, m: int, n: int) -> int:
        row = [1] * n

        for i in range(m - 1):
            newRow = [1] * n
            for j in range(n - 2, -1, -1):
                newRow[j] = newRow[j + 1] + row[j]
            row = newRow
        return row[0]

        # O(n * m) O(n)
```
notes: 
time complexity: 
space complexity: 

---

