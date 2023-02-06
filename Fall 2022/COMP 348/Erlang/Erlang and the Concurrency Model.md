# Erlang and the Concurrency Model 
## Thread scheduling
- Traditionally, multi-threaded code runs on top of an operating system that treats eacg thread as an independently scheduled entity
	- For example, database and browser are running at the same time and need two threads each. The OS schedules a total of 4 threads giving each a full slice of the CPU available time.
		- This works for modest thread counts
---
## The Erlang way
- Erlang does not work this way 
	- Erlang might have hundreds of thousands of threads and therefore its noty possible for a typical computer to supprt them all or schedule them 
- Inseated, Erlang virtual machine creates its own super-lightweight threads that each recieve a tiny portion of the time alloted to the Erlang VM process
	- The OS does not know anything aboiut these threads
	- This allows a massive number of threads to be made with almost no resource overhead
	- Note that all threads must share the same block of CPU time
---
## Spawn, send and recieve 
- Erlang refers to its lightweight threads as "processes"
- To create a new process we use the `spawn` function
	- `Pid = spawn(Mod, Func, Args)`
		- This generates a new process that begins running the Func function found in the Mod module with a list of args that can be passed 
		- Note that the spawn function retuns a the process ID of the new process 
- Let's say we have the module `bar` containing the function `baz`
```Erlang 
-module(bar). 
-export(baz/2). 
baz(X, Y) -> X * Y.
```
- From the current module `foo` we can create a process to run `baz`
```Erlang
-module(foo).
start() -> 
PID = spawn(bar, baz, [4, 3]).
```

---
## Process communciation
- Processes "talk" to each other using the `send` and `recieve` functions 
- Note that processes do not share any memory so they have no direct access to the same data structures
- The send function:
	- `Pid ! Message`
		- Where Pid is the proccess ID and ! is the send operator 
		- Message is one or more data items (e.g. a tuple or a list of ints)
- The recieve function: 
	- Uses pattern matching to determin which that arrive is theirs
```Erlang
listen() -> 
	receive {dog, Name} -> 
		“Mr” ++ Name; % create a new string 
		{cat, Name} -> “Ms” ++ Name % create a new string 
		end.
```
- NOTE BENE: 
	- `listen` is not a special keyword, we could have called this function anything we wanted
	- `recieve` consists of one or more patters
	- If no match is found, the message goes into the "save" queue and can be checked again at a later time
---
## Continuous recieve loops
- A recieve can be invoked in two ways
	1. Periodically: we check for the message and if its not there we go back and do other things
	2. Continuosly: (like a server application), we would want the new process to sit in a recieve loop and wait for many messages (perhaps loop forever)
- Example of Option 2
```Erlang
listen() -> 
	receive {dog, Name} -> 
		dog_func(Name), % do something 
		listen(); 
	{cat, Name} -> 
	cat_func(Name), % do something 
	listen() 
	end.
```
### Two-way communication 
- We can allow for two0way communciation by including the sender's process ID with the message
- Erlang provides the self() function to capture the process ID of the current process
- Sending a process would look like: 
```Erlang 
-module(foo). 
start() -> 
	PID = spawn(bar, baz, [4, 3]), 
	PID ! {self(), “Important Info”}.
```
- On the other side we can capture the ID and return a message
```Erlang
listen() -> 
	receive 
		{Sender, Msg} -> 
			do_something(Msg), 
			Sender ! “Thanks” 
end.
```
---
## Receive timeouts
- One problem with recieve is if the expected message never arrives (e.g. the send crashes)
- While its not a true deadlock, the program may hang if it waits forever for something that will never come (the queue remains empty)
- To adress this, Erlang provides a "timeout" mechanism on the recieve that can break if the message foes not arrive in a specific time period 
	- Below is an exmaple where we set the timeout to 2000 miliseconds
```Erlang
listen() -> 
	receive 
		{Msg} -> 
			do_something(Msg) 
	after 2000 -> % break after 2 seconds 
		do_something() % do this and finish 
end.
```
---
## Process registration
- So far it has only been possibel to communciate within a parent/child ID 
- However, preocesses need to communicate with "non-related" processes 
- Erlang provides a name registration service for this purpose
	- This allows a process ID to be associated with a name/label 
		- Note that the process names need to be known a priori
- The relevant functions are
	- register(atomName, ID) 
	- unregister (atomName)
	- whereis(atomName) % returns PID or undefined 
	- registered( ) % returns a list of all processes
```Erlang
start() -> 
	register(woof, spawn(myLib, dog), 
	register(meow, spawn(myLib, cat).
```
```Erlang
dog() -> Cat = whereis(meow), Cat ! “dog says woof”.
```
---
