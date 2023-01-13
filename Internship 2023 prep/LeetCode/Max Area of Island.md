---
tags:
- leetcode
---
**Title**: 695. Max Area of Island
**Link**: https://leetcode.com/problems/max-area-of-island/
**Difficulty**: #leetcode/difficulty/medium 
**Special tags**: #neetcode/area/graphs #leetcode/got_best_solution 
**Status**: #leetcode/status/completed  
**Time**:   00 : 20 : 21

---
# Problem Statement
You are given an `m x n` binary matrix `grid`. An island is a group of `1`'s (representing land) connected **4-directionally** (horizontal or vertical.) You may assume all four edges of the grid are surrounded by water.

The **area** of an island is the number of cells with a value `1` in the island.

Return _the maximum **area** of an island in_ `grid`. If there is no island, return `0`.

---
# My Solution
```python
class Solution:
    def maxAreaOfIsland(self, grid: List[List[int]]) -> int:
        rows, cols = len(grid), len(grid[0])
        visited = set()
        max_area = 0

        def bfs(i, j):
            queue = collections.deque()
            queue.append((i,j))
            visited.add((i,j))
            dirs = [(1,0), (0,1), (-1, 0), (0, -1)]
            area = 0
            while queue:
                r, c = queue.popleft()
                area += 1
                print(area, queue)
                for dr,dc in dirs:
                    nr, nc = r + dr, c + dc
                    if nr in range(rows) and nc in range(cols) and grid[nr][nc] == 1 and (nr, nc) not in visited:
                        queue.append((nr,nc))
                        visited.add((nr,nc))
            return area
                

        for r in range(rows):
            for c in range(cols):
                if grid[r][c] == 1 and (r, c) not in visited:
                    new_area = bfs(r,c)
                    print(r,c, new_area)
                    max_area = max(max_area, new_area)
        return max_area
```
notes: 
time complexity: 
space complexity: 

---
# Best Solution
```python
class Solution:
    def maxAreaOfIsland(self, grid: List[List[int]]) -> int:
        ROWS, COLS = len(grid), len(grid[0])
        visit = set()

        def dfs(r, c):
            if (
                r < 0
                or r == ROWS
                or c < 0
                or c == COLS
                or grid[r][c] == 0
                or (r, c) in visit
            ):
                return 0
            visit.add((r, c))
            return 1 + dfs(r + 1, c) + dfs(r - 1, c) + dfs(r, c + 1) + dfs(r, c - 1)

        area = 0
        for r in range(ROWS):
            for c in range(COLS):
                area = max(area, dfs(r, c))
        return area
```
notes: dfs solution instead of bfs
time complexity: 
space complexity: 

---

