**[Assignment](http://cs.brown.edu/courses/csci1730/2022/smol.html)**

[[2022-09-07 Wed]]

16:29 - Installed [Stacker](https://github.com/LuKC1024/stacker)
16:31 - Installed [SMoL family of languages](https://github.com/shriram/smol)
17:56 - Finished Scope


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

This returns 3. Because `y` is defined before the function call, this executes fine, because the top level environment has a definition for `y`. 

```racket
#lang stacker/smol/fun

(defvar y 100)
(deffun (addy x)
  (defvar y 200)
  (+ x y))
(addy 2)

```

> [!important] 
> If a variable is defined in both the function body and the top level block, the function body block takes precedence in deciding the value to use. Variables can only use definitions in their block or super-blocks, they cannot look into sub blocks. If no valid variable definition is found it returns `error`

For example a variable used in the top level block can only use a top level definition and cannot use the definition in any sub block

```racket
(defvar x 1)
(deffun (main)
  (defvar x 2)
  (deffun (get-x) x)
  (get-x))

(main)
```

Returns 2, because get-x is defined inside main block in which the value of x is 2.

```racket
(defvar x 1)
(deffun (get-x) x)

(deffun (main)
  (defvar x 2)
  (get-x))
(main)
```

Returns 1 because get-x is defined in top level block where x is defined to be 1.

**When we see a variable reference, how do we find the corresponding declaration, if any?**

 - We look first in its block, and then in super blocks until we hit the top level block, at which point if no declaration is found we error.

> [!important] 
> We find the declaration by looking in a series of blocks. We start with the block in which the variable reference occurs. If the variable is declared in the current block, we use that declaration. Otherwise, we look up the block in which the current block occurs, and so on recursively. (Specifically, if the current block is a function body, the next block will be the block in which the function definition is; if the current block is the top-level block, the next block will be the _primordial block_.) If the current block is already the primordial block and we still haven't found a corresponding declaration, the variable is unbound.

> [!important] 
> The primordial block is a non-visible block enclosing the top-level block. This block defines values and functions (e.g., `+` and `/`) that are provided by the language itself.

```racket
#lang stacker/smol/fun

(defvar x 1)
(defvar x 2)
x

```

> [!error] 
> This returns `error`. It is an error to define a variable twice within a single block.

The most recent value isn't used as in other languages.

```racket
(deffun (f x x)
  (+ x x))
(f 1 2)
```

Because x is used twice in the function body block

### Running in DrRacket
```racket
(defvar x 1)
(deffun (get-x) x)

(deffun (main)
  (defvar x 2)
  (get-x))
(main)
```

![[Screen Shot 2022-09-07 at 5.43.26 PM.png | 400]]
![[Screen Shot 2022-09-07 at 5.43.40 PM.png | 400]]

![[Screen Shot 2022-09-07 at 5.44.19 PM.png | 400]]

![[Screen Shot 2022-09-07 at 5.44.23 PM.png | 400]]

![[Screen Shot 2022-09-07 at 5.44.26 PM.png | 400]]

![[Screen Shot 2022-09-07 at 5.44.29 PM.png | 400]]

![[Screen Shot 2022-09-07 at 5.44.31 PM.png | 400]]

## Task 2: [Order](https://script.google.com/a/macros/brown.edu/s/AKfycbyOWF819avuY6uh0PlP-GAVNCZc0xHucUuzgaJD8ZLng5b329uzM2jVsN1zJGMyk5PAgQ/exec?tutorial=order&userId=rohit_mohnani)

> [!note] 
> for arithmetic operators like `+`, `-`, `/`, `*` they come before the values they operate on. The syntax is `(operator first_val second_val)`. The operation then performed is first_val operation second_val.

```racket
(defvar x (/ 1 0))
42
```

> [!important] 
> When you define a variable (in this case, `x`), you have to bind it to a value, no matter whether or not you need the value of that variable later in the program. 

The program errors when it tries to evaluate `(/ 1 0)`.



