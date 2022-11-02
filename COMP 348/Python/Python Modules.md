## Basic Structure of a Python Program 
- For larger programs, Python code must be organized in a series of files 
	- We call these files modules, they are text files with the file extension .py
		- Note that the main module does not need to end in .py but usually does 
## The Use of Modules
- Python allows us to "import" modules into other modules
```python 
import banana # external module
banana.peel()
```
## Import Logic
- In C, the "#include" directive is merely a textual subsitution process, this is very different to python
	- The extended code is converted to bytecode at compile time 
- In Python, the import process is done during run time 
- When a program is run and an import statement is encountered, the following steps are taken 
1. Find the imported module in the file system 
2. Compile the contents of the imported .py file into a .pyc file
3. Execute the contents of the imported module before proceeding with the current program 
	- This usually just means loading and recording all the structures of the files

##### Nota Bene 
- All the compiling and loading occurs at runtime 
- A module will only be imported once
### Compilation of Python Files
- Unlike C, Python does not compile and link modules into a single executable file
	- Instead, source code is converted into intermediate bytcode format the first time it is seen
		- This produces a .pyc from the original .py file
- Note that .pyc files are not made for the main module, but only for the imported modules
- It is usually this .pyc byte code format that is executed when the program runs
![[Screen Shot 2022-11-02 at 12.45.36 PM.png]]
### Loading 
### Syntax 
## Namespaces
## The "main" module 
## Packages 