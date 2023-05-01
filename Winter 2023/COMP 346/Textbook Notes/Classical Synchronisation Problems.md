## 7.1 Classical Problems of Synchronisation 
- These are a large class of concurrency-control problems 

### The Bounded Buffere Problem 
- Assume that the Producer and the Consumer share the following resources
``` Java
int n;
semaphore mutex = 1;
semaphore empty = n;
semaphore full = 0
```
