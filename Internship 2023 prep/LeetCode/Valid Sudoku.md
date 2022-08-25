---
tags:
- leetcode
---
**Title**: 36. Valid Sudoku
**Link**: https://leetcode.com/problems/valid-sudoku/
**Difficulty**: #leetcode/difficulty/medium  
**Special tags**: #neetcode/area/arrays_hashing 
**Status**: #leetcode/status/completed 

---
# Problem Statement

Determine if a `9 x 9` Sudoku board is valid. Only the filled cells need to be validated **according to the following rules**:

1.  Each row must contain the digits `1-9` without repetition.
2.  Each column must contain the digits `1-9` without repetition.
3.  Each of the nine `3 x 3` sub-boxes of the grid must contain the digits `1-9` without repetition.

**Note:**

-   A Sudoku board (partially filled) could be valid but is not necessarily solvable.
-   Only the filled cells need to be validated according to the mentioned rules.

---
# My Solution

```python
class Solution:
    def isValidSudoku(self, board: List[List[str]]) -> bool:
        rows = {}
        columns = {}
        boxes = {}
        
        for row_no in range(len(board)):
            for column_no in range(len(board[0])):
                if row_no not in rows:
                    rows[row_no] = set()
                if column_no not in columns:
                    columns[column_no] = set()
                box_no = (3 * (row_no // 3)) + (column_no // 3)
                if box_no not in boxes:
                    boxes[box_no] = set()
                
                val = board[row_no][column_no]
                if val != ".":
                    
                    if val in rows[row_no]:
                        return False
                    else:
                        rows[row_no].add(val)
                    
                    if val in columns[column_no]:
                        return False
                    else:
                        columns[column_no].add(val)
                    
                    if val in boxes[box_no]:
                        return False
                    else:
                        boxes[box_no].add(val)
                        
        return True
```
notes: Keep hashsets for each of the rows, columns, and boxes. As you encounter values check the respective hashsets. If the value is already in the hashset return False because duplicate, otherwise continue. If finish loops return True because no duplicates.
time complexity: O(n^2) no. of cells
space complexity: O(n)

Could also do this with hashmaps which might be a bit faster due to faster lookups, but in theory they are the same solution.

---
# Best Solution
#leetcode/got_best_solution 

```python
class Solution:
	def isValidSudoku(self, board: List[List[str]]) -> bool:
		cols = collections.defaultdict(set)
		rows = collections.defaultdict(set)
		squares = collections.defaultdict(set) # key = (r /3, c /3)
		
		for r in range(9):
			for c in range(9):
				if board[r][c] == ".":
					continue
				if ( board[r][c] in rows[r] or 
					board[r][c] in cols[c] or 
					board[r][c] in squares[(r // 3, c // 3)] ): 
					return False
				cols[c].add(board[r][c])
				rows[r].add(board[r][c])
				squares[(r // 3, c // 3)].add(board[r][c])
		return True
```
notes: a little bit cleaner than mine but same implementation
time complexity: 
space complexity: 

---

