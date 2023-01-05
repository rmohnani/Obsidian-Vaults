---
tags:
- leetcode
---
**Title**: 572. Subtree of Another Tree
**Link**: https://leetcode.com/problems/subtree-of-another-tree/
**Difficulty**: #leetcode/difficulty/easy 
**Special tags**: #neetcode/area/trees #leetcode/couldnt_solve 
**Status**: #leetcode/status/completed  
**Time**: 00 : 28 : 06

---
# Problem Statement
Given the roots of two binary trees `root` and `subRoot`, return `true` if there is a subtree of `root` with the same structure and node values of `subRoot` and `false` otherwise.

A subtree of a binary tree `tree` is a tree that consists of a node in `tree` and all of this node's descendants. The tree `tree` could also be considered as a subtree of itself.

---
# My Solution
doest work close thoigh 177/182 tests
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def isSubtree(self, root: Optional[TreeNode], subRoot: Optional[TreeNode]) -> bool:
        if not root and not subRoot:
            return True
        elif root and subRoot:
            return (root.val == subRoot.val and self.isSubtree(root.left, subRoot.left) and self.isSubtree(root.right, subRoot.right)) or (self.isSubtree(root.left, subRoot) or self.isSubtree(root.right, subRoot))
        else:
            return False
            
        
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
    def isSametree(self, root1: Optional[TreeNode], root2: Optional[TreeNode]) -> bool:
        if not root1 and not root2:
            return True
        elif root1 and root2 and root1.val == root2.val:
            return self.isSametree(root1.left, root2.left) and self.isSametree(root1.right, root2.right)
        else:
            return False

    def isSubtree(self, root: Optional[TreeNode], subRoot: Optional[TreeNode]) -> bool:
	    if subRoot is None:
            return True
        if root is None:
            return False
        
        if self.isSametree(root, subRoot):
            return True
        
        return self.isSubtree(root.left, subRoot) or self.isSubtree(root.right, subRoot)
        
            
        
```
notes: should've used the isSametree function in my code, but thought i could integrate it which caused failure cases I couldn't debug. I also didnt think of the root being None and subroot being none edge cases. 
time complexity: 
space complexity: 

---

