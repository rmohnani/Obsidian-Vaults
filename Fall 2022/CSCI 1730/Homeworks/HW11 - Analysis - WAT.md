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

It doesn't make sense to be able to add and subtract and perform arithmetic operations on booleans, because adding booleans is not the same as anding them. It seems that under the hood in cases where arithmetic is used, True evaluates to 1 and False to 0 which seems to make sense, but the behaviour is still strange and really in my opinion should give an error.

# Example 2
Language: 