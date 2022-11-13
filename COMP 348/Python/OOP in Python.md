## Object Oriented Programming in Python
- Python has object oriented capabilities and in many ways acts simpler compared to Java and C++
	- However, there are a few caveats that might throw a user off if they are expecting Java-like functioning
## Simple class definition
- The syntax for defining a class in Python is trivial: 
```python 
class class_name: 
	statement 1
	statement 2 
	# ...
	statement n

```
---
## Instantiating and using objects
```python 
class Foo:
  x = 43
  get_x(self):
     return self.x
```
- Here is another example of a simple class that has a function which returns the value of its "class member" `x`
	- Here, self is not a keyword in Python, but it is the standard word 
	- The first parameter in Python is always the reference to the object that will be instantiated from the class definition 
- Why do we use `self` in python but not in Java or C++? It's because the latter two languages do this under the covers with the compiler but we will see later that it is necessary in Python so that the methods act upon the 'right' object
---
- Creating an object from a class definition is simple: 
```python 
myFoo = Foo() # there is no new keyword in python 
x = myFoo.get_x()
## the following two statements are equivalent 
myFoo.get_x()  
Foo.get_x(myFoo)
```
- Classes are recorded in module files, just like any other code
---
## Member Variables
1. Class
- Variables defined outside of any methods are class variables, there is no keyword for this 
	- Note: these variables must be accessed using the `self` reference, otherwise you are creating a local varibale within the method itself
1. Instance
- Objects instantiated from the previous `Foo` class do not have private version of these variables
- so ANY changes made to the variable outside the class definiting will affect ALL such objects
---
## Initialization 
- In Python, we use a method called `__init__` to define a constructor 
	- So our previous example would be 
```python 
class Foo: 
	x = 43
	__init__(self):
	self.stuff = "stuff"
	
	get_x(self):
	print self.x
```
- When we instantiate a Foo object, the `__init__` method will run 
	- In this case a new variable called `stuff` will be created and added to the object instance
- What about multiple constuctors? There is only one `__init__`per class
	- This can be done using the following standardized syntax
	- `init1()`, `init2()`,`__init__(self, person=None)` etc.
- `__init__` is an example of a method that is automatically applied to the class. There are other methods like this, they are often used in operator overloading 
---
## Operator Overloading 
## Inheritance 
- How do we create subclasses in Python ? 
	- Below, we see an example of a class Foo that extends a base class Baz
```python 
class Foo(Baz):
  x = 43

  __init__(self):
     Baz__init__(self)
     self.thing = “thing”

  get_x(self):
     return self.x
```
- In this exmaple, Foo inherits all of the Baz functionality 
	- I.E. its methods and class variables
	- Instance variables would only be inherited if `Foo __init__` calls the `Baz __init__` method 
- Note that multiple inheritance is possible in Python 
	- you can add multiple Base classes with the () notation 
	- however its not a good idea because things get confusing quickly 
---
## Visibility 
- There are no visibility keywords in python, such as `public` or `private` or `protected`
	- Everything is public, if one has reference to an object it can be modified
- There are privacy _conventions_ in python, such as using the underscore for any variables (e.g. `_amt` or `_total`)
