Semaphors: 
Wait(): checks if the semphore value is zero... if so it will not allow entry into the critivcal zero
- if greater than zero (no process in the c.s.) it will let the process enter the critical section 
- Whenever a process wants to enter the critical section, it will call wait. It will decrement the variable possibly to zero where another process will therefore be blockers

Signal(): After a c.s. is finished in exection, it will increment the value of the semaphore integer. This makes it possible for other threads to enter the c.s. 

- Counting semphore: multiple instances of a c.s. multiple processes can enter a c.s.
- Notify(): will wake up the other thread for use of a critical section 
- Explain how we can use semphors for multiple drinkers 
- Thread.sleep() - context switch could happen but not when you have semaphors 
- barrier sync for 3 processes
	- We need to vreate a semohore for each process 
		- There is a high possibility of deadlock in this situaiton 
- General solution: still a topic of research today 
- Semaphore.acquire is the java implementation of wait 