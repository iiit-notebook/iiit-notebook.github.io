---
title: Linear Algebra Lecture 19
date: 2021-04-6
author: Pratyaksh Gautam
code: ma2.101
number: 19
---
## Diagonalizability of Matrices contd.

All square matrices are not necessarily diagonalizable.
Consider the example
$$
\begin{bmatrix}
	0 & 1 \\
	0 & 0 \\
\end{bmatrix}
$$
Its characteristic polynomial gives use $\lambda ^ 2 = 0$, and thus the only eigenvalue is 0.
Since the polynomial has two identical roots 0, we say that the **algebraic multiplicity** of the root 0, is 2.  
Naturally it follows that the sum of all the algebraic multiplicities of each root must add up to $n$,
since the characteristic polynomial must be of degree $n$, the dimension of the matrix.

The **geometric multiplicity** is the number of dimensions of $ker(M - \lambda I)$,
which is the same as the number of linearly independent eigenvectors with eigenvalue $\lambda$

## Norms and Inner Products

The **norm** or the "length" of a vector $v$ is defined as $\sqrt{\langle v, v \rangle}$,
the square root of the inner product of the vector with itself.
We have already seen the definitions and relevant properties of the inner product in previous lectures.
