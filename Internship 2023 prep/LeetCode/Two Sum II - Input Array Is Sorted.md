---
tags:
- leetcode
---
**Title**: 167. Two Sum II - Input Array Is Sorted
**Link**: https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/
**Difficulty**: #leetcode/difficulty/medium  
**Special tags**: #neetcode/area/two_pointers 
**Status**: #leetcode/status/completed   

---
# Problem Statement

Given a **1-indexed** array of integers `numbers` that is already **_sorted in non-decreasing order_**, find two numbers such that they add up to a specific `target` number. Let these two numbers be `numbers[index1]` and `numbers[index2]` where `1 <= index1 < index2 <= numbers.length`.

Return _the indices of the two numbers,_ `index1` _and_ `index2`_, **added by one** as an integer array_ `[index1, index2]` _of length 2._

The tests are generated such that there is **exactly one solution**. You **may not** use the same element twice.

Your solution must use only constant extra space.

---
# My Solution

```python
class Solution:
    def twoSum(self, numbers: List[int], target: int) -> List[int]:
        left = 0
        right = len(numbers) - 1
        
        while numbers[left] + numbers[right] != target:
            total = numbers[left] + numbers[right]
            if total > target:
                right -= 1
            else:
                left += 1
        
        return [left + 1, right + 1]
        
```
notes:  One pointer on the left and one on the right. If the total is greater than target shift right pointer left. Now the value of the left pointer will also need to be higher. so if the total is less than target shift left pointer right. this means we will always be looking in the correct direction for combinations. because we wont have the case where the left pointer or right pointer may need to backtrack.
time complexity: O(n)
space complexity: O(1)

---
# Best Solution
#leetcode/got_best_solution 
```python
class Solution:
    def twoSum(self, numbers: List[int], target: int) -> List[int]:
        l, r = 0, len(numbers) - 1

        while l < r:
            curSum = numbers[l] + numbers[r]

            if curSum > target:
                r -= 1
            elif curSum < target:
                l += 1
            else:
                return [l + 1, r + 1]
```
notes: Slightly better. uses better termination condition of while left pointer less than right pointer, if they cross then there is no solution. Since we are guaranteed a solution in the question I used that as my termination condition but this is more general.
time complexity: 
space complexity: 

---

