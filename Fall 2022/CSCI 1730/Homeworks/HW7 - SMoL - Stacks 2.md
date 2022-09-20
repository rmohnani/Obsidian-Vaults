**[Assignment](https://cs.brown.edu/courses/csci1730/2022/smol.html)**


# Task: [Stacks 2](https://docs.google.com/document/d/16Sw5XIBENvhqV9g4EMiDGczOjwwypF8x7uYwKc9HQYU/edit)

## Question 1
**![](https://lh6.googleusercontent.com/BQJL1lDjt8ZvY06GfC_22rCLOW4AeKa_e_Jkh-HkUmHMlaP2pr14qHBduSEmy2ThvbAFSzV1lB_xDEGTBgPsQKhTLOuzpliiHOCMm1k6JUGKa6otltU6973mb3ohOnPASGKaZJeK-0bs7_0zLkaO_aJsvudBrKyfSqieWtc9J4_yv5TDSkoJgMzrIQ)**

```racket
#lang stacker/smol/fun
; #:no-trace

(deffun (pause) 0)

(defvar v0 0)
(defvar v1 (mvec 1))
(defvar v2 (mvec v1))
(set! v0 (mvec v1 v2))

(vec-set! v1 0 v2)
v0
(pause)
```

- The bindings in env 1502 tell me I need to define 3 variables v0, v1, v2 in that order, and that they ultimately need to be assigned to vectors.
- The order of the mvec environments tell me that the order vector creation is v1,v2,v0
- The mvec envs tell me v1 and v2 both have one element which is set to the other vector. And that v0 has 2 elements, 1st is v1 and 2nd is v2.
- From the yellow stack env 1502, the 2 `#<void>` tell me I use a set! or vec-set! in total twice.
- The vector location in the stack tells me I call v0 before I call pause which is what is being evaluated and returned in the blue block.



