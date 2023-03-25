### 1. [10 Points] Let R(A,B,C,D) be a relation schema with the following set of FD’s: _F = {AB → C, C → D, D → A}._
_(a). Find all the keys of R._
First, find the closure of each attribute: 
- A -> A
- B -> B
- C -> CDA
- D -> A
- AB -> ABCD
- AC -> ACD
- AD -> AD
- BC -> BCD
- BD -> BDA
- ABC -> ABCD
- ABD -> ABCD
- ACD -> ACD
- CBD -> ABCD 
Therefore, the keys of R is AB since its minimal
_(b). Find all the superkeys of R that are not keys._
{ABC, ABD, CBD}
### 2. [Points 10] In each of the following rules about FD’s, prove if the given rule is valid.

_If it is not valid, then give a counter-example_

_(a). AB → DE and A → C, then B → C._
No, lets say we have the following entities: 
| A 	| B 	| C 	| D 	| E 	|
|---	|---	|---	|---	|---	|
| 1 	| 1 	| 0 	| 1 	| 1 	|
| 1 	| 0 	| 1 	| 0 	| 0 	|
| 0 	| 0 	| 1 	| 0 	| 0 	|
_(b). If AB → C, then A → C or B → C._
No, lets say we have the following entities: 
| A 	| B 	| C 	|
|---	|---	|---	|
| 1 	| 1 	| 1 	|
| 0 	| 1 	| 0 	|
| 1 	| 0 	| 0 	|
### 3. [10 Points] Suppose R(A,B,C,D,E) is a relation with some set F of FD’s that holds on R. For each of the following cases of F, project the FD’s in F onto relation S(A,B,C). Note that the result is the set of FD’s that hold on S if F holds on R.
X = -   {}, {A}, {B}, {C}, {A,B}, {A,C}, {B,C}, {A,B,C}
_(a). AB → DE, C → E, D → C, and E → A._
Find closure of X under F(a)
- {} ->{}  
- {A} -> {A} 
- {B} ->{B}
- {C} -> {CE}
- {A,B} -> {ABCDE}
- {A,C} -> {ACE}
- {B,C} -> {BCE}
- {A,B,C} -> {ABCDE}
F1 = {AB -> C}
_(b). A → D, BD → E, AC → E, and DE → B._
- {} ->{}  
- {A} -> {AD} 
- {B} ->{B}
- {C} -> {C}
- {A,B} -> {ABDE}
- {A,C} -> {ABCDE}
- {B,C} -> {BC}
- {A,B,C} -> {ABCDE}
F1 = {AC -> B}
### 4. [10 Points] Consider the following relations with the FD’s that hold on them. In each case, (i) determine every FD that violates the BCNF requirements, and (ii) decompose the given relation into BCNF relations.

_(a). R(A,B,C,D) with the FD’s: A → B, B → C, C → D, and D → A._
Already in BCNF 
_(b). R(A,B,C,D,E) with the FD’s: AB → C, C → D, D → B, and D → E._
To answer the question, we compute the closures of the LHS X of every FD to see if X+=R or not.
AB -> ABCDE
C-> CDBE
D-> DBE
C and D are not superkeys 

1. Decompose R into two relations: AB and R –B, and project F onto the new relations
R1{DBE} 
Projection: 
{}-> {}
{D} -> {DBE}
{B} ->  {B}
{E} -> {E}
{D, B} -> {DBE}
{D, E} -> {DBE}
{B, E} -> {BE}
{D, B, E} -> {DBE}
F1 = {D -> BE}

R2{ACD}
- {} ->{}  
- {A} -> {A} 
- {D} ->{asd}
- {C} -> {BCDE}
- {A,D} -> {}
- {A,C} -> {ABCDE}
- {D,C} -> {}
- {A,D,C} -> {ABCDE}
F2 = {AB -> C, AC -> B, C->D}
2. Repeatedly do the following 

If either R–B or AB is not in BCNF w.r.t their corresponding FDs, decompose it further.
### 5. [20 Points] For a relation R(A,B,C,D,E), we propose a decomposition R into the three relation schemas: R1(A,B,C), R2(B,C,D), and R3(A,C,E). For each of the following sets of FD’s that hold on R, use the technique discussed in the class to (i) prove/disprove the proposed decomposition is lossless, and (ii) determine whether or not, the proposed decomposition is dependency-preserving.

_(a). A → D, D → E, and B → D._

_(b). CD → E, E → D, and A → D._

6. [15 Points] Consider the relation stocks(B,O, I, S, Q,D) with the FD’s: S → D, I → B, IS → Q, and B → O, where you can think of B as broker, O as office (of the broker), I as investor, S as stock, Q as quantity (of the stocks owned by the investor), and D as dividend (of the stock)._

_(a). Find all the keys of Stocks._

_(b). Find a minimal basis for the FD’s, if not already minimal._

_(c). Use the synthesis algorithm to find a lossless-join and dependency-preserving_
_decomposition of Stocks into 3NF relations. Are any of the resulting relations_
_not in BCNF?_
