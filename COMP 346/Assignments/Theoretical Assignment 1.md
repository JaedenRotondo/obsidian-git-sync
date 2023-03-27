## Question # 1

1.  What is an operating system? What are the main purposes of an operating system?
    - Operating system is software. it is the programming always running on the system. It allows applications to connect witht the computer hardware. The operating system provides serveral services to the user including a user itnerface, I/O device management, program exectuions, file-process management, etc. 
2.  Define the essential properties of the following types of operating systems:
    • Batch  
	    - A batch system is a type of operating system that takes a batch file of jobs and executes them sequentially
    • Time sharing  
	- With several users, a time shairng system allocates CPU time to many processes in a fair and quick manner, with a single host. 
    • Dedicated  
	    - A dedicated operasting system is one that is created for a particular device, as oposed to a general purpose operating system 
    • Parallel  
	    - Parallel refers to processes which run in parallel to each other, which is a form of concurrency. This requires a multi processor system (2 or more central processing units)
    • Multiprogramming
	    - An operating system that is able to run more than a single program, or what we call processes. Several processes will run on the CPU
1.  Under what circumstances would a user be better of using a time-sharing system rather than a PC or single-user workstation?
- When there is a lack of resoruces, or when instead of having individual computers it is more cost effects ot have a single large computer. It might also be beneficial for large computational programs where a single user workstation is not a viable option. 

## Question # 2 skipped

Consider a computer system with a single-core processor. There are two processes to run in the system: P1 and P2. Process P1 has a life cycle as follows: CPU burst time of 15 units, followed by I/O burst time of minimum 10 units, followed by CPU burst time of 10 units. Process P2 has the following life cycle: CPU burst time of 10 units, followed by I/O burst time of minimum 5 units, followed by CPU burst time of 15 units. Now answer the following questions:

| Type | p1 | Type | p2 |
|------|----|------|----|
| CPU  | 15 | CPU  | 10 |
| I/O  | 10 | I/O  | 5  |
| CPU  | 10 | CPU  | 15 |


1.  a)  Considering a single programmed operating system, what is the minimal total time required to complete executions of the two processes? You should explain your answer with a diagram.
- Since we are using a single process system, there is no possibility of context switching and the minimum execution time will be the sum of all the processes regardless of whether they are CPU or I/O 
$$T = p1 + p2 = (15 + 10 + 10) + (10 +5 + 15) = 65 \ units  $$
1.  b)  Now considering a multiprogrammed operating system, what is the minimal total time required to complete executions of the two processes? You should explain your answer with a diagram.
- Since we are using a multiprocessing system, we can assume that th I/O device execution times can be yielded to the other process in the following *minimal* order: Max(P1, P2) = 35 Units

c) Throughput is defined as the number of processes (tasks) completed per unit time. Following this definition, calculate the throughputs for parts a) and b) above. How does multiprogramming affect throughput? Explain your answer.
- Throughput for single processor system: 2/65
- Throughput for dual processeor system 2/35

## Question # 3

I. What is the performance advantage in having device drivers and devices synchronize by means of device interrupts, rather than by polling (i.e., device driver keeps on polling the device to see if a specific event has occurred)? Under what circumstances can polling be advantageous over interrupts?
- Device interrupts used to synchronize devices rather than polling allows for the processing unit to work on other tasks while the I/O device is working. If there is just polling, the computer will have to busy wait until the external process is complete. 
- There are certain circumstances where polling is better than interrupts. Performing storage I/O with ultra-low latency devices with fast memory with polling till copmletion (running clock cycles) is faster than interrupts, especially due ot the time it takes to context switch on large systems. 
II. Is it possible to use a DMA controller if the system does not support interrupts? Explain why.
- no because direct memory access involves the CPU in the transfer of memory. It utilizes the bus directly but is still interupted after every block (instead of every byte)
IV. The procedure ContextSwitch is called whenever there is a switch in context from a running program A to another program B. The procedure is a straightforward assembly language routine that saves and restores registers, and must be atomic. Something disastrous can happen if the routine ContextSwitch is not atomic.

(a) Explain why ContextSwitch must be atomic, possibly with an example. (b) Explain how the atomicity can be achieved in practice.
- (a) Atomicity of context switching is incredibly important because, if it were not the case, the information within the registers duiring a context switch need to be transferred to the main memory. If this is not done to completion and the registers are overwritten prior to the transfer- data will be lost
- (b) Atomocity can be achieved in practice with the "disable interrupt" functionality. Disable interrupt tells the cpu that during the critical section of a program, it cannot be halted until completion 
## Question # 4

1.  If a user program needs to perform I/O, it needs to trap the OS via a system call that transfers control to the kernel. The kernel performs I/O on behalf of the user program. However, systems calls have added overheads, which can slow down the entire system. In that case, why not let user processes perform I/O directly, without going through the kernel?
    - The main reason why things are performed through the kernel and not directly via the  user processes because that would be a security issue. Instead, supervision via a mode bit allows for the kernel space to be entered for short and monitored periods of time. On top of this, certain actions (errors, either malicious or unintentional) should not be granted to the user unless authorized. 
2.  Consider a computer running in the user mode. It will switch to the monitor mode whenever an interrupt or trap occurs, jumping to the address determined from the interrupt vector.
    1.  (a)  A smart, but malicious, user took advantage of a certain serious loophole in the computer's protection mechanism, by which he could make run his own user program in the monitor mode! This can cause disastrous effects. What could have he possibly done to achieve this? What disastrous effects could it cause?
        - yielding and intering monitor mode? Creating several threads and yielding to a different thread - executing in monitor mode? 
    2.  (b)  Suggest a remedy for the loophole.


## Question # 5

Suppose that a multiprogrammed system has a load of N processes with individual execution times of t1, t2, ...,tN. Answer the following questions:

a) How would it be possible that the time to complete the N processes could be as small as: maximum (t1, t2, ...,tN)?

b) How would it be possible that the total execution time, T > t1+ t2+ ...+tN? In other words, what would cause the total execution time to exceed the sum of individual process execution times?

## Question # 6

Which of the following instructions should be privileged? Explain why. (i) Read the system clock,  
(ii) Clear memory,  
(iii) Reading from user space

(iv) Writing to user space  
(v) Copy from one register to another (vi) Turn off interrupts, and  
(vii) Switch from user to monitor mode.

## Question # 7

Assume you are given the responsibility to design two OS systems, a Network Operating System and a Distributed Operating System. Indicate the primary differences between these two systems. Additionally, you need to indicate if there any possible common routines between these systems? If yes, indicate some of these routines. If no, explain why common routines between these two particular systems do not make sense.
- A distributed system is a system of physcially seperate computers which are networked together to allow users to use resources that are shared amongst that network. On the other hand, a network operating system allows for sharing materials through a network but acts autonomously from these computers. A distributed system creates a less autonomous environment where there is only the illusion that there exists a single operating system that controls the network. Additionally, a distributed system nodes share the same operating system, while in a network operating system each node has its own operating system. 
- There are common routines between these systems, since they both provide connectivity via TCP/IP networking protocols, but the similarities are few. 
- Examples of networking operating systems include both Peer to Peer (P2P) and Server/Client operating systems. These systems share information on the basis of file exchange while distributed systems share information on the bases of message passing and shared memory. 