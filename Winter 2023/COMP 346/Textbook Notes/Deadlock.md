--- 
## Chapter 6.1 

- A solution to the critical section problem must satsify the following 3 requirements: 
	1. Mutual Exclusion: If P1 is exectuing in the critical section, no other processes can be exectuing in their critical sections
	2. Progress: If no process is executing its critical section and some processes wish to enter, then they cannot be postponed indefinetly 
	3. Bounded waiting: There exists a bound on the number of times that other processes are allwed to enter their critical section after a process has made a request to enter its critical section before that request is granted
## Chapter 6.2 _The Critical-Section Problem_
- Disabling interrupts is not a feasable solution in multiprocessor environments. 
- A nonpremptive kernel is obviously free of race conditions  
- Despite the drawbacks of the preemptive kernels, they are more suitable for real-time programming as it will allow real-time process to preempt a process currently running in the kernel. 
## Chapter 6.3
#### Peterson's Solution 
- An attempt ot solve the critical section problem
- It is not successful as a solution to the critical section problem when processors reorder read/write operations
	- Processors do this to speed up the overall processing time 
	- It usually isnt a problem (for exame reordering credit balances between addition and subtraction doesnt change the overall result) but its a problem when you assign values to variables as so: 
``` Java
boolean flag = false;
int x = 0;

// where Thread 1 performs the statements
while (!flag)
;
print x;
//and Thread 2 performs
x = 100;
flag = true;
```
	- thread 1 could see that flag is true but x is still 0, and print 0 when the expected outcome is 100. 
- _Peterson’s solution is restricted to two processes that alternate execution between their critical sections and remainder sections.
- Note the j = 1-i  
``` Java
int turn;
boolean flag[2];
while (true){
flag[i] = true;
turn = j;
while (flag[j] && turn == j)
	;
/* critical section */
flag[i] = false;
/*remainder section */
}
```
- Mutual exclusion is not held in petersons solutions if theres multithreading if there is instruction reordering like so: ![[Screenshot 2023-04-18 at 2.29.17 PM.png]]

