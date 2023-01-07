---
tags:
- leetcode
---
**Title**: 1448. Count Good Nodes in Binary Tree
**Link**: https://leetcode.com/problems/count-good-nodes-in-binary-tree/
**Difficulty**: #leetcode/difficulty/medium 
**Special tags**: #neetcode/area/trees 
**Status**: #leetcode/status/completed  
**Time**: 00 : 07 : 06

---
# Problem Statement
Given a binary tree `root`, a node _X_ in the tree is named **good** if in the path from root to _X_ there are no nodes with a value _greater than_ X.

Return the number of **good** nodes in the binary tree.

---
# My Solution
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def goodNodes(self, root: TreeNode) -> int:

        def is_good(node, max_val):
            if not node:
                return 0
            elif node.val >= max_val:
                return 1 + is_good(node.left, node.val) + is_good(node.right, node.val)
            else:
                return is_good(node.left, max_val) + is_good(node.right, max_val)
        
        return is_good(root, root.val)
```
notes: 
time complexity: 
space complexity: 

---
# Best Solution
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def goodNodes(self, root: TreeNode) -> int:
        def dfs(node, maxVal):
            if not node:
                return 0

            res = 1 if node.val >= maxVal else 0
            maxVal = max(maxVal, node.val)
            res += dfs(node.left, maxVal)
            res += dfs(node.right, maxVal)
            return res

        return dfs(root, root.val)
```
notes: 
time complexity: 
space complexity: 

---

