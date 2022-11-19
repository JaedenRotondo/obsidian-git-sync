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
- Most of the motivation for functional languages comes from the research environment 
	- This is because functional programming languages can be evalutated on *correctness* a lot better (and hence reliability)
	- By using "true" functions its a lot easier to determine whether or not a function will always work as intended
- The correctness of functional languages also plays a role in *concurency*
	- If we know that no function can alter the value of the global state variables, it is possible to run several functions at once without any unintended consequences
---
## Higher Order functions 
- A higher order function, or a functional form, is a function that either takes as argument another function or returns a function 
	- Porgramming languages often use the term "first class functions" to imply that functions can be used like variables (passed and returned through other functions)
- C does NOT support first class functions
- Python DOES support first class functions
### Function composition 
- Composition is a functional form that takes two functions as paramters and then applies the first function to the application of the section function 
	- Note that this is not the same as taking an argument of a function as the function of another argument with an input like `foo( boo(2), 4)`
---
## Recursion, mutability, and purity
- Functional langauges rely heavily on recursion as opposed to looping structures in imperitive programming languages 
- Most functional languages provide a list of data structures like lists, dictionaries, etc
	- In general, these data structures are not mutable (so that the global state is not altered)
- Pure functional languages are just collections of functions and provide no imperatives or constructs
	- With Haskell as a notable exception, most functional programming langauges are hyprids (Clojure is an example of this class)
----
