**[Assignment](http://cs.brown.edu/courses/csci1730/2022/smol.html)**


# Tasks
## Task 1: [MutVar](https://script.google.com/a/macros/brown.edu/s/AKfycbyOWF819avuY6uh0PlP-GAVNCZc0xHucUuzgaJD8ZLng5b329uzM2jVsN1zJGMyk5PAgQ/exec?tutorial=mut-vars&userId=rohit_mohnani)
### Mutable Variables
> [!note] 
> `set!` _mutates_ the value of a variable
> It can only mutate existing bindings. If no binding exists it will `error`

> [!important] 
> `set!` expressions produce a special value, the _void_ value, which indicates that evaluating the expression is not meant to produce an interesting value; rather, the evaluation is only for its "side effects".

```racket
#lang stacker/smol/state

(defvar x 12)
(defvar y x)
(set! x 0)
x
y

```

Here `set!` changes the binding of x only, because y is bound to the evaluation of x which is 12 not x itself, so when x is changed y isn't.

> [!important] 
> 1.  Which variable (if any) a `set!` mutates is dictated by scope.
> 2.  Using `set!` to mutate a variable (e.g., `y`) won’t mutate the binding of other variables (e.g., `x`), no matter how the definition of the first variable is related to the second variable (e.g., given `(defvar y x)`, mutating either `x` or `y` will not mutate the other).

> [!important] 
> -   `defvar` creates new bindings.
> - `set!` mutates existing bindings.
> - Referring to a variable gives the value that the variable is bound to at that moment.
> - Function calls are similar to `defvar`. They bind the formal parameters (the names) with the actual parameters (the argument values).


## Task 2: [Begin](https://script.google.com/a/macros/brown.edu/s/AKfycbyOWF819avuY6uh0PlP-GAVNCZc0xHucUuzgaJD8ZLng5b329uzM2jVsN1zJGMyk5PAgQ/exec?tutorial=begin&userId=rohit_mohnani)
> [!note] 
> `begin` lets you evaluate a sequence of expressions and returns the value of the last expression.
> A `begin` expression evaluates its sub-expressions from left to right and produces the value of the right-most expression.
> `begin` computes its sub-expressions in top-to-bottom, left-to-right order, and gives the value of the last expression.
 

> [!important] 
> `(if cnd thn els)` evaluates `cnd`. If the evaluation produces a true value, `thn` is evaluated in place of the whole `if` expression. Otherwise, `els` is evaluated.
> Giving `if` too few or too many subexpressions is a syntactic error.










