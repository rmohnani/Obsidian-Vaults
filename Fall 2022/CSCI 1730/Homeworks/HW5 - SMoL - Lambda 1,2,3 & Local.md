**[Assignment](https://cs.brown.edu/courses/csci1730/2022/smol.html)**

11:02 - finished lambda 1 in PL now
12:48 - start lambda 2
13:09 - finished lambda 2
15:36 - start lambda 3
15:56 - finished lambda 3
16:43 - finished local

# Tasks
## Task 1: [Lambda 1](https://script.google.com/a/macros/brown.edu/s/AKfycbyOWF819avuY6uh0PlP-GAVNCZc0xHucUuzgaJD8ZLng5b329uzM2jVsN1zJGMyk5PAgQ/exec?tutorial=lambda1&userId=rohit_mohnani)
```racket
#lang stacker/smol/hof

(deffun (double x)
  (+ x x))
(defvar f double)
(f 2)
(f 3)

```

> [!attention] 
> It binds `double` to a function and `f` to _the value of `double`_, which is the function. Because `f` is bound to a function, it can be called. So this program produces `4 6`.
> Note: some programming languages (e.g., Java) do NOT consider functions or methods a kind of value. But many programming languages, from Python to Rust, do.
> Functions are values. So they can also go in vectors.

> [!important] 
> Functions are values. Therefore, variables (notably parameters) can be bound to functions, functions can return functions, and vectors can refer to functions.

## Task 2: [Lambda 2](https://script.google.com/a/macros/brown.edu/s/AKfycbyOWF819avuY6uh0PlP-GAVNCZc0xHucUuzgaJD8ZLng5b329uzM2jVsN1zJGMyk5PAgQ/exec?tutorial=lambda2&userId=rohit_mohnani)

> [!note] 
> Functions remember the environment that they refer to. Function values are called _closures_ because function bodies are enclosed by the environments in which the function values are created.

## Task 3: [Lambda 3](https://script.google.com/a/macros/brown.edu/s/AKfycbyOWF819avuY6uh0PlP-GAVNCZc0xHucUuzgaJD8ZLng5b329uzM2jVsN1zJGMyk5PAgQ/exec?tutorial=lambda3&userId=rohit_mohnani)

> [!important] 
> You have seen that functions are values. Currently, the only way to create a function is by `deffun`. But this should not be the only way. `deffun` creates a function _and_ binds it to a variable. You just saw that we can just _bind_ functions using `defvar`. Similarly, we can just _create_ functions, using `lambda`.

> [!note] 
> `(deffun (f x ...) body)` is a shorthand for `(defvar f (lambda (x ...) body))`


## Task 4: [Local](https://script.google.com/a/macros/brown.edu/s/AKfycbyOWF819avuY6uh0PlP-GAVNCZc0xHucUuzgaJD8ZLng5b329uzM2jVsN1zJGMyk5PAgQ/exec?tutorial=local&userId=rohit_mohnani)

> [!note] 
> _local binding forms_: `let` and `letrec` and `let*`.
> In general, `let` binds the _left-hand-side variables_ (in this case, `x` and `y`) to the values of the _right-hand-side expressions_ (in this case, `2` and `(+ 2 1)`) such that the _body_ (in this case, `(+ x y)`) can refer to all those left-hand-side variables.
> Furthermore, the bindings are _local_, which means we can't refer to the `let`-bound variables outside the `let`.

> [!note]
> A `let` expression binds its left-hand-side variables such that its body is in the scope of all the variables.
> (Recall that the scope of a variable is the region of a program where the variable can be referred to.)

```
#lang stacker/smol/hof

(let ([x 123]
      [getx (lambda () x)])
  (getx))

```

The scope of `x` only includes the `let` body (i.e., `(getx)`) and does NOT include any of the right-hand-side expressions (i.e., `123` and the `lambda` expression). So the `x` in the `lambda`
expression is undefined.

> [!important] 
> In a `let`, the scope of a left-hand-side variable includes _none_ of the right-hand-side expressions.
> 
> ![[Screen Shot 2022-09-16 at 4.36.49 PM.png]]

> [!important] 
> In a `letrec`, the scope of a left-hand-side variable includes _all_ of the right-hand-side expressions.
> ![[Screen Shot 2022-09-16 at 4.39.19 PM.png]]

```racket
#lang stacker/smol/hof

(deffun (double n)
  (* n 2))
(deffun (add1 n)
  (+ n 1)) 

(let* ([x 0]
       [x (add1 x)]
       [x (double x)])
  (+ 3 x))

```

This program will error because none of the right-hand-side expressions can refer to `x`. Replacing `let` with `letrec` will NOT fix the error. 

> [!important]
> Recall that in a `letrec`, the scope of a left-hand-side variable includes _all_ of the right-hand-side expressions. To achieve this while avoiding confusion, `letrec` insists that all left-hand-side variables must be distinct. (`let` also has this restriction, but for a different reason.)



If we replace `let` with `let*`, this program will produce `5`, the value of `(+ 3 (double (add1 0)))`. `let*` allows you to do a series of bindings sequentially.

Let's summarize the scoping rules of `let*`. After that, we will do a handful of exercises to test your understanding of `let`, `letrec`, and `let*`.


> [!important] 
> In a `let*`, the scope of a left-hand-side variable includes _all of the subsequent_ right-hand-side expressions.
> ![[Screen Shot 2022-09-16 at 4.41.28 PM.png]]



