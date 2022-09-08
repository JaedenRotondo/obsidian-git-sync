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

## Operaitions
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
- 

