# Clojure Programs
## Absence of loops
- It is always best to use the core functions in Clojure, but sometimes we need to make custom functions. The question arises (since we don't have looping mechanisms), how do we iterate over data? 
---
## Clojure recursion
- When loops are not available, recursion is used instead
- How would we reverse the values in a vector of ints? 
```clojure
(defn flip
	[numbers]
	(if (empty? numbers)
	[]
	(conj (flip (rest numbners)) (first numbers))))
```
---
## Use of recur
- Note that basic recursion can be implemented simply by making a recursive call
- However, in cases where the recursion is the last epxression in the function, it is reccommend you use the *recur* function
- By using recur, tail-call recursions are transformed into something resembling a while loop
---
## Libraries and namespaces
- In Clojure, we refer to a collection of functions as a library 
- Each library is associated with its own namespace
	- like a java package
- Namespaces are defined at the top of your clojure library file with
	- `(ns myproj.foo)`
---
## Hiding functions
- Clojure has no public or private keywords
	- So all functions are vars are public by default
- If you want to indicate that a funciton is not part of the public API use `defn` instead of `def`. This only works for functions
- Using `^:private` as a metadata taf for the compiler also works for data
```clojure 
(defn- boo [y] (* (* y y) y)) 
(def ^:private boo [y] (* (* y y) y))
```
---
## Importing Clojure and Java libraries
- To import other libraries, we augment the current namespace definition 
```clojure
(ns test.foo (:require test.bar)) ; a library of functions in test/bar 
(test.bar/myfunc x) ; myfunc is a funcion in test/bar
```
- We can use the refer option to use the funciton without qualifying it as something.
- The same logic is used to import libraries from the Clojure framework itself
- 
---
## Instantiating Java classes 
- It is also possible to import Java classes into your Clojure code
	- For this we use `:import` instead of `:require`
---