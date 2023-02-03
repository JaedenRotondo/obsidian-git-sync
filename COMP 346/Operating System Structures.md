> Permanently Skip: Sections 2.2, 2.8.1, 2.8.2, 2.8.3, 2.8.4, 2.8.5, 2.9 & 2.10
## 2.1 Operating-System Services
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

## 2.3 System Calls
- 