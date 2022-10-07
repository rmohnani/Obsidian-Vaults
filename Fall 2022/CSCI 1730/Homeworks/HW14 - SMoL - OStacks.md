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

	
