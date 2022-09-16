**[Assignment](https://cs.brown.edu/courses/csci1730/2022/smol.html)**

11:02 - finished lambda 1 in PL now
12:48 - start lambda 2
13:09 - finished lambda 2
15:36 - start lambda 3
15:56 - finished lambda 3

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


## Task 4: [Let](https://script.google.com/a/macros/brown.edu/s/AKfycbyOWF819avuY6uh0PlP-GAVNCZc0xHucUuzgaJD8ZLng5b329uzM2jVsN1zJGMyk5PAgQ/exec?tutorial=local&userId=rohit_mohnani)





