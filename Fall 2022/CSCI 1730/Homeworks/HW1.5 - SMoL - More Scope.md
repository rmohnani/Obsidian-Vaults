**[Assignment](http://cs.brown.edu/courses/csci1730/2022/smol.html)**

# Task: [More Scope](https://script.google.com/a/macros/brown.edu/s/AKfycbyOWF819avuY6uh0PlP-GAVNCZc0xHucUuzgaJD8ZLng5b329uzM2jVsN1zJGMyk5PAgQ/exec?tutorial=more-scope&userId=rohit_mohnani)

```racket
#lang stacker/smol/fun

(defvar x 1)
(deffun (gety)
  (defvar y x)
  (defvar x 2)
  y)
(gety)

```

The answer is `error`.

The body of `gety` tries to bind `y` to the value of `x`. This `x` must refer to the `x` defined in the body of `gety` rather than the `x` defined in the top-level block. So `y` is NOT bound to `1`. However, the `x` in `gety` has not yet been bound to `2`, so the program errors.

> [!hint] 
> If there is a variable name in the scope that has not been defined yet but is referenced first, it cannot use an outer level scope's definition for that name. So it will error

> [!important] 
> > We find the declaration by looking in a series of blocks. We start with the block in which the variable reference occurs. If the variable is declared in the current block, we use that declaration. Otherwise, we look up the block in which the current block occurs, and so on recursively. (Specifically, if the current block is a function body, the next block will be the block in which the function definition is; if the current block is the top-level block, the next block will be the _primordial block_.) If the current block is already the primordial block and we still haven't found a corresponding declaration, the variable is unbound.
> > 
> > The **scope** of a variable is the region of a program where we can refer to the variable. Technically, it includes the block in which the variable is defined, and all sub-blocks of the block, _except_ the sub-blocks (not including the block itself) in which the same name is re-defined. When the exception happens, that is, when the same name is defined in a sub-block, we say that the variable in the sub-block **shadows** the variable in the outer block.
> > 
> > We say a variable reference (e.g., "the `x` in `(+ x 1)`") is **in the scope of** a declaration (e.g., "the `x` in `(defvar x 123)`") if and only if the former refers to the latter.

