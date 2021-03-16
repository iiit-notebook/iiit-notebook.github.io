---
title: Linear Algebra Lecture 11
date: 2021-03-16
author: Pratyaksh Gautam
code: ma2.101
number: 11
---
## Gauss-Jordan Elimination
In **Gauss-Jordan** elimination, we convert the augmented matrix to **reduced row echelon form (RREF)**.
RREF is very similar to row echelon form, where the leading entry of each row is 1,
and the column containing a leading 1 has all other entries as 0.

## Elementary matrices
A matrix that can be obtained from the identity matrix, by applying elementary row and column transformations,
is known as an **elementary matrix**.

Interestingly, premultiplying a matrix by an elementary matrix which was obtained by applying a certain set of elementary transformations on the identity matrix, is the same as applying those transformations

**Fundamental Theorems of Invertible Matrices:**
a) $A$ is invertible.  
b) $Ax = B$ has a unique solution for every $b \in \mathbb{R}^n$.  
c) $Ax = 0$ has only the trivial solution.  
d) The RREF of $A$ is $I_n$.  
e) $A$ is a product of elementary matrices.  

The above statements are all equivalent forms of each other.

**Definition:** (Invertible Matrices)  
If $A$ is an $n \times n$ matrix, the inverse of $A$ is a matrix $A^{-1}$ with the property
$$AA^{-1} = A^{-1}A = I_n$$

If $Ax = B$ has a unique solution, $x = A^{-1}B$.  
Suppose there exists another solution $y$, then
$$Ay = B$$
$$\implies A^{-1}Ay = A^{-1}B$$
$$\implies Iy = A^{-1}B$$
$$\implies y = A^{-1}B$$

Thus we have $y = x = A^{-1}B$, meaning we only have a unique solution.
