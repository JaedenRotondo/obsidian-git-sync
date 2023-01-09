# Erlang Programs
## Function syntax
- Functions in Erlang share the basic properties of those in other functional languages 
	- All functions return a value
	- In Erlang this is often a data vale but some functions return the "ok" atom (like Clojure's `nil`)
	- The basic syntax of an Erlang function: 
```Erlang 
func_name (parm1, parm2, …parmN) -> 
	expression_1, 
	expression_2, 
	...
	expression_N.
```
- There are no special keywords to introduce a new function
- Function definitions always end with a "."
- Here is a simple hello_world function
```Erlang
hello_world () -> 
	io:fwrite(“Hello World\n”).
	... 
	
	hello_world().
```
---
## Basic display functionality 
- The most basic method for printing to the console is `io:fwrite`
- fwrite is a function in the io module priovided by te Erlang framework
- The subsitution character is the tilde (~) as opposed to the % in C
	- To display a value in its natural form use ~w
	- Strings should use the 's' char 
		- Otherwise, you will get ASCII values
	- The list of values, like any other list, is wrapped in square [] brackets
- Example io:fwrite uses: 
```Erlang
io:fwrite(“Hello World\n”). 
io:fwrite(“An int: ~w\n”, [43]). 
io:fwrite(“A float: ~w~n”, [77.67]). io:fwrite(“A string: ~s~n”, [“boo”]). 
io:fwrite(“Stuff: ~w, ~w, ~s~n”, [3, 4.5, “cat”]).
```
---
## Functional arity 
- Function arity is done by pattern matching, if there is no match then an error is generated
- If the function has a different number of paramters, we can make these function more or less similar to Clojure: 
```Erlang
foo(X) -> X * X. 
foo(X, Y) -> X * Y. 
foo(X, Y, Z) -> foo(X) * foo(Y, Z).
```
- However, if we want to have several funcitons with the same arity, we can utlize Erlangs pattern matching abilkites
- Note that each variation is terminated by a semi colon, except for the last one
```Erlang
foo({dog, Name}) -> io:fwrite(“Dog: ~s~n”, [Name]); 
foo({cat, Name}) -> io:fwrite(“Cat: ~s~n”, [Name]); 
foo({pig, Name, Weight}) -> io:fwrite(“Pig: ~s, Weight: ~w ”, [Name, Weight]).
```
- Erlang will pick the first function that matches
---
## Higher order functions 
- Like Clojure and other funcitonal languages, funcitons can be passed as arguments and can be returned from functions as well
- Anonymous functions are also allowed: In Erlang, we do this by calling it `fun`
	- And we terminatet the anon function with `end`
```Erlang
lists:map( fun(X)->X*2 end, [1, 2, 3, 4]). ; [2,4,6,8]
```
---
## Modules 
- Erlang applications are organized into modules 
- Modules are defined by the *-module* attribute prefixed with a "-"
---
## Exporting functions 
- Functions can be exported in order to be callable in other modules
	- We use the `-export` attribute 
- A funciton is considered to be private if it is not included in the export list
- When a function is exported, we must also indicate the arity of the function to be exported 
```Erlang
-export(baz/1, bar/1, bar/2).
```
---
## Importing functions
- Similarily, functions are imported using the `-import` attribute
- NOTE: the only purpose of import is tho eliminate the need to fully qualify the funciton with the module name
	- Without it, the function is still accesible as long as the module name is specified
---
## Compiling and running code 
- To run Erlang programs form the command line it is necessary to compile them into .beam files
	- This is essentially like creating .class files for java
- One way to do this is with the erlc compuler
	- RUN erlc foo.erl
---