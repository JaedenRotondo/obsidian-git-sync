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
---
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
- Manual inclusion is usually placed after the "#include" declearations or at the top of the file 
- Manual inclusion works but it is oftentimes not a good idea for the following reasons: 
1. You need to add a lot of lines to your code manually if you use a lot of functions 
2. Since functions will need to be used in several source files, this manual addition will have to be repeated for every file they are used in 
3. If the API changes (the name of the function or irts signature changes) you would need to make these alterations one by one 
---
## User-Defined Header Files
A ".h" file might look like this: 
```c
/* file1.h */

int do_something(int x);
```
While the C file would look like 
```c
#include <stdio.h>
#include “file1.h”

void my_method(){

  int y = do_something(4);
}
```
- Here we assume that all files are in the same folder as the source file. If not, additional path info would need to be added with the `#include` directive
	- `“#include ../module/file1.h”``
---
### Header Guards 
- In reality your header fies should be written with conditionals called header guards
	- This makes sure that you only include a header file once. If there are more than one copy of a header file it can often cause compilation issues
``` c
#ifndef file1_H_ #define file1_H_

int do_something(int x);

#endif
```
---
## Compiler Warnings
- gcc will oftentimes compile your code even if there are problems as long as they are not fatal
	- This is why its a good idea to include the `-Wall` flag when compiling to print all warnings
	- `-   gcc –Wall file1.c file2.c myApp.c`
- A compiler warning to understand before the exam: 
	- `implicit declaration of function ‘do_something’`
		- This tells us that gcc could not find info about this function so it will just use defaults to produce the object code
---
## Function Visibility 
- Since C is not an OO language, it does not have funtion visibility in the same way that Java does
- By default, all functions are _externally visible_
	- Meaning that they are globally visible to all other files in the application 
	- Using the default visibility for all functions isnt a good idea, it would be equivalent to setting all functions in a Java application to public
---
### Static Functions 
- There are a few ways to change the visibility of a function in C, the simplest is using the keyword `static`
- When using the `static` keyword you tell the compiler that the funciton cna only be referenced or invoked by the source file which it is written in
	- In essense, this is similar to the `private` keyword in Java 
- For example, lets say our function `do_something()` is using a private `helper()` function 
```c
static int helper(){
	return 10; 
}

int do_something(int x){
  int value = helper();
  return value * 2;
}
```
- In this example, `do_something` is visible to the outside world but the helper is not
---
### Function Location 
- You are free to place functions anywhere in your source file 