[**Assignment**](https://cs.brown.edu/courses/csci1730/2022/loops.html)

# Tasks
## 1.1
```python
button_list = []

for i in range(10):
    button = lambda: print(i)
    button_list.append(button)

for button in button_list:
    button()
```

Output: `9 9 9 ... 9`

```java
import java.util.*;

class Buttons {

    public static interface Button {
        void press();
    }

    public static void main(String[] args) {

        List<Button>buttonList = new LinkedList<>();

        for(int i = 0; i < 10; i++) {
            // Uses Java8's new lambda syntax
            Button b = () -> System.out.println(i);
            b.press();
            buttonList.add(b);
        }

        for(Button b : buttonList) {
            b.press();
        }
    }
}
```

Output: 

```
Main.java:15: error: local variables referenced from a lambda expression must be final or effectively final
            Button b = () -> System.out.println(i);
                                                ^
1 error
Error: Could not find or load main class Main
Caused by: java.lang.ClassNotFoundException: Main
```


```racket
#lang racket

(define button-list
  (for/list ([i (in-range 0 10)])
    (lambda () (println i))))
 
(for ([button button-list])
  (button))
```

Output: `0 1 2 ... 8 9`

## Q1 - What Happens?
Try your best to explain what might be going on behind the scenes that causes these differences. _Remember to cite your sources, if applicable._

For Python it seems like the `i` passed to the print statement in the lambda function is not evaluated and passed by value, but is instead passed by reference. So that when i changes
and we create a new lambda for a new button, the i in the old lambdas also change or at least are not evaluated yet. This until we exit the for loop and i goes out of scope so that they need to be evaluated. Right before i goes out of scope it has the value 9, so all the lambdas evaluate i to 9, so when the buttons are called we get 9s.

For Java we get an error regarding the local variable i passed to the Button lambda function. 