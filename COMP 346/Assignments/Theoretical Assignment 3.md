## Question # 1 
Answer the following questions: 
###### i. (a) What are relocatable programs? (b) What makes a program relocatable? (c) From the OS memory management context, why programs (processes) need to be relocatable? 
- Relocatable programs are programs that can be loaded into phsyical memory from other locations with correct adresses for resources.   
- A program is relocatable if it can be relocated without the loss of data. If a program contains relative addresses (or virtual addresses) then it is relocatable. 
- Processes must be relocatable for purposes of compaction. If you shift the process in memory you need that process to be relocatable 
###### ii. What is (are) the advantage(s) and/or disadvantage(s) of small versus big page sizes? 
- Small page sizes: 
	- Advantage: The internal fragmentation caused by the last page is smaller 
	- Disadvantag: Page table entries accquire more overhead, and I/O is slower. Page faults are also more likely if the pager size is smaller. 
- Big page sizes:
	- Advantage: I/O is more suitable for larger page sizes, page tables have less overhead
	- Disadvatange: internal fragmentation in the last frame 
	- less page faukts 
###### iii. What is (are) the advantage(s) of paging over segmentation? iv. What is (are) the advantage(s) of segmentation over paging? Explain your answers.
- Paging is advantageous compared to segmentation because it removes the problem of externel fragmentation. Segmentation involves splitting the code to be loaded into memory into differently sized pieces which when taken in and out of memory will require compaction to create usable space
- Segmentation is not all bad though, it removes the issue of internal fragmentation. Since eacg segment is a custom size required for the micro process, there is no internal fragmentation. Also since page lookup is preferably done in the cache, context switching is faster because there is no extra storage used in the cache.

## Question # 2
Consider the below implementations of a semaphore’s wait and signal operations:
![[Pasted image 20230419122656.png]]
###### a) What are the critical sections inside the wait and signal operations which are protected by disabling and enabling of interrupts?
- The critical sections in the wait operation which are protected by the disable and enable interrupts is the semaphore implementations of the ready queue
###### b) Give example of a specific execution scenario for the above code leading to inconsistency if the critical sections inside implementation of wait() and signal() are not protected (by disabling of interrupts).
- Scenario: If the wait() and signal() operations are not protected the following can throw a queue empty index error: 
- wait() operation runs with semaphore value reduced to 0
- interrupt
- Signal() operation dequeues sem.queue
- there is no elements in sem.queue (error)
###### Suppose that process A calling semaphore wait() gets blocked and another process B is selected to run (refer to the above code). Since interrupts are enabled only at the completion of the wait operation, will B start executing with the interrupts disabled? Explain your answer.
- No, although the restore(state) is executed, it is up to the operating system to perform the context switch which will not be performed until the disable interrupt is released
## Question # 3
Consider a demand-paged system where the page table for each process resides in main memory. In addition, there is a fast associative memory (also known as TLB which stands for Translation Look-aside Buffer) to speed up the translation process. Each single memory access takes 1 microsecond while each TLB access takes 0.2 microseconds. Assume that 2% of the page requests lead to page faults, while 98% are hits. On the average, page fault time is 20 milliseconds (includes everything: TLB/memory/disc access time and transfer, and any context switch overhead). Out of the 98% page hits, 80 % of the accesses are found in the TLB and the rest, 20%, are TLB misses. Calculate the effective memory access time for the system.
MM lookup: 1ms
TLB lookup: 0.2ms 
page miss ratio: 0.02
page hit ratio: 0.98 
page miss : 20000ms 
TLB hit ratio: 0.8 
TLB miss ratio 0.2
Effective memory access time: 
$$hitTime: 0.98(0.8(0.2+1)+0.2(1+1+0.2) + 1)+$$
$$missTime : 0.02(0.2+1+20000 + hitTime)$$

- hitTime + missTime = 2.352 + 400.0704
=  402.42(rounded to 2 decimal)
_Note that this solution takes as an assumption that the pages which are stored in the TLB are random_

## Question # 4
Consider the page reference string Ʀ={0, 1, 2, 0, 1, 2, 0, 1, 2, 3, 6, 7, 6, 7, 0, 1, 2, 3, 4} for a given process.
###### (a) Show the memory representation of the pages using the LRU algorithm and an allocation of 3 frames. How many page faults are there?
| Frame / Allocation | 0  | 1  | 2  | 0 | 1 | 2 | 0 | 1 | 2 | 3  | 6  | 7  | 6 | 7 | 0  | 1  | 2  | 3  | 4  |
|--------------------|----|----|----|---|---|---|---|---|---|----|----|----|---|---|----|----|----|----|----|
| Frame 1            | 0* | 0  | 0  | 0 | 0 | 0 | 0 | 0 | 0 | 3* | 3  | 3  | 3 | 3 | 0* | 0  | 0  | 3* | 3  |
| Frame 2            |    | 1* | 1  | 1 | 1 | 1 | 1 | 1 | 1 | 1  | 6* | 6  | 6 | 6 | 6  | 1* | 1  | 2  | 4* | 
| Frame 3            |    |    | 2* | 2 | 2 | 2 | 2 | 2 | 2 | 2  | 2  | 7* | 7 | 7 | 7  | 7  | 2* | 2  | 2  |

There are 11 page faults 
###### (b) Show the memory representation of the pages using the Belady Optimal algorithm and an allocation of 3 frames. How many page faults are there? 
| Frame / Allocation | 0  | 1  | 2  | 0 | 1 | 2 | 0 | 1 | 2 | 3  | 6  | 7  | 6 | 7 | 0 | 1  | 2  | 3  | 4  |
|--------------------|----|----|----|---|---|---|---|---|---|----|----|----|---|---|---|----|----|----|----|
| Frame 1            | 0* | 0  | 0  | 0 | 0 | 0 | 0 | 0 | 0 | 0  | 0  | 0  | 0 | 0 | 0 | 0  | 0  | 3* | 3  |
| Frame 2            |    | 1* | 1  | 1 | 1 | 1 | 1 | 1 | 1 | 1  | 1  | 7* | 7 | 7 | 7 | 7  | 7  | 7  | 4* |
| Frame 3            |    |    | 2* | 2 | 2 | 2 | 2 | 2 | 2 | 3* | 6* | 6  | 6 | 6 | 6 | 1* | 2* | 2  | 2  |
There are 9 page faults 
###### (C) Show the memory representation of the pages using the working set model with a window size ∆=3 (∆ indicates the maximum number allowed for a page to be in memory before being replaced; i.e. if a page is not used for 3 consecutive times, then it must either be used/demanded next, or it has to be removed). How many page faults are there?
| Frame / Allocation | 0  | 1  | 2  | 0 | 1 | 2 | 0 | 1 | 2 | 3  | 6  | 7  | 6 | 7 | 0  | 1  | 2  | 3  | 4  |
|--------------------|----|----|----|---|---|---|---|---|---|----|----|----|---|---|----|----|----|----|----|
| Frame 1            | 0* | 0  | 0  | 0 | 0 | 0 | 0 | 0 | 0 | 3* | 3  | 3  | 3 |   | 0* | 0  | 0  | 3* | 3  |
| Frame 2            |    | 1* | 1  | 1 | 1 | 1 | 1 | 1 | 1 | 1  | 6* | 6  | 6 | 6 | 6  | 1* | 1  | 1  | 4* |
| Frame 3            |    |    | 2* | 2 | 2 | 2 | 2 | 2 | 2 | 2  | 2  | 7* | 7 | 7 | 7  | 7  | 2* | 2  | 2  |
There are 11 page faults 
## Question # 5
Consider a system that would implement the page table on the CPU if feasible.
###### (a) Give an advantage of this strategy. 
- The advantage of storing the page table on the cpu (in the cache) would mean faster search up because the space is accessed faster in comparison to ram 
###### (b) Give a disadvantage of this strategy
- The disadvatage of storing the TLB is that context switching takes longer because there is more data which must be switched when processes switch on the CPU 
## Question # 6
Explain (i) an advantage and (ii) a disadvantage that a global page replacement algorithm has over a local page replacement algorithm.
- The advantage of global page replacement is that it has more information to decide what processes will possibly need to be used in the future. This, in theory, would lead to a close number of page faults to Belady's algorithm despite only looking into the past
- The disadvantage of global pae replacement is the complexity time required to process which page should be replaced. The complexity of the global page replacement in O(n) while the local algorithm is O($\Delta$) aka constant 
## Question # 7
Consider a system that adjusts the degree of multiprogramming by monitoring the mean time between page faults (i.e. Tpf) and the mean time to service a page fault (i.e. Tfs). Describe the performance of the paging system in terms of the degree of multiprogramming when (i) Tpf is greater than Tfs
- If the page fault time is greater than the page service time, the degree of multiprogramming is too high 
(ii) Tpf is less than Tfs and 
- If the page fault time is less than the page service time, the degree of multiprogramming is acceptable 
(iii) Tpf is equal to Tfs.
- This would mean that half of the processing time is waisted on page faulting which in most scenarios would be considered wasteful, and therefore the degree of multiprogramming might be too high. 

## Question # 8 
Some systems automatically open a file when it is referenced for the first time and close the file when the job terminates. Discuss the advantages and disadvantages of this scheme as compared to the more traditional one, where the user has to open and close the file explicitly. 
- The advantage of the scheme would be the memory saved from closing files. Users who would possibly not close files when they are finished reading would be wasting the memory by keeping it open 
- The disadvantage is the user experience. Having to reopen files when jobs complete mean unescessary wait times (time spent moving the data to main memory once more)
## Question # 9 
###### a) What is the difference between preemptive and non-preemptive scheduling? Why is strict nonpreemptive scheduling unlikely to be used in a computer system that provides both batch and timesharing service? 
- Preemptive scheduling refers to a method of scheduling where a process can be interupted by another process, for reasons such as starvation and priority. non-preemptive scheduling executes processes in a one by one manner like in systems which utilize uniprogramming. 
- Strict nonpreemptive scheduling is unlikely to be used in such a system because timesharing services by default require use of multiprogramming, where processes can be allocated set amounts of time to execute which provides fairness. Preemptive scheduling in a timesharing environment could have the user feel as though they have all of the processing time even though they dont. This would not be the case in a nonpreemptive scheduling model.
###### b) What is the trade-off used to select the quantum size, say, in pure Round-Robin scheduling? 
- Quantum size refers to the amount of time allocated to a process to run on the CPU by the scheduler. Large qauntum time sizes are beneficial insofar as context swithcing doesnt waste a large ratio of the time, but it trades off the fact that processes will need to wait longer before its their turn. It is suggest that the context swithcing time should be 10% or less of the quantum size time in the Round-Robin scheduling model 

## Question # 10 
What advantage is there in having different values of the scheduling quantum on different levels of a multilevel feedback queuing system? Your answer should consider all aspects such as fairness, starvation, efficiency, etc. 
- The advantage of having different values of scheduling quantum in a feedback queuing system is the ability to prioritize some tasks over others. For example, some processes, such as system level processes, are often desired to have higher priority than other processes. Also, processes that require a lot of running time can be brought to a lower priority where they are ran as first come first serve with a high quantum level. The processes which have a higher priority can be afforded to have a lower quantum time while the low priroity tasks will have a long quantum time which is good because scheduling time is not a problem. 
## Question # 11 
Consider the following set of prioritized processes, where a smaller priority value represents a higher priority.
![[Pasted image 20230419123119.png]]
Assume that all processes arrived at the same time, however they are inserted in the ready list in the order indicated in the above table.

- FCFS waiting times & response times: 
	- P0= 0 
	- P1= 20
	- P2 = 35
	- P3 = 56
	- P4 = 63
- FCFS TAT:
	- P0= 20 
	- P1= 35
	- P2 = 56
	- P3 = 63
	- P4 = 75
| CPU Time total | 20 | 35 | 56 | 63 | 75 |
|-----------|----|----|----|----|----|
| Process   | 0  | 1  | 2  | 3  | 4  |

- SJF waiting times & response times: 
	- P0= 34
	- P1= 19
	- P2 = 54
	- P3 = 0
	- P4 = 7
- SJF TAT: 
	- P0= 54
	- P1= 34
	- P2 = 75
	- P3 = 7
	- P4 = 19
| CPU Time total | 7 | 19 | 34 | 54 | 75 |
|-----------|---|----|----|----|----|
| Process   | 3 | 4  | 1  | 0  | 2  |


- Priority 
- Priority waiting times & response times: 
	- P0= 27
	- P1= 0
	- P2 = 47
	- P3 = 68
	- P4 = 15
- Priority TAT:
	- P0= 47
	- P1= 15
	- P2 = 68
	- P3 = 75
	- P4 = 27
| CPU Time total  | 15 | 27 | 47 | 68 | 75 |
|-----------|----|----|----|----|----|
| Process   | 1  | 4  | 0  | 2  | 3  |


- Round Robin (Quantum time is 3)

| CPU End Time | 3 | 6 | 9 | 12 | 15 | 18 | 21 | 24 | 27 | 30 | 33 | 36 | 39 | 40 | 43 | 46 | 49 | 52 | 55 |
|--------------|---|---|---|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|----|
| Process      | 0 | 1 | 2 | 3  | 4  | 0  | 1  | 2  | 3  | 4  | 0  | 1  | 2  | 3  | 4  | 0  | 1  | 2  | 4  |


| CPU Time  | 58 | 61 | 64 | 67 | 70 | 72 | 75 |
|-----------|----|----|----|----|----|----|----|
| Process   | 0  | 1  | 2  | 0  | 2  | 0  | 2  |

- RR Response times: 
	- P0 = 0
	- P1= 3
	- P2 = 6
	- P3 = 9
	- P4 = 12
- RR waiting times: 
	- P0= 72 - 20 = 52
	- P1= 61-15 = 46
	- P2 = 75 - 21 = 54
	- P3 = 27-7 = 0
	- P4 = 30-12 = 18
- RR TAT: 
	- P0= 72 
	- P1= 61
	- P2 = 75
	- P3 = 27
	- P4 = 30