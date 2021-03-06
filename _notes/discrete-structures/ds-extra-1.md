---
date: 2020-10-14
title: DS Extra 1
author: Pratyaksh Gautam
code: ma5.101
---

## Relations as matrices

Binary relations can also be visualized as matrices. In fact, it turns out this kind of visualization is very convenient and can be useful in proving some important results combinatorially.
Consider a binary relation $R: A \rightarrow B$, such that $\vert A \vert = m$ and $\vert B \vert = n$, we can represent this as an $m \times n$ matrix.

<div>
$$R = \begin{bmatrix}
		a_{11} & a_{12} & \dots \\
		\vdots & \ddots & \\
		a_{m1} &        & a_{mn}
	\end{bmatrix}$$
</div>

In this matrix, if $a_{ij} = 1$, then $(i,j) \in R$, and similarly if $a_{ij} = 0$, then $(i,j) \notin R$.

As an example, let us take a simple relation, from $A = \lbrace 1, 2, 3\rbrace $ to $B = \lbrace 4, 5\rbrace $,  
$R = \lbrace (1,4), (3, 5)\rbrace$  
The matrix representation for the same is then:

<div>
$$R =	\begin{bmatrix}
			1 & 0 \\
			0 & 0 \\
			0 & 1 \\
		\end{bmatrix}$$
</div>

Note that we need to already know which row and column refers to which element of each set.
This is often taken to be the elements of the set in some defined order.
Here too the ordered pairs corresponding to the elements of the matrix are not explicitly stated.

Now, let us consider a relation on a set of numbers 0 to n, $R: A \rightarrow A$, where $\vert A \vert = n$, so the corresponding matrix looks something like this:  

<div>
$$R = \begin{bmatrix}
		a_{11} & a_{12} & \dots \\
		\vdots & \ddots & \\
		a_{n1} &        & a_{nn}
	\end{bmatrix}$$
</div>

### All relations
Since we have a total of $n^2$ elements in the matrix, all of which could be either 0 or 1 to signify the presence of an ordered pair in the 
relation, we get a **total of $2^{n^2}$ relations possible** in $A \times A$.

### Reflexive relations
The requirement of a reflexive relation is that every element in the domain should be mapped to itself. On the matrix this corresponds to 
all the diagonal elements being 1. 

<div>
$$R = \begin{bmatrix}
		1	   & a_{12} & \dots \\
		\vdots & 1      & \\
		a_{n1} &        & 1
	\end{bmatrix}$$
</div>

This means that there are n fixed elements in the matrix, but we are free to change about the rest of the elements. This means **we have 
$2^{n^2 - n} = 2^{n(n-1)}$ total reflexive relations possible.**

### Symmetric relations
For symmetric relations, if $a_{ij} = 1$, then we must also have $a_{ji} = 1$. So we can only permute the elements of one triangle (say upper) and the diagonal.

<div>
$$R =	\begin{bmatrix}
		a_{11}	& a_{12}& \dots	& a_{1n}	\\	
				& a_{22}& \dots	& a_{2n}	\\
				&		& \ddots& \vdots	\\
				&		&		& a_{nn}	\\	
		\end{bmatrix}$$
</div>

This gives us a total of $\sum_{i = 1}^{n} i = \frac{n(n+1)}{2}$ elements, which can be either 0 or 1. So **we have a $2^{\frac{n(n+1)}{2}}$ total symmetric relations possible.**

### Anti-symmetric relations
For anti-symmetric relations, we know that for the diagonal elements, they can either be 0 or 1, but the interesting case is that of the non-diagonal elements.
For two corresponding elements $a_{ij}$ and $a_{ji}$, we know that either:  
+ $a_{ij} = 0$ and $a_{ji} = 1$
+ $a_{ij} = 1$ and $a_{ji} = 0$
+ both are zero

This means that we have a total of n elements with 2 possible states, and $\frac{n(n-1)}{2}$ pairs of the remaining elements with 3 possible states.
This gives us **$2^{n} \cdot 3^{\frac{n(n-1)}{2}}$ total possible anti-symmetric relations.**

### Reflexive and symmetric relations
For relations that are both reflexive and symmetric, we have the same as symmetric relations, but now the diagonal is frozen; it can only have 1's.
As a result, the number reduces to $2^{\frac{n(n+1)}{2} - n} = 2^{\frac{n(n-1)}{2}}$  
i.e **there are $2^{n \choose 2}$ total relations that are both symmetric and reflexive.**
