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
	    
	1.  Which of these correspond to classes, and why?
	    



**