- C is an imperative and procedural programming language 
	- _Imperative_: A langauge which uses a series of statements to alter the state of the program. This is in contrast to declarative programming languages which simply indicate which output you want to see. 
	- _Procedural_: A programming langauge which is written in a way that incldudes procedures and subroutines which can be called at a later time at the point of use
---
## Functions 
- Functions have the following standard form: 
```c
return_type name(parameter_list){ 
	function_body
}
```
## Multi-File C
- All files in C are compiled seperately into one executable 
	- Since files are ndependent from each other, there might be tens of thousands of files which requires a very complex makefile environment 
		- makefiles use a special syntax/language to define how C/C++ source files should be compiled and linked into a single application or library
- Simple multifile compilation is structured like this 
	- `gcc file1.c file2.c myApp.c`
		- This assumes there are 3 c files with one of them including a main() function
- You will get an implicit function declaration error if you try to invoke a function that is in a different file without telling the compiler the size and return type of the function you are using 
	- We can solve this by calling the source file with the "external" function declarations it will be using 
---
### Method 1: Manual Inclusion 
```c
#include <stdio.h>

int do_something(int x); // prototype

void my_method(){
  int y = do_something(4);

}
```
## User-Defined Header Files
## Compiler Warnings
## Function Visibility 
