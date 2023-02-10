# Chapter 3:
### Section 3.2.3 Context Switches
- As explained previously, interrupts cause the CPU core to change its current task to run a kernel routine. This requires perserving the *context* in a **context switch**
	- A typical speed is several microseconds 
	- It should be noted that the more advanced/complex a system is, the longer it takes to do a context switch
- Generically, we perform a state save of the current state of the CPU core, be it in kernel or user mode, and then a state restore to resume operations.
---
### Section 3.3.2 Process Termination 
- A process terminates when it finishes executing its final statement and asks the operating system to delete it by using `exit` 
- There are other ways which a process can be terminated. Windows has `TerminateProcess()` for example. For a process to terminate another, it needs to be a child and its identity must be known by the parent process. 
	- This makes sure that misbehaving applications don't kill other processes
- A parent might kill a child process for many reasons: 
	1. The child has exceeded its usage of some of the resources that it has been allocated. 
	2. The task assigned to the child is no longer required 
	3. The parent is exiting, and the operating system does not allow a child to continue if its parent terminates.
		- This is considered *cascading termination*
- Before the parent calls the wait() method a terminated child would be a zombie 
- In the instance where a parent process terminated but a child does tho, we call it a **orphan process**
---
### Multiprocess Architecture (Page 124)
- Why is it the Google Chrome is able to have a tab which has crashed but still work in other tabs? 
	- This has to do with the multiprocess architecture of Google Chrome 
- Because of how processes are understood by the operating system, if a program has a thread that has failed crashed, there is no difference in the eyes of the operating system of whether the thread or the entire process has crashed
	- This is why other browsers such as Internet Explorer crash as a whole if a single web site crashes
- How does Google Chrome bypass this issue? 
> The browser process is responsible for managing the user interface as well as disk and network I/O. A new browser process is created when Chrome is started. Only one browser process is created.

> Renderer processes contain logic for rendering web pages. Thus, they contain the logic for handling HTML, Javascript, images, and so forth. As a general rule, a new renderer process is created for each website opened in a new tab, and so several renderer processes may be active at the same time.

> A plug-in process is created for each type of plug-in (such as Flash or QuickTime) in use. Plug-in processes contain the code for the plug-in as well as additional code that enables the plug-in to communicate with associated renderer processes and the browser process.

>The advantage of the multiprocess approach is that websites run in isolation from one another. If one website crashes, only its renderer process is affected; all other processes remain unharmed. Furthermore, renderer pro- cesses run in a sandbox, which means that access to disk and network I/O is restricted, minimizing the effects of any security exploits.
---
# Chapter 4:  Threads and Concurrency 
## Section 4.1
- A thread is a basic unit of CPU utilization
	- it comprises a thread ID, a program counter (PC), a register set, and a stack
- ![[Screenshot 2023-02-10 at 5.38.27 PM.png]]
- There are many examples of multi-thread utilization in applications
	- A word editor might use different threads, one for processing keystrokes and another to display the graphics on a screen 
	- A web server needs to handle requests for images, video, etc, if they were to be single-threaded, only a single client would be able to be handled at a time 
		- An old solution to this problem would have been to have the system create a process for each task, but this is a high-resource task 
- **Benefits of Multithreaded systems**
	- **Responsiveness**: Multithreaded application allow for a program to keep on running if its performing an intensive operation. A single threaded application woul dbe unresponsive if until the process is completed
	- **Resource Sharing**: Processes are able to share memory by using shared storage or message passing. However threads share memory and resources by default. 
	- 
---
## Section 4.2 
---
## Section 4.3
---