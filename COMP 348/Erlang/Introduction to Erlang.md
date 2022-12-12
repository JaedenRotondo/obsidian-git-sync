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
- 
---
### Whitespaces 
---
## Data structures
### Tuples 
---
### Lists
---
### Maps
---
### Records
---