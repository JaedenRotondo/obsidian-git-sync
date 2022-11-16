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
- In practice, the GC can be invoked in various different ways 
	1. Only when it is determined that memory is low 
		- The memory allocator keeps use of how much memory is used and when the next request for a new object is made, the GC can be invoked if necessary 
	2. On a pre-defined schedule 
		- The point here is that because the GC steals processing cycles from your application, it does not run continuously
---
### Downsides of Mark and Sweep 
- Mark and Sweep works well in terms of memory management 
- But they can be costly for large applications 
	- Its an "all or nothing process" that must always commit a full cycle 
- In practice, various optimizations can be done 
	- For example the *tri-colour* approach is used in which candidates for reclamation are iteratively moved between three sets until it is determined that certain elements are definetely not required anymore. 
		- The benefit of this approach is that the work can be performed in smaller stages
	- It is also possible to use a *generational technique* where the age of the objects impacts the frequency of testing
		- older objects are determined to be more likely to require long term storage and are therefore checked less often 
---
## Argumenting non-GC langauges
- For languages like C which do not have a native garbage collector, it is necessary to use functions like free()
- It is also possible to create an external collector that they compiler does not need to support directly
	- One example of the this is the Boehm garbage collector 
---
### The Boehm GC 
- The three main properties of the BGC are
	1. Uses Mark and Sweep Algorithm 
	2. Black Box: it is not integrated into the compiler 
	3. Conservative: it will do its best  "guess" which objects can be reclaimed
		- It may have false negatives
		- It will never have false positives
- BGC replaces the standard malloc calls with its own functions that act similarily but keep track of stored memory 
 ![[Screen Shot 2022-11-16 at 11.22.45 AM.png]]
- If the GC finds no possible address that could point to the foo memory, it will safely release foo
- For boo, it can not be sure, so it will NOT release boo’s memory
- We might be wrong about boo, if we are then it would be considered a *transient memory leak*
	- However, it is transient (temporary) in that once this function completes, its stack frame will be cleared and the false positive disappears.
---
## Final thoughts
- Although garbage collection is very useful, it is not used in fast systems (like operating systems, database management systems for example) because they are time intensive compared to manual memory allocation 
- For this reason C does not usually use collectors like BGC
- Python uses a different type of garbage collection that is non-traceable as opposed to Mark and Sweep 