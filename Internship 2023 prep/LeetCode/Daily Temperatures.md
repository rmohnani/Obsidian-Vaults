---
tags:
- leetcode
---
**Title**: 739. Daily Temperatures
**Link**: https://leetcode.com/problems/daily-temperatures/
**Difficulty**: #leetcode/difficulty/medium 
**Special tags**: #neetcode/area/stack #leetcode/couldnt_solve 
**Status**: #leetcode/status/todo 

---
# Problem Statement
Given an array of integers `temperatures` represents the daily temperatures, return _an array_ `answer` _such that_ `answer[i]` _is the number of days you have to wait after the_ `ith` _day to get a warmer temperature_. If there is no future day for which this is possible, keep `answer[i] == 0` instead.

---
# My Solution
Anish's solution
```python
class Solution:
    def dailyTemperatures(self, temperatures: List[int]) -> List[int]:
        answer = [0 for i in range(0, len(temperatures))]
        temp_stack = [0]
        for i in range(1, len(temperatures)):
            while len(temp_stack) > 0 and temperatures[i] > temperatures[temp_stack[-1]]:
                idx = temp_stack.pop()
                answer[idx] = i - idx
            temp_stack.append(i)
        return answer
```
notes: 
time complexity: 
space complexity: 

---
# Best Solution
```python
class Solution:
    def dailyTemperatures(self, temperatures: List[int]) -> List[int]:
        ans = [0 for i in range(len(temperatures))]
        temp_stack = [(0, temperatures[0])]
        for i in range(1, len(temperatures)):
            # print(temp_stack)
            while temp_stack and temperatures[i] > temp_stack[-1][1]:
                idx, temp = temp_stack.pop()
                ans[idx] = i - idx
            temp_stack.append((i, temperatures[i]))
        return ans
```

notes: 
time complexity: 
space complexity: 

---

