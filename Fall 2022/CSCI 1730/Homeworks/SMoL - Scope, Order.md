**[Assignment](http://cs.brown.edu/courses/csci1730/2022/smol.html)**

[[2022-09-07 Wed]]

16:29 - Installed [Stacker](https://github.com/LuKC1024/stacker)
16:31 - Installed [SMoL family of languages](https://github.com/shriram/smol)

# Tasks

## Task 1: [Scope](https://script.google.com/a/macros/brown.edu/s/AKfycbwgB8TFheyjhj1YvOQKytu5Xb3A7dQ0B6zN1kgA93DLgn9oiAUovY-mHfum-M7KolsL/exec?tutorial=scope)

### Variable Defintions
```racket
#lang stacker/smol/fun

(defvar x 1)
(defvar y 2)
x
y
(+ x y)
```

>[!Note]
>syntax: `(defvar variable_name variable_value)` 
>`defvar` binds the variable name to the value provided after. 

So in the example it binds x to 1 and y to 2.
All 'operators' are the first thing written, like how:
`+` operation is first then we have x and y which the operation needs to be performed on. 

### Errors
```racket
#lang stacker/smol/fun

(defvar x 123)
(/ x 0)

```

> [!error]
This gives `error` because can't divide a number by 0

```racket
#lang stacker/smol/fun

true
false
(+ true false)

```

> [!error] 
This gives a more specific `#t #f error` because you can't add 2 boolean values.

> [!error] 
**It is an error to compute the value of an undefined variable.**

### Function Definitions

```racket
#lang stacker/smol/fun

(deffun (double x)
  (+ x x))
(double 2)

```

> [!note] 
> syntax: `(deffun (func_name func_input) 'function body')`
> `deffun` binds the function name to the function body

> [!note] 
> A function is invoked/called using this syntax: `(func_name func_input)`


```racket
(deffun (addy x)
  (defvar y 1)
  (+ x y))
(addy 2)
```

This returns 3 because y is defined in the function body to be 1.

```racket
(defvar y 1)
(deffun (addy x)
  (+ x y))
(addy 2)
```

This also returns 3.

> [!important] 
> Since there is no `y` in the function definition block we look in the top level block for a `y`. Since it exists the program executes without error.

> [!info]
> A block is a sequence of definitions followed by a sequence of expressions.
> Blocks form a tree-like structure in a program

```racket
#lang stacker/smol/fun

(deffun (f x)
  (defvar y 1)
  (+ x y))

(deffun (g)
  (deffun (h m)
    (* 2 m))
  (f (h 3)))

(g)
```

Here the Blocks are:
	- The Top level block where `f`, `g` are defined and `g` is called.
	- `f`'s  body, which is a sub block of Top
	- `g`'s  body, which is a sub block of Top
	- `h`'s  body, which is a sub block of `g`

```racket
#lang stacker/smol/fun

(deffun (addy x)
  (+ x y))
(defvar y 1)
(addy 2)

```

This returns 3. 
