---
title: Linear Algebra Lecture 13
date: 2021-03-20
author: Pratyaksh Gautam
code: ma2.101
number: 13
---
## Determinant
The determinant od the $2 \times 2$ matrix 
$$ A = 
\begin{bmatrix}
	a_{11} & a_{12} \\
	a_{21} & a_{22} \\
\end{bmatrix}
$$
is $det(A) = a_{11} a_{22} - a_{12} a_{21}$

*(Note: You already knew this, and you already know how to calculate determinants for larger matrices too, so I'm skipping this)*

### Properties of Determinants
a) If $A$ has a zero row, then $det(A) = 0$  
b) If $B$ is obtained by interchanging two rows (or columns) of A, then $det(B) = -det(A)$  
c) If $A$ has two identical rows (or columns), then $det(A) = 0$  
d) If $B$ is obtained by multiplying a row (or column) of $A$ by $k$ then $det(B) = kdet(A)$  
e) If $C$ is identical to two matrices $A$ and $B$ in all but one row (or column), and that column is the sum of the corresponding columns in $A$ and $B$, then $det(C) = det(A) + det(B)$  
f) If $B$ is obtained by adding a multiple of one row (or column) of A to another row (or column), then $det(B) = det(A)$  

## Elementary matrices
AN **elementary** matrix is one that differs from the identity matrix by a single elementary row transformation, (row exchange, multiplication of row by a constant, or addition of a multiple of another row to the current row).

As a result, the determinant of the corresponding elementary matrix must either be $-1, k$, or $1$ respectively for these three types of elementary matrices.

Premultiplying any other matrix by an elementary matrix corresponds to applying the corresponding row transformation on a matrix itself.

**Theorem**: Let $B$ be an $n \times n$ matrix and let $E$ be an $n \times n$ elementary matrix, then $det(EB) = det(E)\ det(B)$

**Proof**:  
Since we know that premultiplying by an elementary matrix corresponds to applying the corresponding row transformation on a matrix itself, and that the elementary matrix can have determinant equal to either $-1, k$ or $1$, we can prove this be case analysis.

Case 1: $E$ is an exchange matrix with $det(E) = -1$  
In this case, $EB$ would correspond to the matrix $B$ with a single row exchange performed, and thus $det(EB) = -det(B)$.
Since $det(E) = -1$, we can see that $det(E)\ det(B) = - det(B)$.

Case 2: $E$ be a row multiplication matrix with $det(E) = k$  
In this case, $EB$ correspons to the matrix $B$ with a single row multiplied by the constant $k$,
and thus $det(B) = k\ det(B)$
Since $det(E) = k$, then here too we can see that $det(E)\ det(B) = k\ det(B)$

Case 3: $E$ be a row addition matrix with $det(E) = 1$  
In this case, $EB$ would correspond to the matrix $B$ with a single row addition, and thus $det(EB) = det(B)$.
Since $det(B) = 1$, then here again we can see that $det(E)\ det(B) = det(B)$

**Theorem**: A square matrix is invertible iff $det(A) \neq 0$  

**Proof**:  
Let $A$ be a $n \times n$ matrix and $R$ be the RREF of $A$. Then by the theorem of invertible matrices, $R = I_n$.
We also know that we can perform the conversion to RREF through a set of elementary row operations,
which in turn can be represented as a set of premultiplications with the corresponding elementary matrices, i.e.

<div>
$$E_r E_{r-1} ... E_2 E_1 A = R$$  
$$\implies det(E_r E_{r-1} ... E_2 E_1 A) = det(R)$$  
$$\implies det(E_r)\ det(E_{r-1})\ ...\ det(E_2)\ det(E_1)\ det(A) = det(R)$$
</div>
And we know all of these $det(E_i)$s to be non-zero, thus

$$c\ det(A) = det(R)$$

where $c \neq 0$, and thus,

$$det(A) \neq 0 \iff det(R) \neq 0$$

Conversely, suppose that we know that $det(A) \neq 0$, then this implies that it's RREF $R$ must be $I_n$.
Again we can say

<div>
$$E_r E_{r-1} ... E_2 E_1 A = R = I_n$$  
$$\implies (E_r E_{r-1} ... E_2 E_1) A = A^{-1} A = I_n$$  
</div>

Thus $A^{-1} = (E_r E_{r-1} ... E_2 E_1)$, the inverse exists and is given.
