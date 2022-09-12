**[Assignment](http://cs.brown.edu/courses/csci1730/2022/smol.html)**

13:03 - Finished MutVec 1
13:28 - Finished MutVec 2
13:32 - Finished Heap Structure

# Tasks

## Task 1: [MutVec 1](https://script.google.com/a/macros/brown.edu/s/AKfycbyOWF819avuY6uh0PlP-GAVNCZc0xHucUuzgaJD8ZLng5b329uzM2jVsN1zJGMyk5PAgQ/exec?tutorial=vectors1&userId=rohit_mohnani)

> [!note] 
> Mutable vectors are created with `mvec`.
> Vectors are printed as `#(...)`, where `...` is the content of the vector. Only the outer-most vector is prefixed with `'`.


```
(mvec 1 2 3)
'#(1 2 3)
```

Vectors are printed like this with a `#` in front of them


> [!note] 
> `vec-len` computes the length of a vector.

> [!note] 
> `(vec-ref v i)` gets the `i`-th element of the vector `v`. The left-most element is the 0-th element.

> [!note] 
> `vec-set! vector index_to_change new_value` is syntax for how to mutate a vector

> [!note] 
> An `mpair` is a mutable vector of length 2, and vice versa. The two elements are referred to as the left and the right element respectively. Pair operations are shorthands of their vector equivalents. For example, `(left pr)` is `(vec-ref pr 0)` and `(set-right! pr 123)`) is `(vec-set! pr 1 123)`.

## Task 2: [MutVec 2](https://script.google.com/a/macros/brown.edu/s/AKfycbyOWF819avuY6uh0PlP-GAVNCZc0xHucUuzgaJD8ZLng5b329uzM2jVsN1zJGMyk5PAgQ/exec?tutorial=vectors2&userId=rohit_mohnani)

> [!caution] 
> `x` is bound to a vector (let's call it `@100`). `y` is bound to the value of `x`, which is the _same_ vector (`@100`). That is, the vector is _not_ copied. The `vec-set!` mutates the same vector, `@100`.

> [!important] 
> In general, each vector has its own unique _heap address_ (e.g., `@100` and `@200`). The mapping from addresses to vectors is called the _heap_.
> The heap is a collection of vectors. Each vector has its own unique address.

(**Note**: we use `@ddd` (e.g., `@123`, `@200`, and `@100`) to represent heap addresses. Heap addresses are _random_. The numbers don't mean anything.)

```racket
(defvar mv (mvec 3))
(defvar mv2 (mpair mv mv))
(vec-set! (left mv2) 0 42)
```

The first `mvec` call creates a 1-element vector, `@100`. The only element is `3`. The second `mvec` call creates a 2-element vector, `@200`. Both elements of `@200` are `@100`. So far, **A** best describes the heap.

However, the subsequent `vec-set!` mutates `@100` (the left element of `@200`). The 0-th element of `@100` is mutated to `42`. So **D** is the correct answer.

`@100 = #(42); @200 = #(@100 @100)`

> [!important] 
> -   A vector can be referred to by more than one variable and even by other vectors. A vector might even refer to itself.
> - As before, function calls bind the formal parameters to the actual parameters. So, for example, if `x` is bound to a vector then `(f x)` will be processing the same vector. That is, vectors are not copied during function calls. Similarly, other forms of binding (e.g., `defvar`) don’t copy vectors either. The only way to create new vectors is by `mvec`.

> [!note] 
> -   Creating a vector does not inherently create a binding (in the environment).
> - Creating a binding (in the environment) does not necessarily alter the heap.

## Task 3: [Heap Structure](https://script.google.com/a/macros/brown.edu/s/AKfycbyOWF819avuY6uh0PlP-GAVNCZc0xHucUuzgaJD8ZLng5b329uzM2jVsN1zJGMyk5PAgQ/exec?tutorial=heap&userId=rohit_mohnani)
