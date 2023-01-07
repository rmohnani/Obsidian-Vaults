---
tags:
- leetcode
---
**Title**: 98. Validate Binary Search Tree
**Link**: https://leetcode.com/problems/validate-binary-search-tree/
**Difficulty**: #leetcode/difficulty/medium 
**Special tags**: #neetcode/area/trees #leetcode/got_best_solution 
**Status**: #leetcode/status/completed  
**Time**: 00 : 14 : 59

---
# Problem Statement
Given the `root` of a binary tree, _determine if it is a valid binary search tree (BST)_.

A **valid BST** is defined as follows:

-   The left subtree of a node contains only nodes with keys **less than** the node's key.
-   The right subtree of a node contains only nodes with keys **greater than** the node's key.
-   Both the left and right subtrees must also be binary search trees.

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
    def isValidBST(self, root: Optional[TreeNode]) -> bool:
        
        def isValidNode(node, min_val, max_val):
            if not node:
                return True
            elif min_val < node.val < max_val:
                return isValidNode(node.left, min_val, node.val) and isValidNode(node.right, node.val, max_val)
            else:
                return False
        
        return isValidNode(root, -float("inf"), float("inf"))
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
    def isValidBST(self, root: TreeNode) -> bool:
        def valid(node, left, right):
            if not node:
                return True
            if not (node.val < right and node.val > left):
                return False

            return valid(node.left, left, node.val) and valid(
                node.right, node.val, right
            )

        return valid(root, float("-inf"), float("inf"))
```
notes: same
time complexity: 
space complexity: 

---

