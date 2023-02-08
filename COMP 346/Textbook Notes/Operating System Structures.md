## Section 2.1 OS Services
- An operating system provides several services
**1. User Interface:** Example is a GUI, where the mouse is used in a window
**2. Program Execution:** an OS must load a program into main memory and run it 
**3. I/O Operations**: User might need to use an IO device like a keyboard, there must be system structures to manage IO devices
**4. File-System Manipulation**: Read write delete and create files, there is also permission management 
**5. Communicaitons**: Communications can be done via *shared memory* or *message passing*
**6. Error Detections**: for example memory errors or network errors, there must be some handling 
**7. Resource Allocation**: Since programs might be running at the same time, there must be some priority 
**8. Logging**: -   We want to keep track of which programs use how much and what kinds of computer resources.
**9. Protection and Security**: -   When several separate processes execute concurrently, it should not be possible for one process to interfere with the others or with the oper- ating system itself.

---
## Section 2.3 System Calls
- System calls provide an interface to the services made available by an operat- ing system.
### 2.3.1 Example
- Gives an example of how the `cp` command works in Unix
- Essentially, all elements of the command are other system calls which can be called from each other 
- For example, these are system calls which would need to be made 
	- Acquire input file name
	- Write prompt to screen
	- Accept input  
	- Acquire output file name
	- Write prompt to screen
### 2.3.2 Application Programming Interface
- Oftentimes programmers do not want to work with the system calls of a given operating system, there are a few reasons for this
	- Portability: a programmer would not be able to switch operating systems because the specific system calls will differ. An API on the other hand can is portable 
	- Complexity: Although API calls are similar to the actual system calls which they will tigger, oftentimes they are more simple to use 
	- For example the read function takes in several parameters which makes the process easier to code
	- ![[Screenshot 2023-02-07 at 10.58.48 PM.png]]
### 2.3.3 Types of System Calls
- System calls can be categorized into 6 different types 
1. process control
	1. ◦ create process / terminate process  
	3. load / Execute
	4. get process attributes / set process attributes 
	5. Wait / signal event
	6. Allocate and free memory 
2. fil management
	1. Open / close file
	2. Create / delete file 
	3. read write file 
	4. get and set file attributes 
3. device management
	1. read / write / reposition 
	2. get / set device attributes
	3. logically attach or detach devices 
5. information maintenance
	1. get / set time or date
	2. get / set system data
	3. get / set process, file, device attributes
6. communications
	1.  create / delete communication connection
	2. send / recieve messages 
	3. attach / detach remote devices 
7. protection
	1. get / set file permissions 
![[Screenshot 2023-02-07 at 11.01.06 PM.png]]
## Section 2.4 System Services
- System services (also called system utilities) are a convenient environment for program developement and execution 
- They can be divided into the following categories 
	- File management 
	- Status information 
	- File modification 
	- Programming language support
	- Program loading and execution 
	- Communications
	- background services (daemons)


## Section 2.5 Linkers and Loaders
- Usually a program exists on a disk as a binary executable fiele 
	- To run this on the CPU it must be brought into main memory 
	- **Linker**: combines the relocatble object files into a single binary *executable* Note that libraries might be included in this as well
	- **Loader** : Loads the binary file from the linker into the main memory to be run on the CPU 
	- DLL's allow for libraries to be dynamically linked, meaning that they will not be added to the executable unless they are needed
	- ![[Screenshot 2023-02-08 at 3.33.26 PM.png]]
## Section 2.6 Why Applications Are OS Specific
- Each OS provides its own unique set of system calls which makes it difficult to use applications on different OS's 
- However, there are 3 main ways which a program can become OS independent 
1. The application can be written in an *interpreted language* such as python or ruby which would allow for it to be ran with an interpreter 
2. The application can be written in a language that is run in a virtural machine (such as Java). In this case, the virtual machine (which is portable) includes its own bytecode verifier and loader etc) 
3. The application is written in a language that use a standard language or API which the operating system can compile into binary code that it will understand
- There are other issues that exist at lower levels in this system 
	- Each OS has its own binary format (location of header, instructions, variables) that is required for the OS to open the file 
	- CPUs have varying instruction sets 
	- System calls vary between platforms 
## Section 2.7 OS Design and Implementation
### 2.7.1 Design Goals
- User goals and system goals need to be taken into consideration 
### 2.7.2 Mechanisms and Policies
### 2.7.3 Implementation
- Higher level languages are often preffered 
- The only possible disadvantages of implementing an operating system in a higher-level language are reduced speed and increased storage requirements.
	- Not in issue in today's fast systems 
## Section 2.9 Building and Booting an OS
### 2.9.1 OS Generation
- How to build an operating system (who cares)
### 2.9.2 System Boot
- How does the hardware know where the kernel is or how to load that kernel?
- The process of starting a computer by loading the kernel is known as booting the system.
	- This is the BIOS 

## Section 3.4 Interprocess Communication
- There are many benefits of an environment that allows for process communication 
	- **Informaition sharing**: Several applications might be interested in the same piece of data
	- **Computational speedup** If we want a process to run quickly, it is faster to divide it up into subroutines, this is only possible with subroutine communication 
	- **Modulairty**: Interprocess communication allows us to use threads for different tasks and to split things up 
- There are two methods of Interprocess Communication (IPC)
	1. Shared memory 
		- A region of the data is shared 
	2. Message passing 
## Section 12.1 Overview of I/O Systems

## Section 12.2 I/O Hardware

## Section 12.3 Application I/O Interface
### 12.3.3 Clocks and Timers
### 12.3.4 Nonblocking and Asynchronous I/O
### 12.3.5 Vectored I/O
## Section 12.4 Kernel I/O Subsystem
### 12.4.1 I/O Scheduling
### 12.4.4 Spooling and Device Reservation
###  12.4.6 I/O Protection