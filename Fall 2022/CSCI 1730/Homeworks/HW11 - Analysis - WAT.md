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

Language: Javascript

Program: 
```javascript
console.log("55" + [2, "3", null]);
console.log([1] + [2,3,4]);
console.log([1, 2, 3] + [2,3,4]);
```

Returns
```
552,3,
12,3,4
1,2,32,3,4
```

Interesting:

Its interesting that whenever we have something like a string, a number, or another array added to an array, whatever the last item in that first object is, is simply prepended to the first item of the array we're adding to it. We see that in the first one 55 is prepended to 2 (the first item in the array), while the rest are unchanged. Same for when we have a list of 1 element and a list of multiple elements has the last element 3 prepended to 2 (the first element) in the second array. Which is all WAT, it should just throw an error for mismatching types because there is no reasonable way to define said interactions and thus shouldn't even be permitted.
