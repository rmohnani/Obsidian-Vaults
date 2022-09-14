**[Assignment](http://cs.brown.edu/courses/csci1730/2022/smol.html)**

10:05 - start 


# Task: [Stacks 1](https://docs.google.com/document/d/18i4er7B5-bE90LDP2VvYh0OkdfvWJ_08Stxx9bQ2bcM/edit)
## Configuration -> Program
### Question 1

![](https://lh4.googleusercontent.com/EujG_gHjAJYvKKch20k4rDlzgTgwd9ev4YyZBcSnSGbai2nJ0IMt-YCcMmE_bvq1ZKKoQg9IRwQnM2IPvYNWhNoAMsO-L4cAUndhyxgTd1zFXZ2st0aNs0PdFaQSeTg9RQfP8RDTXJ1vxivnyzEjMozY3DGM44cdCjNLEz7auNS1p4c0NzK7GmbO-A)**

```racket
#lang stacker/smol/fun
; #:no-trace

(deffun (pause) 0)

(deffun (top)
  (defvar x 3)
  (+ (inner_1) x)
  )

(deffun (inner_1)
  (defvar y 6)
  (+ (pause) y)
  )

(top)

```


### Question 2

![](https://lh6.googleusercontent.com/gfETfwUl-udJHUsfXpF6kGiLJIAMWzHH1oIwjy3TEG7DMaORjrvr0v07mKAvBXMBmv1Ez-QWwe7FMsbx8LnuuU6hKDjmaDzHplYv8HMCRBDIaWYkQMGaVjNfN8AJ-WpC6Ooac2kw51g9b7Foxv84hxse5b3FF4BZZJtJQjKg5XKxKxXdRzHLwh65SA)

```racket
#lang stacker/smol/state
; #:no-trace

(deffun (pause) 0)

(defvar v1 (mvec 1))
(defvar v2 (mvec 2))
(vec-set! v1 0 v2)
(vec-set! v2 0 v1)

(pause)
```

## Configuration -> Value

### Question 3
![](https://lh6.googleusercontent.com/qBGQ4Wm9rOEzY6O1oG5XjLSgZHDWn7fgZrymlO_2Su2t25dwty0BwePHkjl1WA1rYi8nRH-z1h1P0vY88z-FoIsADzV3p5qb2eCza0o7l_GldSI3jiAbegC11nc6ylCIvA1xKZrV7PWe9WqBT5uBxmig2PNoP5-IslG8bok6lrVyg9JXk1fN_vW3wA)

The value returned to context in environment 1013 is 0. so (- 0 (- x 2)) evaluates to (- 0 (- 4 2)), because x is bound to 4 in env 1013, thus we get (- 0 2) = -2. So -2 is the value returned to the context in env 1668 and the expression to evaluate is (+ -2 (+ y 4)). But y in in env 1668 is bound to 6, so we get (+ -2 (+ 6 4)) = (+ -2 10) = 8. So 8 is returned to the context in env 1467 and we have to evaluate (+ 8 x), but x in env 1467 is bound to 3, so we get (+ 8 3) = 11. So 11 is returned to context in env 1555, which is empty and thus the answer returned is 11.

### Question 4
![](https://lh5.googleusercontent.com/IuBS_2FAhEM65mIEJQDrBCELytxZmWF8wa982nOMPvNRYN2NhJtu5yibhqCiZbeBkemhMOwuqFKECiFdW0gC6hxra28CU8PWTn3k7uj0vXe2S35s_StTsGnhdN7UFbhkU-3M1Ux_pQ2L5fCPDgeY1apkxIA-odQsnSiKKsiHxxaypAdtpC635it4gA)

The value returned to context in env 1838 is 0. So the expression we need to evaluate is (+ 0 x), but x in env 1838 is bound to 2, so we have (+ 0 2) = 2 which is then returned to the context in env 1092. So we need to evaluate (+ 4 2 y), but y in env 1092 is bound to 5. So the expression we need to evaluate is (+ 4 2 5) = 11, which is then returned to the context in env 1964. So we now need to evaluate (+ 11 x), but x in env 1964 is bound 3, so we have (+ 11 3) = 14, which is then returned to context in env 1268. But this context is empty so the value returned is 14.

