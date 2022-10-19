# Python 
---
## Welcome to Python 
- Python is a high-level, interpreted, general purpose programming langauge
---

## Guiding Principles fo Python Design 
- This has been formally codified
	- The Zen of Python 
	- A collection of software principles supported by the language 
		- Easy to understand, easy to read, small number of ways to do complex things, obscure things are for libraries, light clean easy to understand practical language
	- It's syntax is largely self-documenting 
	- As much as possible, Python supports good software engineering practices 
1. An imperative langauge with syntax roughly similar to Java/C
2. Extremely readable code
3. Objec orientation *non OOP possible*
4. Automatic memory management (i.e. garbage collection)
5. No static typing 
	- Suitability of actions/methods is determined at runtime 
---
## Python Data Types

### Ints and floats
- Python provides support for the standard integer and floating point values
- However, Python does not require explicit type definition, like int, flot and double
- Python determines the internal storage format for number automatically 
- For example, in most cases, integer values are stored internally in a C signed ling int
- It is also possible to provide an "L" suffix after an integer value
	- There is no limit on the size of such long integers (other than the size of memory)
	- Internally, this will be stored as an array of digits
	- Procssing of Python long integers is slowers becasue it is using software libraries instead of hardware
- Dynamic ! 
---
### Strings
- Strings inpython are enclosed either in single quotes or double quotes
- Escape characters can be placed in strings
- You can also "turn off" escape characters by using *raw* strings 
	- we preface the string with 'r', example: r"This is a string"
	- It is possible to enclose strings in a triple quote (using either single quotes or double quotes)
		- This will concatenate all lines into a single string
		- The interpreter will automatically add the new line characters
			- To prevent this, you can add a “\” at the end of eachline
```
myNote = “””
   Roses are red
   Violets are blue
   yada yada yada

“””
```
- Strings can be concatenated with the "+" operator
```
s1 = "big" + "dog" #bigdog
s2 = "big" + s1 #bigbigdog
s3 = 3*s2 #bigbigbig 
```
- You can index from the back of the string with a negative array index
- The indexing concept is extended to support the notion of string slices 
```
s1 = “bigdog”
s1[2:4] # gd
s1[2:] # gdog
s1[:4] # bigd
s1[-2:] # og
s1[2:-2] # gd
s1[2:2] #
s1[2:44] # gdog note that this works
```
- IMPORTANT: Slices used inclusive/exclusive format
	- In other words, the start index is inclusive, while the end index is exclusive

#### String Immutability 
- As is the case with Java, Python strings are immutable.
- So this does NOT work
```
s1 = “bigdog”
s1[2] = “G”  
```
Instead, you can make a new string like this: 
```
s1 = “bigdog”
s2 = s1[:2] + “G” + s1[3:]
```
## Lists and Composite Data Types
- Internally, lists are not likely to be implemneted as actual linked lists
- Performance on linked list can be quite poor, particularly for indexing operations 
- In CPython, the list is built using a dynamically resized arrat
	- Here, each cell in the array holds a pointer to the object that is associated with that index
- List can hold anything, it is possible to mix types within a list
- You can also nest lists as follows 
```
list3 = ["foo", "boo"]
list4 = [1, 2, 8, list3, [12, 9]]
```
- Unlike strings, Python lists are mutable,
	- you can change the contents of a list without creating a new list
```
list3 = [“foo”, “boo”]
list4 = [1, 2, 8, list3, [12, 9]]
list4[4] = 16
print list4 # replaced [12, 9]
>>> [1, 2, 8, [“foo”, “boo”], 16]

list4[1:3] = [“do”, “not”]
print list4 # replaced [2, 8]
>>> [1, “do”, “not”, [“foo”, “boo”], 16]
```
---
#### List Methods
-    Lists also support a group of methods that provide advanced functionality.
-   These methods are invoked using the standard OOP-style “.” notation.
- List methods include (where “list” is the name of the list variable):
	- list.append(x): add x to the end of the list  
	- list.extend(L): append list L to current list
	- list.insert(i, x): insert item x at position i 
	- list.remove(x): remove first occurrence of x
	- list.pop(): remove and return the last element 
	- list.pop(i): pop element at position i  
	- list.index(x): return first index position of x
	- list.count(x): number of instances of x – list.reverse(): reverse the order of elements

– list.sort(): sort elements “in place” (optional args are possible with the sort method in order to provide customized sorting)

---
### Computational Complexity 
- It is often useful to be aware of the underlying cost of various operations
- 