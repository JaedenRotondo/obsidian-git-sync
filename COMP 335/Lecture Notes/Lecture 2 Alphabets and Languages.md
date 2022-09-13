# Alphabets and Languages 
##### **_Alphabet:_ Z- a finite set of characters/symbols**
- Example: Z = {a,b,c,...,z} - English Alphabet
##### **_String or Sentence:_ w - A finite sequence of characters from Z** 
- Example: w= cat, w= iloveformallanuagues
##### **_Language_: L - a set *(either finite or infinite)* of strings over Z** 
- Example: set of english words 

> Another example:
> Z =  {0,1,2,...,9, A,B,...,Z, a, b,..., z,\_}
> L - {All valid C++ keywords}

## Operations
#### Concatenation 
Let w = a$_1$ , a$_2$ ,..., a$_n$ 
Let v = b$_1$ , b$_2$, ... b$_n$
w concatenated with v is  wv = a$_1$ , a$_2$ ,..., a$_n$ b$_1$ , b$_2$, ... b$_m$
v concatenated with w is  wv = b$_1$ , b$_2$, ... b$_m$, $a_1$ , a$_2$ ,..., a$_n$ 

#### Reverse 
Let w = a$_1$ , a$_2$ ,..., a$_n$ 
Let $w^R$ = a$_n$ , a$_n-1$ ,..., a$_1$

#### Length of a String 
Given w = a$_1$ , a$_2$ ,..., a$_n$ 
Length |w| = n 

> Note that the length of a concantenated string is the sum of the lengths of each element

#### The empty String ($\lambda$)
- An empty string is denoted by $\lambda$
	- |$\lambda$| = 0 
	- $\lambda v$ = $v \lambda$ = $v$ for all strings in $v$
	- $\lambda$$\lambda$ = $\lambda$
	- N.B. $\lambda abba$ = $abba \lambda$ = $abba$

### Substrings 
_Definition_: A substring of a string w is a subsewuence of consecutive characters in w 
- The difference between a subset and a subsequence is that a subsequence will remain its order and repition 
- $\lambda$ is always a substring of any string, even of itself

#### Prefix and Suffix 
Let $w = uv$
Let $w = abbabbaa$
if $u = abbab$ and $v - baa$
Then, $u$ would be a **a possible** prefix of $w$ and $v$ would be a suffix of $w$ 
- N.B. the smallest prefix and suffix would be $\lambda$
- Prefix length go from 0 to n *the length of the string*

### Another Operation 
$w^n = ww...w$ (n times)
$w^0  = \lambda$ (by definition)
> $w^0 = \lambda$ 
> Base case $w^n+1 = w^nw$
>Proof:  $w = \lambda w= w^0w = w^1 = w$

### Star Operations and Plus Operations 
- N.B. that a lot of people lose marks because of this 
- The star operator and the plus operator are overloaded
- In reality they are 2 kinds of each 
	- We distringuish them as follows: 
	- **Star operator type 1 applies to Alphabets and Languages 
	- **Star operator type to applies** 

#### Star operation as applied to alphabets 
- $Z^*$ is the set of all strings over alphabet Z 
- $Z^+$ - the set of all strings over alphabet Z except for $\lambda$
- Example 
- Z = {a,b}
	- $Z^*$ = { $\lambda$, a, b, aa, ab, ba, bb, aab ...}
	- $Z^+$ =  { a, b, aa, ab, ba, bb, aab ...} (does not include $\lambda$)
- N.B. $Z^*$  = $Z^+$ - $\lambda$
	- $Z^+$ is a language, it is actually the largest language of an alphabet 

### Languages 
- Given alphabet Z, a langauge is a subset of $Z^*$ 
- Examples of languages over $Z^*$ = {a,b} 
	- {} or $\emptyset$ (the empty set)
	- {$\lambda$}
	- $Z^*$ 
	- {abba, a, b}
	- {$a^n b^n : n\ge 0$}
**- Question, what is the lengh of the above languages?** 

### The meaning of |..|
- The following notation is also overloaded
	- It is used to denote (1) string length, and (2) set size

### Operations on Langauges 
- Since languages are sets, standard set operations apply 
- The union of languages is the same as the union of a set
- The intersection of langauge is the same as an intersection of sets
- The compliment of a language is the same as the compliment of a set 
	- The compliemnt is laways in respect to the universe  $Z^*$ 

#### Reverse operations on Languages 
- $L^R = {w^R : w \in L}$ 
- {ab, aa}^R = {aa, ab}}
### Concatenation in Lanagues 
- $L_R \cdot L_R= {xy : x \in L_1, y \in L_2}$ 
![[Screen Shot 2022-09-08 at 2.28.36 PM.png]]

- Note: 
	- $L_1 <= Z^*$ 
	- $L_2 <= Z^*$ 
	- $L_1 L_2 = \{w_1 w_2 : w_1 \in L_1 w_2 \in L_2\}$
- empty set to the power of zero (research)
	- Is equal to $\lambda$
- lambda concatenated to any language does not change the language 
- 

---

### Star Closure (Kleene Star)
- For language L we define 
	- $L^* = L^0 \bigcup L^1 \bigcup L^2 \bigcup L^3 \bigcup ...$
	- $L^* = \{w_1 w_2 ... w_k : \forall k >= 0\}$

##### Example: 
$L = \{a,bb\}$
$L^*=\{ \lambda ,$
= a, bb
aa, abb, bba, bbbb
aaa, aabb, abba, abbbb, ....}

----
### Positive Closure 
- $L^+ = L^0 \bigcup L^1 \bigcup L^2 \bigcup L^3 \bigcup ...$

- Is it possible for $\lambda$ belong to $L^+$
	- This is possible if and only if $\lambda$  was already in the language 
	- Example: L = {$\lambda$} is an example where $\lambda$  would be in $L^+$
