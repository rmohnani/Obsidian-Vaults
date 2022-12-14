**[Assignment](https://cs.brown.edu/courses/csci1730/2022/analysis.html)**
# Task 1: [Steppers](https://cs.brown.edu/courses/csci1730/2022/steppers.html)
https://brown.co1.qualtrics.com/jfe/form/SV_4Vo2TdPDwFHw5kW
![[Screen Shot 2022-09-25 at 5.31.37 PM.png]]

The Stacker uses color coding to distinguish between the different types of things happening in a a program's execution. The Stack has its own blocks which show the different function calls, what is waiting to be executed, and the environment frame it is in. The blue block tells the user what piece of code is being evaluated and in which frame. The green blocks list all the different environment frames that have been opened and the different variables that exist in them and their bindings to values. The light green blocks represent functions and show how functions are stored differently from variables, and in which environment the function was created and thus when called in which it'll be executed in. Until eventually the program terminates successfully or errors and crashes.

![[Screen Shot 2022-09-25 at 5.49.36 PM.png]]

I wonder whether all the environment numbers are accurate to how the computer actually creates and organizes its various environments or whether they are just random abstractions to contextualize how environments are related to each other. I also wonder whether functions are actually stored in a different manner or whether that's just a visual distinction to help the user better organize and separate what's going on. I also wonder all variables are initialize to some 'bad-value' similar to bomb or whether they are unbinded and the bomb is again a visual choice. 

![[Screen Shot 2022-09-25 at 5.57.06 PM.png]]

The Python Tutor makes two broad separations in whats going on in program execution. One side is frames which are the environments in which execution is taking place. The other side is objects, which include functions among other things. Python tutor has all the variables inside the frame in which they are created, it also has arrows to point from some variable to an object. The frame in which we are in is coloured blueish, while frames that are no longer used are greyed out. The creation of arrows shows how objects are created and which ones are referenced from which variables.

![[Screen Shot 2022-09-25 at 7.53.18 PM.png]]

I wonder what happens to the frames that are greyed out. Because they are still used in this case for example when the function is called, as those local frames that were created have the environment in which the func is supposed to execute. I wonder if all variables store pointers to where the object is stored in memory of if they store the object itself. 

![[Screen Shot 2022-09-25 at 7.55.34 PM.png]]

I think the stacker makes it more explicitly obvious what is going on, the colour coding is great because it organizes what's going on well, so you can isolate different areas of program execution and more readily tell whats going on. Whereas with the Python tutor, I think more dots have to be connected mentally to get the same picture the stacker is doing. In some ways Python tutor is more simple and doesn't burden you with more knowledge about stack frames and context of execution etc, so having only two broad categories boils down what is happening to the minnimum which is also helpful. I also liked how th python tutor greyed out environment frames, after we were 'essentially' done with them.

![[Screen Shot 2022-09-25 at 8.45.50 PM.png]]

I like the stacker quite a lot for the reasons stated above. There's nothing I immediately dislike about it.

![[Screen Shot 2022-09-25 at 8.47.19 PM.png]]

I liked how Python tutor focused on just these two general areas, and didn't burden you with more knowledge than you maybe want. I like the use of arrows for variable referencing an assignment and i think seeing how those arrows are generated and change over time is incredibly insightful. I wish there was more colour coding, because I think that would make it more engaging and probably easier to look at and parse like the stacker at a glance.

![[Screen Shot 2022-09-25 at 8.48.57 PM.png]]

I would recommend the stacker if one wants a more thorough understanding of stack frames and variable bindings, what is in context of a function etc. Basically if you want more complete and thoroughly detailed information on whats actually going on in execution use the stacker. I think the python tutor is good for someone who just wants to seee what is happening in the code without the extraneous details of stack frames etc, for someone who just wants to get the jist of what each line is doing.



# Task 2: [Dynamic Scope](https://cs.brown.edu/courses/csci1730/2022/dyn-scope.html)


