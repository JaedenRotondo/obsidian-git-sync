# Chapter 6:  
---
## Section 6.1 Background
- Here is a counter example which shows the problems of concurrency within critical sections: 
![[Screenshot 2023-02-11 at 1.57.43 PM.png]]
> situation like this, where several processes access and manipulate the same data concurrently and the outcome of the execution depends on the particular order in which the access takes place, is called a **race condition**.
- The importance of *process synchronization* and *coordination* has gotten more important since multicore systems (which are more popular now) encourage multithreaeded applications, and since multithreaded applications allow for threads to work in parallel. 
---
## Section 6.2 The Critical Section Problem
- The critical section problem is usually understood in the following code block format: 
```
while (true){
	*entry section*
		critical section
	*exit section*
	    remainder section
    }
```
---
## Section  6.5
---
## Section 6.8
---
