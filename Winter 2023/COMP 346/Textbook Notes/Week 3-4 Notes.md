# Chapter 3:
### Section 3.2.3 Context Switches
- As explained previously, interrupts cause the CPU core to change its current task to run a kernel routine. This requires perserving the *context* in a **context switch**
	- A typical speed is several microseconds 
	- It should be noted that the more advanced/complex a system is, the longer it takes to do a context switch
- Generically, we perform a state save of the current state of the CPU core, be it in kernel or user mode, and then a state restore to resume operations.
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
	- **Economy**: Allocating memory for process creation is an expensive process. Since threads use the same shared/allocated memory it is a lot more economical 
	- **Scalability**: The benefits of multithreading are even greater in a multiprocessor architecture, where threads can be ran parallel on different processing cores
---
## Section 4.2 Multicore Programming 
- Difference between *Concurrency* and *Parallelism*
	- **Concurrency**: Refers to running multiple threads possibly on a single core ![[Screenshot 2023-02-11 at 11.48.39 AM.png]]
	- **Parallelism**: referes to threads running on different cores in parallel ![[Screenshot 2023-02-11 at 11.49.06 AM.png]]
- Problems with Programming systems which utilize multiple core arhitecture 
	- **Idenitfying tasks**: that can be performed on different cores. Ideally, these tasks would be independent of each other
	- **Balance**: One must also identify that certain indepent tasks are not worth running on a seperate core. 
	- **Data Splitting**: In the same way that application processes must be divided into tasks, so does the memory which is allocated towards it
	- **Data Dependency**: The data accessed by the task must be examined for dependencies between two or more tasks 
	- **Testing and Debugging**: Since the program will be running on multiple cores, it is inherently a lot more difficult to bug since there are different tasks that the program can take. 

### 4.2.2 Types of parallelism 
- There are 2 types of parallelism 
	1. **Data Parallelism**: This refers to seperating data sets alongside different computing cores. For example, if you had to find the sum of an array, you could sperate the data so that the first core can access 1 to (N/2)-1 and the other core N/2 to N-1. 
	2. **Task Parallelism**: This refers to distributing Threads (*not tasks*) to different computing cores. Each thread is perfoming a unique operation. Different threads might be operating on the same data or different data. 
> Note that these parallelism methods are not mutually exclusive, and an application may in fact use a hybrid of these two strategies.
---
## Section 4.3
- Threads may be used at both the *Kernel level* or the *user level*.
- Ultimately, there must be a relationship between the kernel threads and the user threads. This includes the following models: 
	1. **Many-to-one Model**:
	- Maps many user threads to a single kernel thread. This means that only one thread can access the kernel at a time. Mulitple threads are unable to run parallel in a multicore system.
	- Thread managemen is done by the Thread library is user space so it is effecient 
	- ![[Screenshot 2023-02-11 at 12.14.10 PM.png]]
	2. **One-to-one Model**:
		- The one to one model maps each user thread to a kernel thread 
		- It allows for more concurrency compared to the many to one model 
		- It is very expensive since making kernel threads is a lot more expensive than making user threads
		- ![[Screenshot 2023-02-11 at 12.14.53 PM.png]]
	3. **Many-to-many Model**:
		- The many-to-many model suffers from neither of these shortcomings: developers can create as many user threads as necessary, and the corresponding kernel threads can run in parallel on a multiprocessor. Also, when a thread performs a blocking system call, the kernel can schedule another thread for execution.
		- As systems advance, and the number of cores are increasing on systems, it is less important to keep track of kernel threads than ever. 
		- ![[Screenshot 2023-02-11 at 12.15.07 PM.png]]
---