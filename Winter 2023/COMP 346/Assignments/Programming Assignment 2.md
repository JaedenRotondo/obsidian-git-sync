--- 
## Phase 1
### Explain your choice of using either synchronized methods or synchronized statements.

We decided to implement synchronized statements instead of methods for several reasons: 

1. Synchronizing the methods by including the `synchronized` keyword will only make sure that a particular thread is unable to access the same method. However, when it comes to our synchronization issues, problems of synchronous deposits and withdrawals could not be trivially solved. Using synchronizing statements on the other hand wherever account[i] was accessed made sure that when a thread was accessing an account that no other thread could touch it. 

2. In general, although synchronized statements are harder to implement, they allow for a more tailored critical section which can result in faster thread functioning 

3. Specific to our program, using synchronized statements was easier because it was quite clear which areas of the code had to be synchronized (i.e. the account array). This is analogous to the buffer in the bounded buffer problem.
---
## Phase 2
### Execute the program and comment about the running times of the server threads compared to using busy-waiting in phase (i)
- Running times when using the semaphore implementation in Phase 2 allowed the server sender and receiver to process transactions even when the buffer was not completely full/empty. This, in theory, should mean that it runs faster. 

- This is because in phase (i) a transaction can only be consumed from the buffer if the buffer was full (placement of the busy wait and yield) while in phase two the sempahore tracked the buffer size and allowed consumption even if the buffer wasnt full and vice versa. 

- With that being said, there was an minimal/insignificant increase of server thread time when using semaphores (445ms avg vs 443ms)- *this can be attributed to the fact that busy waiting is actually not much slower (and in some cased faster) than yielding due to the overhead of context switching in modern systems.* 
---
### Comment about the running times compared to the implementation with 2 threads
- We saw aorund a 25% decrease (440ms to 340ms) in server thread running time when implementing a third thread. This coincides with our understanding of how concurrent threads can lessen the overall time a process takes to complete. 

- It should be noted, however, that run time is not 1/3 faster just because there is 3 threads - but the positive trend remains true nonetheless. Of course, when adding extra threads we will eventually run into a bottleneck as well where this correlation between number of threads and decrease running time also doesnt hold true. 

- For experemental purposes, we tested a different number of threads and observed the results: 
	- 4 Threads - 239 
	- 5 Threads - 241 
	- This shows that even 4 Threads is optimal for the system, but after that there incures a bottleneck from the 5th thread and actually increases the server run time.
---