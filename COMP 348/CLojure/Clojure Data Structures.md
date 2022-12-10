## Clojure Data structures
### Maps
- Clojure maps are equivalent to pythono dictionaries 
	- That is, the provide key/value lookup pairs
- An empty map can be declare as `{}`
```clojure
; profession map
{
 “John” “professor”
 “Sue” “doctor”
 “Ahmed” “astronaut”
}
```
```clojure
; number map with int keys
{
 1 “one”
 2 “two”
 3 “three”
}```
```clojure
; function map
{
 “func1” (fn [] (println “func1”))
 “func2” (fn [] (println “func2”))
}
```
- In practice maps are used with keywords
	- keywords are essentially strings but they allow for faster lookup 
	- keywords are case sensitive
```clojure
; profession map
{
 :john “professor”
 :sue “doctor”
 :ahmed “astronaut”
}
```
---
#### Map Lookups 
- We use the `get` function for map lookup 
```clojure 
(def jobs {
 :john “professor”
 :sue “doctor”
 :ahmed “astronaut”
})
(get jobs :sue) ; => “doctor”
(get jobs :Sue) ; => nil
```
- The output of the following function is null (because of println)
```clojure
; function lookup table

(def funcs {
 :func1 (fn [] (println “func1”))
 :func2 (fn [] (println “func2”))
 :func3 (fn [] (println “func3”))

})

; execute the third function
((get funcs :func3)) ; => func3
```
---
#### Nested maps
- Nested maps can be accessed using the `get-in` function 
```clojure
(def nest {
 :a “eh”
 :b {:dog “fido” :cat “fluffy”}

})

(get nest :a) ; => “eh”
(get nest :b)

  ; => {:dog “fido”, :cat “fluffy”}
(get-in nest [:b :cat]) ; => “fluffy”
```
- You can provie _default values_ for lookup values
	- `(get jobs :bill "bill not found"`
- You can use keywords like a function instead of using `get`
	- `(:john jobs)`
- As noted, Clojure uses whitespaces to seperate code
	- Commas are considered white spaces as well, it is soemtimes used anyway to make code more readable
```clojure
{:john “prof” :sure “doctor”}
;vs
{:john “prof”, :sure “doctor”}
```
---
### Vectors
- A vector is essentially an array delimited by square `[]` brackets
- There are two techniques for creating vectors in Clojure
```clojure
(def myVec [1 2 3])
(def myVec (vector 1 2 3))
```
- We can use the `get` function to return values, if you are trying to return a value at an index thats out-of-bounds - `nil` is returned
- Note that we can put anything in a vector, including functions
```clojure
(def things [
 “dog”
 2
 (fn [] “do something”)
])
(get things 0) ; => “dog”
(get things 1) : => 2
(get things 10) : => nil
```
---
### Lists
- Lists in Clojure are delimited by parenthesis `()`
	- To create a list with parenthesis though, you must prefix it with a single quotation character `'` to differentiate it from a function 
```clojure 
(1 2 3) ;=>error:1isnotafunction 
‘(1 2 3) ; => valid list  
(+ 2 2) ; => function call  
‘(+ 2 2) ; => valid list
```
- Note that, like vectors, it is also possible to define a list using the (list list_content) form.
	- For example, you can include list list_content as well as different datatypes
```clojure
(def foo ‘(2 {:a “eh”, :b “bee”} 3))
```
- Lists have no indexing 
	- Therefore there is no `get` function for lists 
	- Instead we use the `nth` function 
		- out-of-bounds error generated for invalid indexes
	- list `nth` is slower than `get` on a vector
### Sets
##  Creation and access methods
### Immutibility 
- Clojure data structures are immutable
	- One never changes the calues of a data strucute. If changes need to be made, a new data structure is created
- Clojure provides a function called `conj` (conjoin) to add a value to lists and vectors
	- In practice, `conj` adds a vale to the _beginning_ of a list and the _end_ of a vector... Why? 
#### Effeciency
- Although Clojure makes copies of data structures (generally a very slow process if it needs to be done thousands of times)
	- To do this, we will create a new data structure that simply consists of a new path for the updated element
	- We will then connect the remaining paths to the original index
	- To find the updated element, we will use the new index (see path in blue)
- ![[Pasted image 20221210170936.png]]
- Now, we have two distinct data structures, with the second allowing access to the updated elements.
	- Access time is log(x) which is very good. Of course not as fast as the original O(1) of the vector though