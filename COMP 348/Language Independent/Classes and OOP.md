## Classes, Objects, and Methods
- Objected oriented languages define classes that expose a set of methods that can, in turn, be invoked by calling applications.
- OO style provides significant improvements in code isolation and re-use, including:
	- Simple inheritance logic
	- Polymorphic methods
- We see methods as being contained within the object 
	- and that methods act upon data members that are also inside the object (this is wrong)
---
## The logical view of classes and methods
![[Screen Shot 2022-11-15 at 11.14.29 AM.png]]
- When the Dog object is instantiated, values are provided for the name and age 
	- The associated methods can then act on the values of the specific object 
#### The physical implementation 
- At the level of machine code, there are obviously no notions of classes or objects 
- In the simplest case, an object will be similar to what a `struct` is in C
```c
struct foo {
  type member1;
  type member2;
} 
```
- In practice, class methods are just plain old functions, just as we saw in C.
	- Note that methods of a class are just chunks of code that are stored in memory a-contiguously 
- With this information it makes sense to construct a class that holds the variables and pointers to the methods of that class
	- This is a waste of space. Imagine if we have tens of thousands of objects, it would mean we need to have the same copies of the pointers in each object
	- Because of this, classes and objects represent descrete structures
		- A class structure
		- An object structure 
- 
---
## Method implementation 
---
## Class and object structres
---
## Efficient implementations
---
## Linking methods and data 
---