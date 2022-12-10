## Basic Structure of a Python Program

### Indentation 
```Java
if(total > 100)    // update
    z = 2;
	y = 4; // whether this line will be terminated is depending on the language 
```
## Flow Control 

### For Loop 
```python 
for x in animal:
   print “Animal is a “, x
```
- For loops are often used with the Range() function: 
```python 
for x in range(5):
   print “Count is “, x
```
- Range is inclusive/exclusive meaning that the first number is included and the last number is not 
### While Loop
- The contents of a while loop are indented
- There is no need for the use of delimiters in conditional expressions
- The while loop ends when the indentation ends
```python 
	while x < 1: 
		z=2
		y=4
```
---
## Functions 
```python 
def foo(number):
   print “my number is ”, number
   return number * 2
```
- Functions are introduced with the `def` keyword
- parameters require no type 
- Return types are not explicitly specified
	- Functions return `None` by default 
- Functions are pass-by-value 
	- pass by value means you are making a copy in memory of the actual parameter's value that is passed in, a copy of the contents of the actual parameter
- Note that functions can be assigned to variables 
	- If you have a function called foo()
		- foo2 = foo // is allowable and will become an alias to foo()
---
### Default arguments 
- Python allows programs to incude _default arguments_ which subsitute arguments for the function if they are not specified
	- Defaults are specified as “var=default”
```python 
def foo(num, text=“test”, thing=43.5):
   print “my num is ”, num
   print “my text is ”, text
   print “my thing is ”, thing
```
- Note that if no default is provided in a function, then an argument must be provided
- Note that if there is a default for any of the arguments in the signature, then all arguments must have defaults. This is incorrect: 
```python 
def foo(n, x=2, m) # invalid syntax  
foo(3, 4) # no way to know if 4 is x or m
```
- If a subset of arguments that are inputted will be assigned from right to left 
	- This can be altered by using the following syntax
	- Say we have def foo(n, m=4, z=3):
	- We could call foo(3,z=7) m would be 4