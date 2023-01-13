---
tags:
- leetcode
---
**Title**: 79. Word Search
**Link**: https://leetcode.com/problems/word-search/
**Difficulty**: #leetcode/difficulty/medium 
**Special tags**: #neetcode/area/backtracking #leetcode/couldnt_solve 
**Status**: #leetcode/status/todo 
**Time**: 00 : 35 : 06

---
# Problem Statement
Given an `m x n` grid of characters `board` and a string `word`, return `true` _if_ `word` _exists in the grid_.

The word can be constructed from letters of sequentially adjacent cells, where adjacent cells are horizontally or vertically neighboring. The same letter cell may not be used more than once.

---
# My Solution
```python
class Solution:
    def exist(self, board: List[List[str]], word: str) -> bool:
        self.ans = False
        seen = set()
        curr_word = ""
        def backtrack(i, j, word_ind, seen, curr_word):
            print(i,j,word_ind, seen, curr_word)
            if word_ind >= len(word) and curr_word == word:
                self.ans |= True 
                return 
            if i < 0 or j < 0 or i >= len(board) or j >= len(board[0]) or (i,j) in seen or word_ind >= len(word):
                return
            if board[i][j] == word[word_ind]:
                print(i,j,word_ind, seen, board[i][j])
                seen.add((i,j))
                curr_word += str(board[i][j])
                backtrack(i,j+1, word_ind + 1, seen, curr_word)
                backtrack(i-1,j, word_ind + 1, seen, curr_word)
                backtrack(i,j-1, word_ind + 1, seen, curr_word)
                backtrack(i+1,j, word_ind + 1, seen, curr_word)
            else:
                backtrack(i,j+1, word_ind + 1, seen, curr_word)
                backtrack(i-1,j, word_ind + 1, seen, curr_word)
                backtrack(i,j-1, word_ind + 1, seen, curr_word)
                backtrack(i+1,j, word_ind + 1, seen, curr_word)
        print(self.ans)
        backtrack(0,0,0,seen, "")
        return self.ans

```
notes: got close I think
time complexity: 
space complexity: 

---
# Best Solution
```python
class Solution:
    def exist(self, board: List[List[str]], word: str) -> bool:
        ROWS, COLS = len(board), len(board[0])
        path = set()

        def dfs(r, c, i):
            if i == len(word):
                return True
            if (
                min(r, c) < 0
                or r >= ROWS
                or c >= COLS
                or word[i] != board[r][c]
                or (r, c) in path
            ):
                return False
            path.add((r, c))
            res = (
                dfs(r + 1, c, i + 1)
                or dfs(r - 1, c, i + 1)
                or dfs(r, c + 1, i + 1)
                or dfs(r, c - 1, i + 1)
            )
            path.remove((r, c))
            return res

        # To prevent TLE,reverse the word if frequency of the first letter is more than the last letter's
        count = defaultdict(int, sum(map(Counter, board), Counter()))
        if count[word[0]] > count[word[-1]]:
            word = word[::-1]
            
        for r in range(ROWS):
            for c in range(COLS):
                if dfs(r, c, 0):
                    return True
        return False

    # O(n * m * 4^n)
```
notes: 
time complexity: 
space complexity: 

---

