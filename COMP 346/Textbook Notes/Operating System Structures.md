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
### 2.3.2 Application Programming Interface
### 2.3.3 Types of System Calls



## Section 2.4 System Services

## Section 2.5 Linkers and Loaders

## Section 2.6 Why Applications Are OS Specific

## Section 2.7 OS Design and Implementation
### 2.7.1 Design Goals
### 2.7.2 Mechanisms and Policies
### 2.7.3 Implementation

## Section 2.9 Building and Booting an OS
### 2.9.1 OS Generation
### 2.9.2 System Boot

## Section 3.4 Interprocess Communication

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