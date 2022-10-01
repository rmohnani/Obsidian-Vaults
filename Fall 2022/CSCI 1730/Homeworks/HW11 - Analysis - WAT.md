[**Assignment**](https://cs.brown.edu/courses/csci1730/2022/wat.html)

# Example 1
Language: Python

Program:
```python
print(True + True)
print(True - True)
print(True + False)
print(False - True)
```
returns `2 0 1 -1`

Interesting:

It doesn't make sense to be able to add and subtract and perform arithmetic operations on booleans, because adding booleans is not the same as anding them. It seems that under the hood in cases where arithmetic is used, True evaluates to 1 and False to 0 which seems to make sense, but the behaviour is still a WAT and really in my opinion should give an error.

# Example 2
Language: Python

Program:
```python
a = 256
b = 256
print(a is b)

a = 257
b = 257
print(a is b)
```

This prints True and then False

Interesting:

cited from: https://www.youtube.com/watch?v=sH4XF6pKKmk

Apparently this is because the Cpython implementation keeps the first 256 integers as objects in memory and doesn't create duplicates of them. And is operator checks if the object or essentially the memory location is the same. So it returns True. But for 257 a and b get different copies of 257 stored in different places in memory. So checking on that returns False. Strange behaviour since if we want to do comparisons we really should be using the == operator instead, but still WAT.

# Example 3

Language: 