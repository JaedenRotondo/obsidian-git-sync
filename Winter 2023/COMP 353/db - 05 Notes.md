## Covers/ Bases
- Note that F $\equiv$ G iff $F^{+} \equiv G^+$
	- This means they have the same FDs 
- There are two ways to make a minimal bases
	- We can knock out FDs that are not required
	- We can minimize the left side of each FD 
		- instead of AB $\implies$ C, maybe we can say A $\implies$ C
## Canonical Covers
 - Let **F** be a set of FD’s.  A canonical cover of **F** is a set **G** of FD’s that satisfies the following conditions:
	**1.** **G** is equivalent to **F**, that is, **G** ≡ **F** 
	**2.** Every FD in **G** is has a single attribute on the right hand side.
	**3.** **G** is minimal, that is, if we obtain a set **H** of FD’s from **G** by deleting some FD’s in **G** or by reducing the left hand side of some FD’s, then **H** won’t be equivalent to **F  (*that is, H** ≢ **F)**

- A canonical cover **G** is *minimal* in two respects
1. Every FD in G is required in order to make G equivalent to F 
2. Every FD in G is as small as possible 