## Automatic Memory Management 
- As we have seen, there are many forms of memory management traditionally falling into 3 categories
	1. static (global variables)
	2. automatic (local function variables)
	3. dynamic (new, alloc)
- The first two can be handled by the computer/compiler but the third is managed by the programmer
- It is likely that at some point dynamically allocated memory will no longer be needed
	- It is repsonsible to reclaim this space, because large application will end up taking a lot of space if it is not done
	- Failure to reclaim this space is what we have referred to as a *memory leak*
- In the past 20-30 years, virtually all new programming langauges offer some sort of garbage collection for dynamically allocated memory 
---
## Mark and Sweep Algorithm 
- The most fundemental garbage collection technique is a two-phase technique called mark and sweep 
---
## The Root Set
---
## The two-phase approach 
---
### Marking candidates
---
### Sweeping dynamic memory 
---
## Argumenting non-GC langauges
---
### The Boehm GC 
---