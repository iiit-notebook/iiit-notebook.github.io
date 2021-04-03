---
title: Linear Algebra Lecture 18
date: 2021-04-03
author: Pratyaksh Gautam
code: ma2.101
number: 18
---

## More on eigenvalues and eigenvectors
Eigenvectors corresponding to distinct eigenvalues are linearly independent.

Suppose $M$ has $n$ linearly independent eigenvectors,$\{ v_1, v_2, ... v_n\}$,
with corresponding eigenvalues $\{ \lambda_1, \lambda_2, ... \lambda_n\}$

Suppose
$$w = \alpha_1 v_1 + \alpha_2 v_2 + ... + \alpha_n v_n$$
$$\implies Mw = \alpha_1 \lambda_1 v_1 + \alpha_2 \lambda_2 v_2 + ... + \alpha_n \lambda_n v_n$$

In this representation $(\alpha_1, ... \alpha_n)$ are co-ordinates of $W$ in $\{v_1, ... v_n\}$.
If we change basis from $\{ e_1, e_2, ... e_n\}$ to $\{ v_1, v_2, ... v_n \}$, then the linear transformation corresponding to $M$ *acts like* a diagonal matrix.

So in order to change our basis, we must premultiply by a change of basis matrix, say $P$,
where $P$ converts from the new basis to our old standard basis.
Thus, if in the old basis, we had $w \mapsto Mw$,
then in our new basis, we have $\bar w = P^{-1}w$, and the new mapping $\bar w \mapsto P^{-1}MP \bar w$

So if we wished to think of this linear transform in our new basis only, as some transform $\bar M$, such that $\bar w \mapsto \bar M \bar w$, then clearly we have
$\bar M = P^{-1}MP$.

Since application happens from right to left, we can think of what happens to $\bar w$ sequentially, for a more intuitive understanding.  
1. $\bar w$ gets converted back to $w$, since $w = P \bar w$. Now we're in the old standard basis.  
2. $M$ gets applied to $w$, the original transform that we knew, and this operation happens in the old basis.  
3. $P^{-1}$ finally gets applied to this result as well, giving us the result in our new "eigenbasis".  

Note that the eigenvalues of $\bar M$ will be given directly by the diagonal elements of the matrix, which are simply all the $\lambda_i$'s, i.e the same as the eigenvalues of of $\bar M$

## Equivalence relation
Consider a relation for $n \times n$ matrix defined as such

$M \equiv \bar M$ iff there exists invertible $P$ such that $P^{-1}MP = \bar M$.

$M$ is said to be diagonalizable iff $M \equiv$ to a diagonal matrix.

Diagonalizable matrices have some useful properties which stem from the diagonal matrices they are equivalent to.

$$M^tv$$
$$= (PDP^{-1})^tv$$
$$= (PD^tP^{-1})v$$

And computing $D^t$ itself is trivial given $D$ is a diagonal matrix; we simply take the elements along the diagonal to the power $t$ for each one.
