---
tags:
- leetcode
---
**Title**: 74. Search a 2D Matrix
**Link**: https://leetcode.com/problems/search-a-2d-matrix/
**Difficulty**: #leetcode/difficulty/medium 
**Special tags**: #neetcode/area/binary_search #leetcode/couldnt_solve 
**Status**: #leetcode/status/completed  

---
# Problem Statement
Write an efficient algorithm that searches for a value `target` in an `m x n` integer matrix `matrix`. This matrix has the following properties:

-   Integers in each row are sorted from left to right.
-   The first integer of each row is greater than the last integer of the previous row.
---
# My Solution
```python
class Solution:
    def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:

        # determine row
        fst_col = [matrix[i][0] for i in range(len(matrix))]

        def bs(arr, val, l, r, strict):

            while l <= r:
                middle = l + ((r-l) // 2)
                if arr[middle] < val:
                    l = middle + 1
                elif arr[middle] > val:
                    r = middle - 1
                else:
                    return middle
                
            if strict:
                return -1
            return l
        row_idx = bs(fst_col, target, 0, len(fst_col) - 1, False) - 1
        print(row_idx)

        return bs(matrix[row_idx], target, 0, len(matrix[0]) - 1, True) != - 1
```
notes:  Best I could do, couldn't figure out how to get the smallest value close to the target for row-idx. Ahhh looked at solution can't do both using one function.
time complexity: 
space complexity: 

---
# Best Solution
```python
class Solution:
    def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:

        # determine row

        top = 0
        bottom = len(matrix) - 1
        while top <= bottom:
            middle = ((top + bottom) // 2)
            if matrix[middle][-1] < target:
                top = middle + 1
            elif matrix[middle][0] > target:
                bottom = middle - 1
            else:
                break

        if top > bottom:
            return False

        row_idx = (top + bottom) // 2
        left = 0
        right = len(matrix[0]) - 1
        while left <= right:
            middle = (left + right) // 2
            if matrix[row_idx][middle] < target:
                left = middle + 1
            elif matrix[row_idx][middle] > target:
                right = middle - 1
            else:
                return True
        return False

                
```
notes: 
time complexity: log m + log n
space complexity: 

---

