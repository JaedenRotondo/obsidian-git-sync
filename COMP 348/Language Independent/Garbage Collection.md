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
- The most fundemental garbage collection technique is a two-phase technique called mark and sweep know as a *tracing collector*
- Mark and sweep begins with a set of "live" or "active" objects nd then works out from this point which objects that should be considered for reclamation 
	- This starting set is known as the "Root Set" and consists of
		- Any global variables (i.e. outside the function)
		- Variables/references on the current call stack 
---
## The Root Set

![[Screen Shot 2022-11-16 at 10.23.21 AM.png]]
- Assuming that the point of compution is the baz() function the Root Set would include both the foo object as well as the baz object
	- The Root Set is used by pushing out from it all things that are indirectly associated to it 
	- Inderectly associated data is, for example, if the Foo object was an array of 1000 customers... these customers would be indirectly related to the Root Set
---
## The two-phase approach 
- In the Mark phase: 
	- Each object that is dynamically allocated has an "in-use" flag associated with it 
		- At the start of a CG cycle all flags are cleared 
	- Beginning with the Root Set, the Mark phase iterably identifies all objects that are associated with it and marks them as `in use`
- The Sweep phase: 
	- The GC must cycle through **all** objects in the heap and check their `in use` flag 
		- If the flag is set, then the object is left alone 
		- if the flag is not set, the GC knows that no current variable (i.e. stack or static variable) is referring to the object
			- This object is then reclaimed for future use
---
### Running the GC 
- 
---
## Argumenting non-GC langauges
---
### The Boehm GC 
---