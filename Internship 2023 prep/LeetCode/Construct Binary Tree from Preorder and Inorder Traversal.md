---
tags:
- leetcode
---
**Title**: 105. Construct Binary Tree from Preorder and Inorder Traversal
**Link**: https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/
**Difficulty**: #leetcode/difficulty/medium 
**Special tags**: #neetcode/area/trees #leetcode/couldnt_solve 
**Status**: #leetcode/status/completed  
**Time**: 

---
# Problem Statement
Given two integer arrays `preorder` and `inorder` where `preorder` is the preorder traversal of a binary tree and `inorder` is the inorder traversal of the same tree, construct and return _the binary tree_.

---
# My Solution
couldn't figure it out, but lowkey didn't thinnk as much as I should have. Was potentially close to a solution.
notes: 
time complexity: 
space complexity: 

---
# Best Solution
```python
class Solution:
    def buildTree(self, preorder: List[int], inorder: List[int]) -> Optional[TreeNode]:
        if not preorder or not inorder:
            return None

        root = TreeNode(preorder[0])
        mid = inorder.index(preorder[0])
        root.left = self.buildTree(preorder[1 : mid + 1], inorder[:mid])
        root.right = self.buildTree(preorder[mid + 1 :], inorder[mid + 1 :])
        return root
```
notes: 
time complexity: 
space complexity: 

---

