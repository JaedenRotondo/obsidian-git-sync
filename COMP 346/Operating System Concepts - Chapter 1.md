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
1. **Single Processor systems**
	- General purpose computers in the past had single processors with single cores. 
	- Device specific processors like a disk or keyboard might also be a single processor system
		- E.g. PCs containt a microprocessor in the keyboard which converts the keystrokes into code
		- Special-purpose micro-processors are oftern built into the hardware of the specific device
1. **Multiprocessor sytems**
	- Multiprocessor systems dominate the landscape of computing on 
1. **Clustered Systems**
---
## Operating Sytstem Operations 