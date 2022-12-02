## Clojure and the JVM 
- Clojure was designed as a modern dialectic of LISP 
- Its implmented on top of the Java Virtual Machine, although its syntax is simple it might seem unfamiliar compared to Java. 
- It has direct support for concurrency 
	- Meaning that it is suitable for multi-core platforms
---
## Expressions and Forms 
- Clojure code is constructed as a series of expressions of _forms_
- Each expression consists of 2 basic elements 
	- Data types or data structures
	- Some operation on this data
- Expressions are always written in parenthesis 
	- The first value in the parenthsesis is the operaiton
	- The remaining values are data that the operation will act upon
```clojure
(+ 2 2)
; Note the following about the expression: 
; 1.) The expression is closed in "()"
; 2.) There are no commas normally, things are seperated by whitespace
; 3.) Basic math notations use prefix style instead of infix
```
---
## The REPL
- REPL is like a command line interface (similar to what Python has)
	- READ-EVAL-PRINT-LOOP
- you can execute expressions one by one
---
## Clojure return values
- All expressions in Clojure return a value 
```clojure 
; simple Math

(+ 1 1)
(- 2 1)
(* 1 2)
(/ 2 1)

; Equality testing

(= 1 1) ; => true
(= 2 1) ; => false

; negation

(not true) ; => false
```
- You can also print statements in Clojure
```clojure 
(print “woo”)

; => “woo”
```
- Note that the print statement returns `nil`
---
## Basic Clojure types
- Clojure provides some primitive data types that you would expect 
	- Integer
		- corresponds to `long int` in Java
	- Float
		- corresponds to `double`
	- String
		- Always inclosed in ""
	- Boolean
		- True or False
	- `nil` is used as a null value 
- Note that types are not explicilty defined, Clojure will interpret and assign types to values 
---
## Binding names to values
- As previously noted, functional languages do not generally manage a global state
	- Still, it can be useful to associate values with labels so that they can be referenced later
		- `(def name value)`
---
## Functions 
### Trivial Functions
- All functions follow the following syntax
```clojure 
x( fn [parm list] body)
```
- A hello world function would look like `( fn [] "hello world"`
- Clojure does not have any return statements 
	- In the case of a function, the return value is always the last expression within the function
	- In this case, our function returns a string "hello world"
- Note that to invoke an anonymous function like above, you must wrap it in parenthesis 
---
### Function names
- We can name functions using the `def` keyword
- here is a definition of a hello world function 
```clojure
( defn hello [] “hello world” )
```
---
## Control flow
#### If Form 
```
( if boolean-form 
	then-form
    optional-else-form)
```
- The else form is optional, and can be removed. 
#### Do Form
- Clojure provides a Do form in order to a permit a sequence of expressions to be defined.
```clojure 
( if (> 5 0) 
	(do
       (println “looks good”)
       “positive”)
    (do
       (println “looks bad”)
       “negative”))
```
- The return value in this case is the last expresion in the compound funcitno
	- If we re
---
## Truthy and Falsey values
---
