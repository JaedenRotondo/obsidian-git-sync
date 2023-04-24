### Question # 1
> What are the main differences between the user-kernel threads models? Which one of these models is likely to trash the system if used without any constraints?
- The main difference between user and kernel thread models is their size. Kernel threads used without any constrints will likely trash they system. For example, although threads are comparatively lightweight than processes, creating 5000 kernel threads vs 5000 user threads will affect a system greatly. 
- Kernel threads are implmented by the operarting system (as opposed to users) and are therefore recognizeable to the kernel and require hardware support.
- Context swithcing kernel threads is more demanding than user threads. 
- Switching between user threads does not require supervisor privledges, but switching between kernel threads do. 
---
### Question # 2
> Why threads are referred to as “light-weight” processes? What resources are used when a thread is created? How do they differ from those used when a process is created?

- A thread is considered a "light-weight" process becuase they share memory from the process they are running in. This means that context switching between threads can be dones easily. The resources consumed by a thread when it is created is from theh resources of the larger process itself. 
- When a process is created, memory must be allocated (to MM) by the OS and are completely independent from each other. While threads use the same area of memory and are managed by a scheduler
- User level threads are treated as a single task by the operating system 

### Question # 3

Does shared memory provide faster or slower interactions between user processes? Under what conditions is shared memory not suitable at all for inter-process communications?
- Shared memory allows for faster interactions between user processes. This is because it does not incu the overhead from executing sysetm calls. Shared memory is not suitable for inter-process communications when you are in a distributed system and you require a network for inter-process communication
- Since shared memory requires that user processes access memory that is shared amongst processes, it means that memory can be deleted or overwritten in scenarios where it shouldnt be. This type of access can be dangerous in high security scenarios 

### Question # 4

#### a) Consider three concurrent processes A, B, and C, synchronized by three semaphores mutex, goB, and goC, which are initialized to 1, 0 and 0 respectively:
![[Screenshot 2023-03-16 at 2.29.46 PM.png]]
Does there exist an execution scenario in which: (i) All three processes block permanently? (ii) Precisely two processes block permanently? (iii) No process blocks permanently? Justify your answers.

- All three block permanently: Scenario:
	- Process C starts, the mutex is changed to locked (0) and process C waits for goC (locked). goC can only be signaled if Process B runs which will never because the mutex is never signaled. 

#### b) Now consider a slightly modified example involving two processes:
![[Screenshot 2023-03-16 at 2.24.54 PM.png]]
1.  (i)  Let m > n. In this case, does there exist an execution scenario in which both processes block permanently? Does there exist an execution scenario in which neither process blocks permanently? Explain your answers.
    - There is no deadlock in this code if Process A starts. Since process A will signal goB more times than Process B needs to run. 
    - If process B starts, it will never release the mutex to allow for signal(goB)
1.  (ii)  Now, let m < n. In this case, does there exist an execution scenario in which both processes block permanently? Does there exist an execution scenario in which neither process blocks permanently? Explain your answers.
    - If m < n, there is an obvious deadlock scenario, since wait(goB) requires a signal from process A, it cannot run more times than Process A. 
    - If process B starts, it will never release the mutex to allow for signal(goB)
    - In every scenario, process B will never finish executing 

### Question # 5

In a swapping/relocation system, the values assigned to the <base, limit> register pair prevent one user process from writing into the address space of another user process. However, these assignment operations are themselves privileged instructions that can only be executed in kernel mode.

Is it conceivable that some operating-system processes might have the entire main memory as their address space? If this is possible, is it necessarily a bad thing? Explain.

- The operating system processes need to have the entire main memory as their address space so that it can reach certain processes. This is a good thing for security purposes as well. 
### Question # 6

Sometimes it is necessary to synchronize two or more processes so that all process must finish their first phase before any of them is allowed to start its second phase. For two processes, we might write:
![[Screenshot 2023-03-16 at 2.25.24 PM.png]]

a) Give a solution to the problem for three processes P1, P2, and P3.  

b) Give the solution if the following rule is added: after all processes finish their first phase,

phase I, they must execute phase II in order of their number; that is P1, then P2 and finally P3.

### Question # 7

Generally, both P and V operation must be implemented as a critical section. Are there any cases when any of these two operations can safely be implemented as a non-critical section? If yes, demonstrate through an example when/how this can be done without creating any violations. If no, explain why these operations must always be implemented as critical sections.

### Question # 8

What is the potential problem of multiprogramming?

The potential problem of multiprogramming is that, since several processes will be running concurrently, mutual exclusion between the program data as well as allocation of resources which can result in deadlock becomes an issue. 