## Basic Structure of  a C Program 
- Hello World
```
int main(int argc, char* argv[]){
	printf(“Hello World\n”);
return 0; 
}
```
- The `main` function is the starting point of all C programs 
	- It always returns an int 
	- If a return value is not provided, it is automatically set to zero 
## Trivial Compilation 
- C programs are compiled into _object code_ by a compiler
- `gcc` is "GNU Compiler Collection" and clang are common C compilers
	- All should understand the same source files, assuming they conform to a recent C language standard.
## cpp the C Pre Processor 
- cpp examines source code before the compiler
	- It identifies any special cpp _derectives_
	- It transforms your source code into intermediate source files
- cpp is automatically called by gcc when you compule your source files
	- It can be invoked independently with the folliwng command 
		- ` cpp hello.c`
### cpp derectives
- cpp understands 20 derectives, each begins with the  `#` symbol
- There are 3 types of derectives
	1. File inclusion 
		- `#include<file>:` paste a file directly into your source code
	2. Macros
		- `#define<content>:`These are pure textual substitutions 
			- definition of constants
			- compact form of very simple functions 
	3. Conditional Inclusions 
		- `#ifndef<label>:` will possibly include the content that follows
		- This derective will include a label if it is not already defined in the source file
		- Variations of `#ifdef` as well
- Note that cpp language is never seen by the compiler, nor is it int he langauge of C 
	- every derictive is translated into its relative C programming language prior to compilation 
### Head files
- Header files include code that is derieclty placed into the C programming during preprocessing 
- Inclusion of standard header files can be written as follows
	- `#include <stdio.h>` where stdio.h is the source file
	- Standard header files are located in pre-defined that cpp and the compiler can always search for 
		- This is why there is no additional path thats included in the file name 
	- If the file is standard, we use the `<>` notation as opposed to `""`
- The `stdio.h` header file is for input/output functions 
- Here is a list of common header files and there uses: 
	- stdio.h: input/output  
	- stdlib.h: general utilities including memory management and random numbers
	- string.h: character string processing
	- math.h: common math functions
	- time.h: basic time/data utilities
- 
## File Inclusion 
## The standard libraries 
