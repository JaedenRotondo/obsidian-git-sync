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
---
## Method implementation 
- In practice, class methods are just plain old functions, just as we saw in C.
	- Note that methods of a class are just chunks of code that are stored in memory a-contiguously 
- With this information it makes sense to construct a class that holds the variables and pointers to the methods of that class
	- This is a waste of space. Imagine if we have tens of thousands of objects, it would mean we need to have the same copies of the pointers in each object
	- Because of this, classes and objects represent descrete structures
---
## Class and object structres

- A class structure
	- The class object will store the pointers to all methods that the Instance object will be able to access
	- And possibly any shared "class variables"
- An object structure 
	- Will only include instance variables of objects 
---
## Efficient implementations
- There is a problem with the above implementation
	- When a function is invoked, how does the function know which object invoked it? 
	- For example, if there is a object function for printing the name of a dog. How would the function know if "Max" or "Molly" invoked the function 
	- There is no information about this on the stack 
---
### Linking methods and data 
- In practise we solve this by extending the method signature to include a reference/pointer to the object upon which the function should operate
	- This is usually the first parameter of the function call
	- This is the reason why Python needs the "self" argument in the first position of the param list 
		- In Java and C++ they use the argument `this`
---