## Basic Data Types
- Primitive data types in C can be easily understood by the CPU and include ints and floats
- ints can take the form of many different data types (i.e. char, short int, int, long int, long long int) which can use a signed or unsigned form 
- floating points take the form of a float, double, or long double 
---
## Data Type Size
- Although on the surface these basic data types seem to be similar to Java, there is a BIG difference
	- Java runs on a virtual machine that is standardized across all OS and CPU architectures
		- So in Java an `int` is always 4 bytes, it doesnt matter if the native word size of the machine is 32 or 64 bits
		- Meaning that if you port your project to a different architecture it should run the exact same (**this is not the case with C*)
- C uses the data types which are supported by the underlying machine 
	- so an `int` in C might be 2 bytes or 4 bytes or 8 bytes etc
	- This is one of the reasons why C is not considered a portable language 
- C has the `sizeof` operator to determine the size of a given primative data type
	- Note that sizeof can be used with types or variables.
		- When used with data types, the type value must be enclosed in parentheses.
```c
	sizeof (int) 
	sizeof foo // asumming foo is a variable
```
- `sizeof` can also be used with more complex data types as well
---
## C Arrays 
- The syntax for arrays in C is similar to Java as follows: 
```c
	int myArray[10];  
	float foo[140];  
	int bar[foo]; // assuming foo is a variable
	int foo[10][10]; // we can also have multi-demensional arrays 
	float array1[4] = { 10.0, 20.0, 100.0, 0.001 }; // it is also possible to initialize arrays at compile time 
	sizeof foo // number of bytes in the foo array 
	sizeof foo / sizeof foo[0] // number of elements in foo 
```
- Java provides automatic "out of bounds checking", C DOES NOT 
	- If an out of bound element in the array is called, the computer will simply get what is stored in that memory slot (it will be complete junk)
	- (most common occurence of this is an off by one loop)
---
## Composite Data types
- C allows for a composite data type called a struct 
- A struct only has data memebers, it is like a class definition without any methods
	- Structs consist of one or more data types such as ints, floats, doubles, character strings etc.
```c
struct foo {
	int x;
	float y; 
};
struct foo bar; // this sets aside memory of a variable named var of type struct called foo
int structMember = bar.x; // elements of a struct can be accessed using dot notation like Java 
```
- Note that this does not set aside any space, but simply defines the data types labelled in the struct 
- To find the size we can use the sizeof method like `sizeof bar` or  `sizeof(struct foo)`
	- The size might not be what you expect. This is because the compiler will often "pad" the structure of the struct to fit the natural word boundaries of the CPU
		- This makes access much more efficient
---
## Forms of memory allocation 
- All of the data types we have encountetred have been statically defined 
	- Oftentimes applications will need to create new memory dynamically or as is required
- There are 3 types of memory allocation in C 
#### 1. Static 
- Occurs when the compiler knows the variable will exist for the lifetime of the program 
- Since there is only one copy of this variable, the compiler can set aside memory for it at compile time 
#### 2. Automatic 
- Occurs at run-time 
- This kind of memory allocaiton is done for variables that are done inside funcitons 
	- The varibales only exists while the function is being executed
- A run time component which is set aside by the compiler will set up memory for automatically allocated variables when the functions are callled
- We do not set aside memory for these variables at compile time because it would 
	- mean potentially allocating ALL variables to location in memory which is neither required nor effecient. This would occure even if only 1 or 2 functions would be running at a given time. 
	- Recursion would not be possible since each recursive call needs its own version of the function’s variables
- Memory is allocated as required on the process stack (where each function is given its own stack frame)
	- each frame in the stack is dedicated to a function 
	- the base frame of a stack is the main() function 
#### 3. Dynamic 
- Dynamic memory is allocated at runtime and is decided purely by the programmer 
- The memory is taken from the **heap** which grows as required (like the stack)
- You must tell the program how much memory you need, the low level assignment will be done for you 
---
#### The Malloc Family 
- malloc() is a function in the <stdlib.h> library allocates unitialized memory in the order of n bytes 
	- The function returns a pointer to the memory location of the new memory
- calloc() initializes the data to 0 (this is a lot more time consuming)
- realloc() re-allocate a previous memory block to a new size 
	- typically used for resizing arrays 
	- it will maintian the current contents of the data you are resizing if you are making it bigger 
	- Note that realloc will create a completely new memory area, copy the contents of old into new, and then delete the old space
```c
void *malloc(size_t size)
```
- The following function creates an array to hold 10 integers
	- `buffer[2]` will access the third integer in the buffer
```c
int *buffer = (int *)malloc( 10 * sizeof (int) );
```
- `malloc()` will return a `NULL` pointer if the system is not able to allocate the memory for you 
---
#### Pointers and the Heap  
- Note that the pointers to memory which are returned by malloc() are _logical adresses_ not _physical addresses_
	- _logical addresses_ refer to memory location in relation to the program storage space which starts from 0, not the physical space on hardware 
- The compiler has no way of knowing where the memory will actually be stored at runtime, this is something that the computer will handle 
- Note: when you try to access an invalid memory location, the OS will abort your application and print a segmentation fault error.
---
#### Cleaing Memory and the Address Operator 
- Dynamically allocated memory should be returned to the heap when it is finished being used
	- If this is not done, there will be "memory leaks" in the program
		- These are heap areas that never get reclaimed
- To free memory, stdlib provides the `free()` function which takes a void pointer
- the `&` symbol is used on primitive types to find their location in memory, an obvious example of this is used when `scanf()` is invoked
---
#### Character strings and String Basics
# stopped at 5-34