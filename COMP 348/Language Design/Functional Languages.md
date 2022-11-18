## Functional vs Imperative
- The design of the *imperative *programming system is directly based on the Von-Neumman architecture
	- Effeciency is the main concern, instead of the suitability of the langauge for software developement 
- The design of *functional* langauges is based on mathematical functions 
	- A solid theoretical foundation but relatively unconcerned with the architecture of the system it is running on 
---
## Mathematical functions 
- A mathematical function maps a *domain* set to a *range* set
	- The theory is based on *lambda calculus* developed in the 1930s but Alonzo Church 
	- A lambda expression specifies parameters and the mapping function in the following form: 
```lambda-calculus
	λ(x) è x * x * x  
	for the function cube(x) = x * x * x
```
---
## Functions vs procedures
- Mathematical functions and the functions which are used in Python and Java are very different from each other
	- Mathematical functions do not have any side effects 
---
## Side effects
- A side effect is a result that is independent of the function itself
```C 
int foo(int y){
  int x = 3;
  printf(“x: %d, y: %d\n”, x, y);
  return x * y;

}
```
- In the above function, we see that foo prints a string to the display, this is considered a side effect and has nothing to do with the multiplication 
```c
int baz = 4;
int calc(int foo){

baz = baz * 2;

   return foo * baz;
}

// note this line

...
int result = calc(10);
```
1. In the above code, the value of `baz` cannot be used anywhere else in the code as its value might be changed at anytime by the function 
	- "magic" changes to values is often very bad
2. A second issue with side effects is that two invocations of `calc` can produce different results when invoked with the same argument 
	- This is because the function relies on global varibale information and not just function logic 
- We refer to this consistency of functions as *referential integrity*
3. A third issue with imperaitve programming is that the order of functions can matter 
	-  Consider a method that uses the `baz` variable and executes either before or after the `calc` call 
	- On the other hand, if side effects are not possible, then the order of evaluation generally does not matter
		- This gives the compiler a lot more freedom when it comes to compiling/running the code
---
## Motivation 
- 
---
## Higher Order functions 
---
## Recursion, mutability, and purity
----
