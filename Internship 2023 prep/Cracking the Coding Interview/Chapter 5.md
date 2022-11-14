# Chapter: Bit Manipulation
---
# Key Points
- XOR is ^ where it is a 1 if the bits are different
- NOT is ~ where all the bits are flipped
- multiplication by 2^3 is shiffting it left 3 bits
- x ^ 0s = x
- x ^ 1s = ~x
- x ^ x = 0
- x & 0s = 0
- x & 1s = x
- x & x = x
- x | 0s = x
- x | 1s = 1s
- x | x = x
- Computers store integers in 2s complement. Binary representation of -K as a N-bit number is concat(1, 2^(N-1) - K)
- There are two right shifts. Logical right shift shifts the bits and puts a 0 in the most significant bit indicated using >>>. Arithmetic right shift shifts the bits but maintains the value of the sign (most significant) bit so is effectively like dividing by 2 indicated by >>.
- To get bits we use a maskk of (1 << i) and & with num. To set bits we do (1 << i) and | with num.
---
# Question


# Solution

---
