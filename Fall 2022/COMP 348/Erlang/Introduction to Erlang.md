## What is Erlang? 
- Erlang is a functional programming language with emphasis on concurrency and high availability/ fault tolerance (highly scalable!)
- It was developped by Ericcson in the 1980s specifically for the telecommuncation industries needs (Erlang was open-sourced in 1998 )
	- However it used as a general purpose programminglanguage used by companies like Amazon/Facebook/Whatsapp etc
---
## Virtual machine model 
- Like Java, Erlang runs on top of a virtual machine model called BEAM. 
- There are two ways of running Erlang programs
	1. On an interactive command line called Eshell
	2. By compiling the code and running it with erl.
---
## Erlang sytnax 
- Like Clojure, Erlang does not have any type declarations, they are inferred from context
### Types
- Integers (arbitrary length)
- Floating point values (held internally as doubles)
- Strings (surrounded by double quotes)
- There are NO boolean types, but there are constants returned from conditional checks
---
### Expressions
- Unlike Clojure, Erlang does not use LisP-style prefix notation for expressions 
	- So Erlang uses`(2*4),not(* 2 4)`.
- It **is** possible to bind a value to a variable 
- Note Bene:
	- These variables can only be assigned once 
	- The variable names *must* start with an uppercase
- Erlang uses several "seperators"to destinguish elements from expressions
	- Commars are used inbetween function arguments and between expressions in a function body 
	- Semi colons are used between alternate forms of functions, or "arities"
	- a period with a white space after it is used to terminate a complete expression
---
### Whitespaces 
---
## Data structures
### Tuples 
```erlang
0.  P = {person, “John Smith”, 43}.
```
- Note that, unlike a C struct, there are no labels associated with the struct(E.g. no name/age labels)
- In practice, Erlang programmers use an "atom" as the first element of a tuple
	- An atom is essentially a constant label or a string
	- It must pe a lowercase letter
#### Extracting values from tuples 
- Erlang makes extensive use of pattern matching 
	- To find a value from a tuple we can use the following code: 
```erlang
P = {person, “John Smith”, 43}.
{person, _ , Age} = P.
% Age now = 43
```
---
### Lists
- Lists can be created using square brackets, where each element is seperated by commas
- Lists can contain other types and data structures and can be of arbitrary length 
```erlang 
List1 = [14, 12].

List2 = [“abc” | List1].

[TheHead | TheRest] = List2.

% TheHead = “abc”, TheTail = [14, 12]
```
- There are several list functions that can be used in Erlang 
	- Append
	- Delete
	- Sort
	- Split
	- Reverse
---
### Maps
- Maps behave like the comparable structures in python and clojure
- The basic syntax is 
	- `#{key1 Op Val1, key2 Op Val2, ...key3 Op Val3}`
	- Operator can either be a > or =>
	- Note that there is no record name in the first position so its not a record, although the syntax is similar 
```erlang 
M1 = #{man => “joe”, women => “sue”}. 
...  
M2=M1. %M2 is a copy of M1
```
---
### Records
- Records are like tuples but e can associate labels with values
- They are different than other data structures in Erlang because they **do** have a declaration
```erlang 
-record(name, {
  key1 = val1, % val1 is a default
  key2 = val2, % val2 is a default
  ...
  key3, % no default for key3
  ... 
  }).
```
- Below is the declaration of a person record with a default provided for the name 
- To create a record, we use the `#{ }` syntax.
```Erlang
-record(person, {name = unknown, age}).
R1 = #person{}. % name = unknown, age = undefined
R2 = #person{age = 99}. % name = unknown, age = 99
Age = R2#person.age. % Age = 99
```
#### Importing record declarations
- Record declarations are usually declared seperately and then included in the current files 
	- This is a lot like C, Erlang has its own Preprocessor
```erlang
-include(“person.hrl”).
...
R1 = #person{}. % name = unknown, age = undefined
```
- We use the "-include" syntax with the .hrl file extension

---