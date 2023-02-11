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

- A solution to the critical section problem must satisfy 3 elements
1. **Mutual Exclusion**: If one process is executing a critical section, no other process should be able execute that same critical section 
2. **Progress**: If no process is executing in its critical section and some processes wish to enter their critical sections, then only those processes that are not executing in their remainder sections can participate in deciding which will enter its critical section next, and this selection cannot be postponed indefinitely.
3. **Bounded Waiting**: If a thread wishes to enter a critical section, there must be a bounded amount of time in which the thread will be granted access if other threads are in the critical section. 
---
## Section  6.5 Mutex Locks
- MutEx stands for *Mutual eclusion* 
- Boolean Available() to determine if the mutex lock is free or not
- Acquire(): Simply acquires the lock. Equivalent to Wait()... (Spinlock mutex implementation)
```Java
acquire() {  
	while (!available)
	    ; /* busy wait */
    available = false;
}
```
- Release(): Realeses the lock. Equivalent to Signal()
```Java
release() { 
	available = true;
}
```
- The main disadvantage of this system (a spinlock) is that it requires "busy waiting" 
	- While a another process is in a particular critical section, a process which is locked out must simply loop continuosly in calling acquire(). 
	- This wastes CPU cycles that other processes could be using more effeciently 
- Spinlocks have their benefits as well: They do not require context switching. Context switching might take longer than just a couple of spins and is therefore used on many systems today. 
---
## Section 6.8 Liveness 
- One major issue that needs to be addressed in synchronisation is the scenario where a process which wants to enter a critical section will never be able to. There are 2 main types of *liveliness failures*
### 6.8.1 Deadlocks
- Examine the following situation: 
```Java
// P0
	wait(S);
	wait(Q);
	.
	.
	signal(S);
	signal(Q);
```
```Java
//P1
	wait(Q);
	wait(S);
	.
	.
	signal(Q);
	signal(S);
```
- In this situation we have a deadlock: Suppose P0 executes wait(S) and P1 executes wait(Q). Then, P0 wishes to wait(Q) but is blocked till P1 wait(S) which will not be granted. 
	- Essentially, both processes are waiting for each other to continue 
### 6.8.2 Priority Inversion
- We haven't learned this in class yet
> A scheduling challenge arises when a higher-priority process needs to read or modify kernel data that are currently being accessed by a lower-priority process—or a chain of lower-priority processes. Since kernel data are typi- cally protected with a lock, the higher-priority process will have to wait for a lower-priority one to finish with the resource.