---
tags:
- leetcode
---
**Title**: 417. Pacific Atlantic Water Flow
**Link**: https://leetcode.com/problems/pacific-atlantic-water-flow/
**Difficulty**: #leetcode/difficulty/medium 
**Special tags**: #neetcode/area/graphs #leetcode/couldnt_solve 
**Status**: #leetcode/status/completed  
**Time**: 

---
# Problem Statement
There is an `m x n` rectangular island that borders both the **Pacific Ocean** and **Atlantic Ocean**. The **Pacific Ocean** touches the island's left and top edges, and the **Atlantic Ocean** touches the island's right and bottom edges.

The island is partitioned into a grid of square cells. You are given an `m x n` integer matrix `heights` where `heights[r][c]` represents the **height above sea level** of the cell at coordinate `(r, c)`.

The island receives a lot of rain, and the rain water can flow to neighboring cells directly north, south, east, and west if the neighboring cell's height is **less than or equal to** the current cell's height. Water can flow from any cell adjacent to an ocean into the ocean.

Return _a **2D list** of grid coordinates_ `result` _where_ `result[i] = [ri, ci]` _denotes that rain water can flow from cell_ `(ri, ci)` _to **both** the Pacific and Atlantic oceans_.

---
# My Solution
```python
class Solution:
    def pacificAtlantic(self, heights: List[List[int]]) -> List[List[int]]:
        res = []
        rows, cols = len(heights), len(heights[0])

        def bfs(i, j):
            oceans = set()
            visited = set()
            queue = collections.deque()
            queue.append((i,j))
            dirs = [(1,0), (-1,0), (0,1), (0,-1)]
            
            while queue:
                r, c = queue.popleft()
                visited.add((r,c))
                for dr,dc in dirs:
                    nr,nc = r + dr, c + dc
                    if nr in range(rows) and nc in range(cols) and (nr, nc) not in visited and heights[nr][nc] <= heights[r][c]:
                        queue.append((nr, nc))
                    if nr < 0 or nc < 0:
                        oceans.add("pacific")
                    if nr >= rows or nc >= cols:
                        oceans.add("atlantic")
            return len(oceans) == 2

        for r in range(rows):
            for c in range(cols):
                if bfs(r, c):
                    res.append((r,c))
        return res
```
after seeing solution
```python
class Solution:
    def pacificAtlantic(self, heights: List[List[int]]) -> List[List[int]]:
        res = []
        rows, cols = len(heights), len(heights[0])
        atlantic, pacific = set(), set()

        def dfs(i, j, visited, prev):
            if i < 0 or j < 0 or i >= rows or j >= cols or heights[i][j] < prev or (i,j) in visited:
                return
            visited.add((i,j))
            dfs(i-1,j, visited, heights[i][j])
            dfs(i+1,j, visited, heights[i][j])
            dfs(i,j-1, visited, heights[i][j])
            dfs(i,j+1, visited, heights[i][j])
        
        for r in range(rows):
            dfs(r, 0, pacific, heights[r][0])
            dfs(r, cols -1, atlantic, heights[r][cols-1])

        for c in range(cols):
            dfs(0, c, pacific, heights[0][c])
            dfs(rows-1, c, atlantic, heights[rows-1][c]) 
        return [[r,c] for r,c in set.intersection(atlantic, pacific)]
```
notes: works but TLE slow.
time complexity: 
space complexity: 

---
# Best Solution
```python
class Solution:
    def pacificAtlantic(self, heights: List[List[int]]) -> List[List[int]]:
        ROWS, COLS = len(heights), len(heights[0])
        pac, atl = set(), set()

        def dfs(r, c, visit, prevHeight):
            if (
                (r, c) in visit
                or r < 0
                or c < 0
                or r == ROWS
                or c == COLS
                or heights[r][c] < prevHeight
            ):
                return
            visit.add((r, c))
            dfs(r + 1, c, visit, heights[r][c])
            dfs(r - 1, c, visit, heights[r][c])
            dfs(r, c + 1, visit, heights[r][c])
            dfs(r, c - 1, visit, heights[r][c])

        for c in range(COLS):
            dfs(0, c, pac, heights[0][c])
            dfs(ROWS - 1, c, atl, heights[ROWS - 1][c])

        for r in range(ROWS):
            dfs(r, 0, pac, heights[r][0])
            dfs(r, COLS - 1, atl, heights[r][COLS - 1])

        res = []
        for r in range(ROWS):
            for c in range(COLS):
                if (r, c) in pac and (r, c) in atl:
                    res.append([r, c])
        return res
```
notes: 
time complexity: 
space complexity: 

---

