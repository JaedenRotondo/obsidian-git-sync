# Concurrency and Erlang
## Concurrency vs parallelism 
- Concurrency refers to the concept of seperate threads of control/execution within a program 
- Parallel programs are those that support simultaneous execution of distincy instruction streams
	- By definition, they run on multiple CPU's or cores.
	- Typically, they are used to increase the perfomrance of a specific algorithm 
		- parallel sort!
- Concurrency programs can be run on a single core at a time.
	- They are usedf to divide the logic of a complex program into distinct units
- *all parallel programs provide concurrency, but concurrent programs are not necessarily parallel*
---
## Race conditions and critical regions 
- It can be very difficult to write concurrent programs correctly: primary problem is controlling access to shared data
	- If not *write-able* data is shared between the threads, then there are no problems
	- sharing read only data is never a problem
- The central problem is associated with what we call **race conditions**
	- When two or more threads must access and potentially update a data structure, it is possible that the final state of the data will depend on a *race* to the data
		- Because of this, the thread winning the race may update the data first, though the thread losing the race is likely to make the last update
- Here is the problem in application: 
  ![[Pasted image 20221213142852.png]]
### Criticial regions
- The code where updates are made are called "critical regions"
- Clearly, we must ensure that **only one thread at a time enters and exists the critical region... how do we ensure this? **
	- We use *locks*
---
## Locks
- In its simplest form, a lock is a variable that can be set to opne/closed (0/1)
	- So a lock is set at the start of the critical region and then released when this thread leaves the critical region
	- When a second thread encounters a closed lock, it must wait or "block" until the lock has been released
- There is one small complication with this model 
	- While setting a variable can be done with a single high level language instruction, this instruction is in fact compiled into multiple level isntructions 
	- This is problem because when application/threads are run, they are swapped on and off the CPU by the operating system
		- This is how we give the appearance of many application running simultaneously 
- The OS has not control over the exact machine level instruction that is currently executing 
	- So it is possible to swap a thread just after it reaches an open lock but just before it finalizes the action of updating a lock **(THIS IS BAD)**
- For this reason, all modern CPU instruction sets provide a special "test and swap instruction"
	- This is an atomic assignment that always completes
---
## Deadlock and Livelock
- This is all fine and dandy for trivial locks. Real application may consist of many threads and many shared data structures/critical regions
- This creates 2 kinds of problems
	1. **Deadlock**
		- This occurs when a thread A is waiting ofr a lock held by Thread B, while the thread B is wiating on a lock held by Thread A
			- This will cause the application to hang forever in this state
	2. **Livelock**
		- Threads contending for locks spend a great deal of time repeatedly relaeasing locks in order to make them available to one another, but not actually getting much work done
- Even when things work properly, a lot of time can be spent setting, releasing, and waiting for locks
	- This seriosly impacts the performance that was supposed to be gained!! 
---
## ALTERNATIVE: Message passing
- As we have seen, "low level" thread management does not scale very well
- One alternative (this is used by Erlang) is called *message passing*
- **message passing** consists of a set of message queues associated with individual processes or tasks 
	- Data is not shared directly, instead information is sent to and recieved from each process
		- These messages are placed into a queue of messages that the process can examine
		- Messages have a sender ID and a "tag" to identify message type
---
## Asynchronous communication 
- Messages can be viewed as *asynchronous* 
	- sending and recieving processes do not block during transfer, so sending and recieving are "decoupled"
- Note that it is still possible for a process to hang when using message passing
	- You can explicitly wait for a message from a task that has crashed
		- This is not a true deadlock and can be adressed by the programmer
---
