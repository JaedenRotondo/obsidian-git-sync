## Basic Structure of a Python Program 
- For larger programs, Python code must be organized in a series of files 
	- We call these files modules, they are text files with the file extension .py
		- Note that the main module does not need to end in .py but usually does 
---
## The Use of Modules
- Python allows us to "import" modules into other modules
```python 
import banana # external module
banana.peel()
```
---
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
---
### Compilation of Python Files
- Unlike C, Python does not compile and link modules into a single executable file
	- Instead, source code is converted into intermediate bytcode format the first time it is seen
		- This produces a .pyc from the original .py file
- Note that .pyc files are not made for the main module, but only for the imported modules
- It is usually this .pyc byte code format that is executed when the program runs
![[Screen Shot 2022-11-02 at 12.45.36 PM.png]]
---
### Loading 
- There are other methods of loadung modules other than the basic import 
#### Import option 2: the From Statement 
- The `from` statement: 
	- the from and import are combined to allow for using the functions from an imported module without direct reference. In this way, we dont need to fully qualify the imported name 
```python 
from foo import bar
bar()
```
- Keep in mind that the entire foo module is compiled into .pyc even if you are only importing a single function `bar`
#### Import option 3: general import* 
```python 
from foo import *
bar()
boo()
baz()
```
- Although this is simple, it is not desirable because in large files it is hard to see where certain methods come from 
---
## Module Namespaces
- The Python interpreter makes a local _symbol table_ for each module 
	- This is to make sure there are no conflicts between variable names that are common across different files 
- By default, global variables are visible throughout the module but they are not visible to other files unless they are imported 
- dir() can be used to list the the names in a given module 
## The "main" module 
- When the python program runs, the interpreter sets a number of global variables
- Name of the module is held in `__name__`
- if the module is the starting module, its name is set to `__main__`
- 
## Packages 
- Python Packages are developed from Namespaces 
- Common modules can be organized into directory hierarchies 
- To indicate to the interpreter that the folders do in fact represent a package, each (sub)package must include a `__init__.py` file at the root level.