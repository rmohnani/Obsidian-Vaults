---
tags:
- leetcode
---
**Title**: 150. Evaluate Reverse Polish Notation
**Link**: https://leetcode.com/problems/evaluate-reverse-polish-notation/
**Difficulty**: #leetcode/difficulty/medium 
**Special tags**: #neetcode/area/stack #leetcode/got_best_solution 
**Status**: #leetcode/status/completed  
**Time**: 00 : 10 : 19

---
# Problem Statement
Evaluate the value of an arithmetic expression in [Reverse Polish Notation](http://en.wikipedia.org/wiki/Reverse_Polish_notation).

Valid operators are `+`, `-`, `*`, and `/`. Each operand may be an integer or another expression.

**Note** that division between two integers should truncate toward zero.

It is guaranteed that the given RPN expression is always valid. That means the expression would always evaluate to a result, and there will not be any division by zero operation.
basically post-fix notation

---
# My Solution
```python
class Solution:
    def evalRPN(self, tokens: List[str]) -> int:
        stack = []
        operations = {"+", "-", "*", "/"}
        for item in tokens:
            # print(stack)
            if item not in operations:
                stack.append(item)
            else:
                s_num = int(stack.pop())
                f_num = int(stack.pop())
                val = 0
                if item == "+":
                    val = f_num + s_num
                elif item == "-":
                    val = f_num - s_num
                elif item == "*":
                    val = f_num * s_num
                elif item == "/":
                    val = int(f_num / s_num)
                else:
                    print("error: invalid operation")
                    exit
                stack.append(str(val))
                
        return stack.pop()
```
notes: 
time complexity: 
space complexity: 

---
# Best Solution
```python
class Solution:
    def evalRPN(self, tokens: List[str]) -> int:
        stack = []
        for c in tokens:
            if c == "+":
                stack.append(stack.pop() + stack.pop())
            elif c == "-":
                a, b = stack.pop(), stack.pop()
                stack.append(b - a)
            elif c == "*":
                stack.append(stack.pop() * stack.pop())
            elif c == "/":
                a, b = stack.pop(), stack.pop()
                stack.append(int(b / a))
            else:
                stack.append(int(c))
        return stack[0]
```
notes: could just have everything in stack be an int which is smarter probably would've done this fix if trying to better working solution, effectively same though this is just cleaner
time complexity: 
space complexity: 

---

