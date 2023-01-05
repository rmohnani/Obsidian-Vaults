---
tags:
- leetcode
---
**Title**: 110. Balanced Binary Tree
**Link**: https://leetcode.com/problems/balanced-binary-tree/
**Difficulty**: #leetcode/difficulty/easy 
**Special tags**: #neetcode/area/trees #leetcode/got_best_solution 
**Status**: #leetcode/status/completed  
**Time**: 00 : 07 : 56

---
# Problem Statement
Given a binary tree, determine if it is 
height-balanced. 
A **height-balanced** binary tree is a binary tree in which the depth of the two subtrees of every node never differs by more than one.

---
# My Solution
first try
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def isBalanced(self, root: Optional[TreeNode]) -> bool:
        self.is_bal = True

        def dfs_get_height_check_bal(node):
            if not node:
                return 0
            
            left = dfs_get_height_check_bal(node.left)
            right = dfs_get_height_check_bal(node.right)
            diff = abs(left - right)
            if diff > 1:
                self.is_bal &= False
            return 1 + max(left, right)
        
        dfs_get_height_check_bal(root)
        return self.is_bal
        
```
second try
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def isBalanced(self, root: Optional[TreeNode]) -> bool:

        def dfs_get_height_check_bal(node):
            if not node:
                return 0
            
            left = dfs_get_height_check_bal(node.left)
            right = dfs_get_height_check_bal(node.right)
            diff = abs(left - right)
            if diff > 1:
                return False
            if left is False or right is False:
                return False
            return 1 + max(left, right)
        
        is_bal = dfs_get_height_check_bal(root)
        if type(is_bal) == bool:
            return is_bal
        return True
        
```
notes: In first simply keep going even if we find a false, in second attempt to immediately go back up the recursive stack and return false
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
    def isBalanced(self, root: Optional[TreeNode]) -> bool:
        def dfs(root):
            if not root:
                return [True, 0]

            left, right = dfs(root.left), dfs(root.right)
            balanced = left[0] and right[0] and abs(left[1] - right[1]) <= 1
            return [balanced, 1 + max(left[1], right[1])]

        return dfs(root)[0]
```
notes: Pairs whether is balanced, and height of tree in output of recursive call. Which is what I thought would also work.
time complexity: 
space complexity: 

---

