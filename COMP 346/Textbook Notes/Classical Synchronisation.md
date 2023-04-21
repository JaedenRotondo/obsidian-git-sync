## 6.4 Hardware support for synchronisation 
---
- As discussed in the section about deadlock, the process in which code is executed might be reordered by processors, which can lead to problems of symchronizaiton
	- One solution for this is the use of test_and_set() which acts as an atomic statement. 
		- If two processors try to execute a test_and_set() at the same time, they will execute in a random order one after the other
- The compare_and_swap() instruction (CAS), just like the test and set() instruction, operates on two words atomically, but uses a different mechanism that is based on swapping the content of two words.
	- We did not go over the implementation in class so i left this out?? 
## 6.6 Semaphores
- Implementation of signal(S)
```Java
wait(S){
	while(S <= 0)
		; // busy wait 
	S--; // decrement 
}
```
- Implementation of wait(S)
```Java 
signal(S){
	S ++; //incremement
}
```
- The counting (general) sempahore has an unrestricted domain 
- While the binary semaphore is restricted between 0 and 1 
- In a single-processor environment we can solve the mutual exclusion problem by simply inhibiting interrupts during the time the wait() and signal() operations are executing.