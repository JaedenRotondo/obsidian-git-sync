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
- Because functions are first class entities in clojure, they can be passed as argumnents without any special syntax
- Example: 
```clojure 
; passing functions 
(defn outer 
	[inner data] ; parm1 = func, parm2 = data 
	(inner data)) ; inner() is called on data
```
- Clojure allows for functions to return other functions
	- To do this, the new function definition must be the last expression of the body of the outer function
	- Typically the inner function is anonymous
```
(defn outer 
	(expression 1) 
	(expression 2) 
	(anonymous inner function))
```
---
### Anonymous functions
- Anonymous functions are quite useful, map is an example
	- map applies its funtion argument to each othe the elemnts of the associated sequence
---
### Closures
-  Partially instantiated functions that store the variables that are currently in the scope of the outer function
- Closures are like instance variables in a function invocation 
- Clojure is not object orineted but this is a work around 
---
### Map and reduce
---
### Core functions
- Here are some core functions to be aware of for the final: 
	- (first *sequence*)
		- `(first [4 6 2 1])` gives 4
		- Returns the first element of a sequence 
	- (rest *sequence*)
		- `(rest [4 6 2 1])` gives ( 6 2 1)
		- Returns all elements of a sequence except for the first node
	- (cons item *sequence*)
		- `(cons 3 [4 2 5 2])` => (3 4 2 5 2)
		- cosntructs a new list by adding the argument as the first element
	- (take n *sequence*)
		- `(take 2 [4 3 6 7])`  => (4 3)
		- Returns a list with "n" first elements of the sequence
	- (drop n *sequence*)
		- `(drop 2 [4 3 6 7]) ` => (6 7)
		- Returns a list with the first "n" elements of the sequence removed
	- (take-while func *sequence*)
		- `(take-while even? [2 4 5 6 7])` => (2 4)
		- Extracts the elements of a sequence until the function does not return true (truthy)
		- There is another way of writing the take-while example
```clojure
(take-while #(< % 5) [ 3 1 4 6 7]) ; => (3 1 4)
```
- #( ) is a shorthand for defining anonymous functions
- The % sign is used to capture the argument passed into the outer function
### Core functions continued
- (some func *sequence*)
	- `(some even? [3 4 5 6 7] )` => true
	- Will determine if any of the sequence yields true for the function and returns the result
- 
---
### Lazy functions
- In many cases, it would be inneficient to materialize a massive sequence in order to then call a simple function on it
- In many cases, Clojure will emply "lazy sequences" so that it only materializes what it needs to 
```clojure
(first (range 1000000)) ; => 0 ; instantaneous response 
(last (range 1000000)) ; => 999999 ; noticeably slower
```
--- 