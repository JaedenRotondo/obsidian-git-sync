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
## Lists

