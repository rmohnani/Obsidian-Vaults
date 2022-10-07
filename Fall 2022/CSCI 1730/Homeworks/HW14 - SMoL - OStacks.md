[**Assignment**](https://docs.google.com/document/d/1TSguKP_MBOf03KyWZnlYC4Lk5-LPagdvtK29gRLiIoY/edit)

# Task 1: Basic Objects

```racket
#lang stacker/smol/hof

(deffun (o-state-2 init)
  (lambda (m)
    (if (equal? m "inc")
        (lambda () (set! init (+ init 1)))
        (if (equal? m "get")
            (lambda () init)
            -1730))))

(defvar o (o-state-2 5))
((o "inc"))
((o "get"))

```

Run this program through to completion.

1.  Provide a screenshot of your final configuration.

![[Screen Shot 2022-10-07 at 11.41.41 AM.png]]
2.  You should see four closures. Using the addresses in the above configuration:
    
	1.  Which of these correspond to objects, and why? 

		915 corresponds to the object because it follows the object pattern of a lambda followed by cases. This also makes sense as it is bound to o which is supposed to be the object in the code.
	    
	1.  Which of these correspond to classes, and why?
	
		o-state-2 corresponds to the class. This is because it has a lambda taking constructor params (here it is just init) which is then followed by the object pattern in 915, thus giving it the class pattern we've seen before.


# Task 2: Static Members


1.  Provide a screenshot of your final configuration.
	![[Screen Shot 2022-10-07 at 12.38.40 PM.png]]
2.  How many objects are created? Where are they located in your configuration (using the addresses in the above screenshot)

	2 Objects are created at addresses 324 and 430.

4. Trace through the configuration to show why counter behaves like a static.

	Whenever o-static-1 gets called (set! counter (+ 1 counter)) this is the first code that runs in the begin call. We can see the class closure at address 551. Comparing this to the object closures at 324 and 430 we see they are both missing this counter updating code. So whenever we call the class closure on some param to give us an object, we evaluate this counter updating once, meaning for every new object we create we increment counter by 1. and we can see it is static because it is in the same environment as the class closure 1033.


# Task 3: Dynamic Dispatch

1.  Provide a screenshot of the configuration at the point where the a-tree object has been initialized and before the method dispatch begins.
![[Screen Shot 2022-10-07 at 12.55.09 PM.png]]
2.  In the above configuration, point out which values represent mt and node objects. Do any values here correspond to classes? If so, which one(s) and why?

	Closure 134 represents an mt object, thus l,r in env 1055 and r in env 1356 are bound to mt objects. The node closure corresponds to the node class, because it follows class pattern of some variable set up in a let before returning a lambda (object). Closures 225 and 436 correspond to node objects/instances. Closure 225 corresponds to the node represented in env 1207 which rests at 1055 and tells us (v l r) = (5 mt mt). While closure 436 corresponds to node represented in env 1467 which rests at 1356 and tells us (v l r) = (10 nodeAt225 mt)
    
3.  Dynamic dispatch depends on objects having a consistent representation (this is the heart of “object polymorphism”: you can treat them interchangeably, and the differences in behavior are hidden inside the objects). In what way do these objects have a consistent representation?

	The consistent representation is that both node and mt objects have a defined method "sum" and have a variable self that points to the lambda that comprises their object pattern which is what both mt and node objects are then returning. So we can call "sum" on both objects but how a node object implements the sum method vs how an mt object implements the sum method is hidden inside the object. If one of them didn't implement this method, we would not be able to simply call sum, as we'd have to then account for let's say mt not having a sum and thus we'd have to define a function call to do this separate from the classes/objects themselves.


    
