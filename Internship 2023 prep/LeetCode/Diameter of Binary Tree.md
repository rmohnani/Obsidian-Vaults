---
tags:
- leetcode
---
**Title**: 543. Diameter of Binary Tree
**Link**: https://leetcode.com/problems/diameter-of-binary-tree/
**Difficulty**: #leetcode/difficulty/easy 
**Special tags**: #neetcode/area/trees #leetcode/couldnt_solve 
**Status**: #leetcode/status/todo 
**Time**: 

---
# Problem Statement
Given the `root` of a binary tree, return _the length of the **diameter** of the tree_.

The **diameter** of a binary tree is the **length** of the longest path between any two nodes in a tree. This path may or may not pass through the `root`.

The **length** of a path between two nodes is represented by the number of edges between them.

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
    def diameterOfBinaryTree(self, root: Optional[TreeNode]) -> int:
        self.max_diam = 0

        def dfs_ret_height_update_max(node):
            if not node:
                return -1
            left = dfs_ret_height_update_max(node.left)
            right = dfs_ret_height_update_max(node.right)
            self.max_diam = max(self.max_diam, left + right + 2)
            return 1 + max(left, right)
        
        dfs_ret_height_update_max(root)
        return self.max_diam
            
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
    def diameterOfBinaryTree(self, root: Optional[TreeNode]) -> int:
        res = 0

        def dfs(root):
            nonlocal res

            if not root:
                return 0
            left = dfs(root.left)
            right = dfs(root.right)
            res = max(res, left + right)

            return 1 + max(left, right)

        dfs(root)
        return res

```
notes: stylistically slightly different from what is in the video solution which I've written up in my-sol part.
time complexity: 
space complexity: 

---

