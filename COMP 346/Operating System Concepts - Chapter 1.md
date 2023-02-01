--- 
> An operating system is *software* that manages a computer's hardware

### Chapter Objectives: 
1. Describe the general organization of a computer system and the role of interrupts
2. Describe the components in a modern pumitprocessor computer system
3. Illistrate the transition from user mode to kernel mode
4. Discuss how operating systems are used in various computing environments
5. Provide examples of free and open source operating systems
---
## What Operating Systems Do (1.1)
- Hardware: 
	- Central Processing Unit (CPU)
	- Memory 
	- I/O devices 
- We have no universal accepted definition of what is part of the **operating system** 
	- A common definition of an operating system is the program running at all times, usually called the *kernel*
	- There are applications in the operating system that are not necessarily in the kernel though
	- There are programs called "application programs" which include all programs not associated with the operating system (*think videogames*)
	- Middleware is this sort of limbo between the kernel and applications which is pretty large in mobile devices 
---
## Computer System Organization (1.2)
### Interrupts 
> A hardware interrupt is **an electronic signal from an external hardware device that indicates it needs attention from the OS**. One example of this is moving a mouse or pressing a keyboard key. In these examples of interrupts, the processor must stop to read the mouse position or keystroke at that instant.

- The implementation of an interrupt is done through an "*interrupt-request line*" that the CPU senses after executing every instruction 
- For more advanced systems not only do we need to take care of interrupts when they happen, but we need more sophisticated management techniques
	1. We need the ability to defer interrupt handling during critical processing
	2. We need an efficient way to dispatch to the proper interrupt handler for a device
	3. We need multilevel interrupts (some interrupts are more important that others!!) george orwin 1982!!
	- In modern day systems we use **interupt controller hardware** to handle this
---
### Storage structure 
- There are different types of memory each with their pros/cons. *Generally, there is a tradeoff between size and speed.* 
	**- Main memory** 
		- Usually too small to store all neede programs and data permanently 
		- Is volatile, it loses its contents when the power is turned off
		- Its close to the CPU, and pretty fast (not nearly as close or fast as registers and cache tho)
	- **Secondary Memory**
		-  Can be very large, it can store as much data as necessary
		- Not nearly as fast as main memory 
		- is not volatile, meaning that if the power goes off nothing gets lost 
		- Split into two categories, Mechanical and electrical NVS (non volatile storage)
		- Examples: NVM and HDDs
- All forms of memory provide an array of bytes with their own adresses. Based on the Von Neuman Architechture of the CPU, interactions are achieved through `load` and `store` instructions. 
### I/O structure (breifly in 1.2.3)
- A general purpose computing system as we know of uses a common *bus* to exchange data via multiple devices
	- This form of interrupt-driven system is ine when there is a small amount of data but can produce high overhead when trying to move a lot of data (e.g. seconary memory storage I/O)
- **Direct memory acces (DMA)** is a solution to this problem of speed. 
	- The device controller transfers the an entire block of data directly from the device to main memory (or vice/versa) *with no intervention from the CPU*
	- In this way, only one unterrupt is sent (to signal the process has been completed) instead of an interrupt for every byte of data.
---
## Computer System Architecture (1.3)

- We catagorize thecomputer system architecture based on the number of general-purpose processors used
- A **core** is the component that executes instructions and registers for storing data locally
### Single Processor systems
- General purpose computers in the past had single processors with single cores. 
	- Device specific processors like a disk or keyboard might also be a single processor system
		- E.g. PCs containt a microprocessor in the keyboard which converts the keystrokes into code
		- Special-purpose micro-processors are oftern built into the hardware of the specific device
### Multiprocessor sytems
- Multiprocessor systems dominate the landscape of computing of computing
	- The main benefit of multicore systems is increased throughput 
	- The speedup ration of N processors in not N time- it is less than N. This is because there is a bit of overhead when working with multiple processors cooperating on a single task 
#### Symmetric multiprocessing system
- Each peer CPU processor performs all tasks
	- All processors use the same physical memory and share the same bus 
	- The benefit of this model is that many processes can run simultaneously —N processes can run if there are N CPUs—without causing performance to deteriorate significantly.
![[Screenshot 2023-01-18 at 11.32.44 AM.png]]

- **One chip (processor) and multiple cores** use a lot less energy compared to multiprocessor systems which makes them more useful in mobile devices and laptops 
	- Here is an example of a dual core design on the same chip (processor)
	- ![[Screenshot 2023-01-18 at 11.34.03 AM.png]]

- Adding CPUs to a multiprocessor system does benefit preformance, but the rule is not the scalable. This is because the system bus becomes a bottleneck as the CPUs tend to compete for system bus space
	- This can be avoided if we give each CPU a bit of its own memory accessed via a small fast local bus 
	- The CPUs are connected by a "*shared system interconnect*" which is known as **non-uniform memory access aka NUMA**![[Screenshot 2023-01-18 at 11.38.56 AM.png]]
### Clustered Systems
 - Clustered systems gather togehter CPUs
	 - They are different than multiprocessor systems because they are comprised of 2 or more individual systems (called nodes) joined together. Each node is like its own multicore system. 
		- These systems are considered "loosely coupled"
	- The generally accepted definition is that clustered computers share storage and are closely linked via a local-area network LAN
	- Clustered systems provide *"high availability service"* meaning that if one or more of the clusters fails, the system can still run 
		- We are able to achieve a high availability if there is some redundancy in the system 
		- Systems which include this redundancy allow for "graceful degredation" when service is not fully available. And even "Fault tolerant" when things go wrong but the users can still maintain access
			- Fault tolerance requires a mechanism to allow the failure to be detected, diagnosed, and, if possible, corrected.
![[Screenshot 2023-01-18 at 11.59.16 AM.png]]
> The definition of multiprocessor has evolved over time and now includes multicore systems, in which multiple computing cores reside on a single chip. Multicore systems can be more efficient than multiple chips with single cores because on-chip communication is faster than between-chip communication.
> ![[Screenshot 2023-01-18 at 11.34.38 AM.png]]
---
## Operating Sytstem Operations (1.4)

- An operating system provides an environment with which programs can run on 
	- When a computer is booted, there needs to be an initial program which is run (this is known as a bootstrap) which is located in the hardware in firmware
		- To accomplish this goal, the bootstrap program must locate the operating-system kernel and load it into memory.
		- It is from here that the operating system can run daemons (one of which is systemd)

### Multiprogramming and Multitasking 
- In **multiprogramming**, a program is execution is called a process
	- The operating system is dealing with many programs and needs to wait on certain (for example an I/O interrupt) and would move onto another process (program) while it waits
	- In a non-multiprogrammed system, the CPU would simply sit idle waiting for an I/O interrupt
	- This allows for the CPU to always ben in use, it is analogous to my gastrointerologiust who has more patients than just me. When i am finished my appointment he doesnt wait around but instead tends to his other patients
- **Multitasking** is the logical extension of this: 
	- In multitasking, the CPU executes multiple processes by switching among them. It swtiches so fast that the user experiences a fast response time
	- EXAMPLE: Imagine, a human can only type at like 7 letters a second. This is really slow for a computer, it would be a waste of time for the CPU to sit idle waiting for the user to type another letter, it is best to move on and work on another process in the meantime 
	- for CPUs to multitask, they need a form of memory management as well as a priority list for processes (called *CPU scheduling*)

### Dual mode and multimode operation 
- We need to distinguish between a user and a system, the way we give admin privledges is by using a **mode bit** where kernel (0) or user (1)
- When control is passed from the kernel to the application, the mode bit would be set to one 
- LOOK THRU THE SLIDES TO GET A BETTER IDEA OF HOW SECURITY OF ADMIN RIGHTS WORK 
### Timer 
- A timer can be set to interupt the computer after a specified amount of time. This allows for the OS to maintain control of the CPU at all times so that applicaitons which crash etc will not become detrimental 
## Resource management (1.5)
### Processing management 
- A process is an instance of a program in execution. The process is an *active entity* while the program is a *passive entity*, similar to a file stored on a disk
- The operating system is responsible for the following activies in connection with process management 
	- Creating and deleting user/system processes
	- Scheduling processes and threads on the CPU
	- Suspending and resuming processes
	- Providing mechanisms for process synchronisation and communication
### Memory management
- The operating system is responsible for 
	- Keeping track of which parts of memory are currently being used and which processes are using them 
	- Allocating and deallocating memory space as needed
	- Deciding which processes (or parts of processes) and data to move into and out of main memory
#### File-System Management 
- 