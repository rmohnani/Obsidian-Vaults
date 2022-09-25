**[Assignment](https://cs.brown.edu/courses/csci1730/2022/analysis.html)**
# Task 1: [Steppers](https://cs.brown.edu/courses/csci1730/2022/steppers.html)
https://brown.co1.qualtrics.com/jfe/form/SV_4Vo2TdPDwFHw5kW
![[Screen Shot 2022-09-25 at 5.31.37 PM.png]]

The Stacker uses color coding to distinguish between the different types of things happening in a a program's execution. The Stack has its own blocks which show the different function calls, what is waiting to be executed, and the environment frame it is in. The blue block tells the user what piece of code is being evaluated and in which frame. The green blocks list all the different environment frames that have been opened and the different variables that exist in them and their bindings to values. The light green blocks represent functions and show how functions are stored differently from variables, and in which environment the function was created and thus when called in which it'll be executed in. Until eventually the program terminates successfully or errors and crashes.

![[Screen Shot 2022-09-25 at 5.49.36 PM.png]]

I wonder whether all the environment numbers are accurate to how the computer actually creates and organizes its various environments or whether they are just random abstractions to contextualize how environments are related to each other. I also wonder whether functions are actually stored in a different manner or whether that's just a visual distinction to help the user better organize and separate what's going on. I also wonder all variables are initialize to some 'bad-value' similar to bomb or whether they are unbinded and the bomb is again a visual choice. 



# Task 2: [Dynamic Scope](https://cs.brown.edu/courses/csci1730/2022/dyn-scope.html)


