# What is Finite Automata

> Automata theory is the study of abstract computing devices, or "machines." 

### The uses of Finite Automata in Computer Science
1. Software for desinging and checking the behaviour of digital circuits
2. The "lexical analyzer" of a typical compiler, that is, the compiler compnent that breaks the input text into logical units, such as identifiers, keywords, and punctuaution 
3. Software for scanning large bodies of texts, such as collections of Web pages, to find occurances of words, phrases or other patterns. 
4. Software for verifying systems of all types that have a finite number of distinct states, such as communciations protols or protocols for secure exchange of information. 

- Finite automata is characterised by the fact it only has a finite number of states. This means that, at a given point, there is only a relavnat portions of the systems hisotry that is available (This is a state). 
	- Since there is only a finite number of states, the system must be carefully designed to remember what is important and forget waht is not 
	- The advanatge of having only a finite number of states is that we can implement the system with a fixed set of resources. 
		- For exmaple, we could implement it in a hardware as a circuit, or as a simple for of program that can make decisions looking only at a limted amount of data or using the position in the code itself to make the decision. 

- Example 1.1 
	- The simplest nontrivial finite automata is the on/off switch 
 ![[Pasted image 20220730164647.png]]
	 - A finite state automata will usually show a start and finish state
		 - The start state can correspond to things like an empty string, if one were mapping a lexicographic recognition 
#### Structural Representations
- There are two important notations that are not automation-like, but play an important role in the study of automata and their applications 
	1. *Grammars* are useful models when designing software that processes data with recursive structure. 
		- The best known example is a "parser", the component of a compiler that deals with the recursively nested feaatures of the typical programming langauge, such as expressions -- arithmetic, conditional, and so on. 
	2. *Regular Expressions* also denote the structure of data, especially text strings. 
### Automata and Complexity 
- Automata are essential for the study of the limtis of computatuion. There are two important issues: 
	1. What can a computer do at all? This study is called "decidability", and the problems that can be solved by computers are called "decidable". This topic is addressed in #Chapter_9
	2. What can a computer do efficiently? This study is called "intracibility", and the problems that can be solved by a computer using no more time than some slowly growing function of the size of the input are called "tractable".  This topis is studied in #Chapter_10

### Set-Formers as a Way to Define Languages
- It is common to describe a language using a "set-former":
	- { w | something about w}
		- This expression is read "the set of words w such that (whatever is said about w to the right of the vertical bar)." Examples are
		1. {w | w consists of an equal number of 0's and 1's}
		2. {w | w is a binary integer that us prime}
		3. {w | w is a syntactically correct C program}
- It is also common to replace w by some expression with paramters and describe the strings in the langauge by stating conditions on the parameters. Here are some examples; 
	1. {$0 ^n 1^n  | n >= 1$}
		- Read "the set of 0 to the n 1 to the n such that n is greater than or equal to 1"
		- This langauge consists of the strings {01, 0011, 000111, ...}
	2. {$0^i1^j | 0 <=  i , <= j$} 
		- This language consists of strings with some 0's (possibly none) followed by at least as many 1's. 
### Chapter Summary: 
- Definitions: 
	1. *Finite Automata*: Finite automata involve states and transitions among states in response to inputs. They are useful for building several different kinds of software, including the lexical analysis component of a compiler and systems for verifying the correctness of circuits or protocols, for example. 
	2. *Regular Expressions*: There are a structural notation for describing the same patterns that can be represented by finite automata. They are used in many common types of software, including tools to search for patterns in text or in file names, for isntance. 
	3. *Context-Free Grammars*: These are an important notation for describing the structure of programming languages and related sets of strings; they are used to build the parser component of a compiler
	4. *Turing Machines*: These are automata that model the power of real computers. They allow is to study decidabilty, the question of what can or cannot be done by a computer. They also let us distinguish tractable problems - those that can be solved in polynomial time - those that can be solved in polynomial time -from the intractable problmes - those that cannot. 