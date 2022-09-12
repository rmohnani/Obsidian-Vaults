[[2022-09-12 Mon]]

# Implementation Track
**Interpreter** :: Program -> Answer/Value

Simulates the program (pretends its being run)

**Compiler** :: Program in Language L -> Program in target language T 

**Evaluator** - a thing that eventually gives you an answer using some combination of Interpreter and Compiler

Languages are independent of their implementations
notion of interpreted and compiled languages are nonsensical because any can be both.

 # look_into - just in time compilers

call by value/ eager 
eager as opposed to lazy
eager evaluates expressions into values always immediately,
lazy languages say they can evaluate expressions later

sequential (evaluate expression to completion) or parallel in that it evaluates partially both

SMoL is sequential and eager and left-to-right
evaluation is a tree traversal




