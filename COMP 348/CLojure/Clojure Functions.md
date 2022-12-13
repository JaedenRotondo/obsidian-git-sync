## Clojure Functions
### Basic Format
```Clojure
; standard form of function 
( defn func_name 
	“doc string” ; standard documentation 
	[parms] ; zero or more 
	(expression 1) ; function body 
	(expression 2)
	… 
	(expression n))
```
- The "doc string" is like the official documentation. It is located after the `defn` line
- There is also a `doc` function that can be used to display documentation for a given method
---
### Parameters
- Clojure functions can take any number of parameters
- Clojure also allows for _arity overloading_
	- This allows for a multi paramter version of a function to be used. Its like overloading in Java except the datatypes are irrelevant, its just based on the number of paramters
```Clojure
; basic arity overloading 
( defn func_name
	([arg1] ; one parm version 
		(expression)) 
		
	([arg1 arg2] ; two parm version 
		(expression)))
```
---
### Passing and returning functions
- 
---
### Closures
---
### Map and reduce
---
### Core functions
---
### Lazy functions
--- 