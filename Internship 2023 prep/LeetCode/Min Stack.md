---
tags:
- leetcode
---
**Title**: 155. Min Stack
**Link**: https://leetcode.com/problems/min-stack/
**Difficulty**: #leetcode/difficulty/medium  
**Special tags**: #neetcode/area/stack #leetcode/got_best_solution 
**Status**: #leetcode/status/completed  
**Time**: 00 : 08 : 40

---
# Problem Statement
Design a stack that supports push, pop, top, and retrieving the minimum element in constant time.

Implement the `MinStack` class:

-   `MinStack()` initializes the stack object.
-   `void push(int val)` pushes the element `val` onto the stack.
-   `void pop()` removes the element on the top of the stack.
-   `int top()` gets the top element of the stack.
-   `int getMin()` retrieves the minimum element in the stack.

You must implement a solution with `O(1)` time complexity for each function.

---
# My Solution
```python
class MinStack:

    def __init__(self):
        self.stack = []
        self.mins = []
        

    def push(self, val: int) -> None:
        self.stack.append(val)
        if self.mins != []:
            if val < self.mins[-1]:
                self.mins.append(val)
            else:
                self.mins.append(self.mins[-1])
        else:
            self.mins.append(val)

    def pop(self) -> None:
        self.stack.pop()
        self.mins.pop()
        

    def top(self) -> int:
        return self.stack[-1]

    def getMin(self) -> int:
        return self.mins[-1]
```
notes: 
time complexity: 
space complexity: 

---
# Best Solution
```python
class MinStack:
    def __init__(self):
        self.stack = []
        self.minStack = []

    def push(self, val: int) -> None:
        self.stack.append(val)
        val = min(val, self.minStack[-1] if self.minStack else val)
        self.minStack.append(val)

    def pop(self) -> None:
        self.stack.pop()
        self.minStack.pop()

    def top(self) -> int:
        return self.stack[-1]

    def getMin(self) -> int:
        return self.minStack[-1]
```
notes: same solution just for push the min stack value determination is cleaner
time complexity: 
space complexity: 

---

