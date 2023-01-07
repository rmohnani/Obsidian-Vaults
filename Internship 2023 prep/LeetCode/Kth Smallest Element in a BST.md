---
tags:
- leetcode
---
**Title**: 230. Kth Smallest Element in a BST
**Link**: https://leetcode.com/problems/kth-smallest-element-in-a-bst/
**Difficulty**: #leetcode/difficulty/medium 
**Special tags**: #neetcode/area/trees #leetcode/got_best_solution 
**Status**: #leetcode/status/completed  
**Time**: 00 : 02 : 51

---
# Problem Statement
Given the `root` of a binary search tree, and an integer `k`, return _the_ `kth` _smallest value (**1-indexed**) of all the values of the nodes in the tree_.

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
    def kthSmallest(self, root: Optional[TreeNode], k: int) -> int:
        ordered_lst = []

        def inorder_traversal(node):
            if not node:
                return None
            if node.left:
                inorder_traversal(node.left)
            ordered_lst.append(node.val)
            if node.right:
                inorder_traversal(node.right)
                
        inorder_traversal(root)
        return ordered_lst[k - 1]
            
```
notes: 
time complexity: 
space complexity: 

---
# Best Solution
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None


class Solution:
    def kthSmallest(self, root: TreeNode, k: int) -> int:
        stack = []
        curr = root

        while stack or curr:
            while curr:
                stack.append(curr)
                curr = curr.left
            curr = stack.pop()
            k -= 1
            if k == 0:
                return curr.val
            curr = curr.right
```
notes: just doing it iteratively instead using a stack
time complexity: 
space complexity: 

---

