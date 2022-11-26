---
tags:
- leetcode
---
**Title**: 981. Time Based Key-Value Store
**Link**: https://leetcode.com/problems/time-based-key-value-store/
**Difficulty**: #leetcode/difficulty/medium 
**Special tags**: #neetcode/area/binary_search #leetcode/got_best_solution 
**Status**: #leetcode/status/completed  

---
# Problem Statement
Design a time-based key-value data structure that can store multiple values for the same key at different time stamps and retrieve the key's value at a certain timestamp.

Implement the `TimeMap` class:

-   `TimeMap()` Initializes the object of the data structure.
-   `void set(String key, String value, int timestamp)` Stores the key `key` with the value `value` at the given time `timestamp`.
-   `String get(String key, int timestamp)` Returns a value such that `set` was called previously, with `timestamp_prev <= timestamp`. If there are multiple such values, it returns the value associated with the largest `timestamp_prev`. If there are no values, it returns `""`.
---
# My Solution
```python
class TimeMap:

    def __init__(self):
        self.time_map = dict()
        
    def set(self, key: str, value: str, timestamp: int) -> None:
        if key not in self.time_map:
            self.time_map[key] = []
        self.time_map[key].append([timestamp, value])
            


    def get(self, key: str, timestamp: int) -> str:
        arr = self.time_map.get(key, [])
        left = 0
        right = len(arr) - 1
        val = ""
        while left <= right:
            mid = (left + right) // 2
            if arr[mid][0] <= timestamp:
                left = mid + 1
                val = arr[mid][1]
            else:
                right = mid - 1

        return val
        


# Your TimeMap object will be instantiated and called as such:
# obj = TimeMap()
# obj.set(key,value,timestamp)
# param_2 = obj.get(key,timestamp)
```
notes: 
time complexity: 
space complexity: 

---
# Best Solution
```python

View on Github
class TimeMap:
    def __init__(self):
        """
        Initialize your data structure here.
        """
        self.keyStore = {}  # key : list of [val, timestamp]

    def set(self, key: str, value: str, timestamp: int) -> None:
        if key not in self.keyStore:
            self.keyStore[key] = []
        self.keyStore[key].append([value, timestamp])

    def get(self, key: str, timestamp: int) -> str:
        res, values = "", self.keyStore.get(key, [])
        l, r = 0, len(values) - 1
        while l <= r:
            m = (l + r) // 2
            if values[m][1] <= timestamp:
                res = values[m][0]
                l = m + 1
            else:
                r = m - 1
        return res
```
notes: cleaner
time complexity: 
space complexity: 

---

