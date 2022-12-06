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
- 
### Lists
### Sets
##  Creation and access methods
### Immutibility 
