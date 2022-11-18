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
- In the above code, the value of `baz` cannot be used anywhere else in the code as its value might be changed at anytime by the function 
	- "magic" changes to values is often very bad
---
## Higher Order functions 
---
## Recursion, mutability, and purity
----
