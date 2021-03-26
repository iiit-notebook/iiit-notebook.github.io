---
title: Linear Algebra Lecture 12
date: 2021-03-18
author: Shashwat Singh
code: ma2.101
number: 12
---

# Fundamental theorem of invertible matrices

Let $A$ be an $n \times n$ matrix then the following statements are logical equivalents:
1. $A$ is invertible.
2. $A \cdot X = b$ has a unique solution for any $b \in \mathbb{R}^n$ 
3. $A \cdot X = 0$ has only the trivial solution.
4. The reduced row echelon form of $A$ is $I_n$ 
5. $A$ is a product of elementary matrices.

We will now prove that all those properties are logical equivalents.


$2 \Rightarrow 3$

Assume $A\cdot X = b$ for has a unique solution for any $b \in R^n$ . Now, let $b = 0$ . This will make the whole thing a homogeneous system of equations and homogeneous systems of equation at least have the trivial solution and since we know that the solution in this case is unique, we can say that the trivial solution is the only solution. 

$3 \Rightarrow 4$ 

We assume that $A \cdot X = 0$ has the unique trivial solution. 
Therefore, if we try to to Gauss-Jordan elimination, we should arrive at the reduced echelon form such that the augmented matrix will look like this: 
$[A | 0]$ 

$$= \left[\begin{array}{cccc|c} a_{11} & a_{12} & . & . & 0 \\  . & . & . & . & 0   \\ . & . & . & . & . \\ a_{n1} & a_{n2} & . & . & 0 \end{array}\right]$$ 

and since we know this is solvable and has trivial solution, we can say that we should be able to, after row operations, represent it as this 

$$\left[\begin{array}{cccc|c} 1 & 0 & . & . & 0 \\  . & . & . & . & 0   \\ . & . & . & . & . \\ 0 & 0 & . & 1 & 0 \end{array}\right]$$

because we know $x_1 = x_2 = x_3. .. x_n = 0$ 
as you can see the left side of the augmented matrix is $I_n$. Since we could get to to the augmented matrix using row operations alone, we can get from $A$ to $I_n$ using row operations alone, thus $I_n$ is the reduced echelon form of $A$.

$4 \Rightarrow 5$ 

Assuming that the reduced row echelon form of $A$ is $I_n$. Each row operation corresponds to an elementary matrix, therefore that means that $A$ can be left multiplied with a bunch of appropriate elementary matrices to get to $I_n$.

$E_1 \cdot E_2 … E_n \cdot A = I_n$ 

where $E_1$ to $E_n$ are all elementary matrices. We know that all Elementary matrices are invertible, thus we can say that 

$A = E_1^{-1} \cdot E_2^{-1} ...… \cdot E_n^{-1} I_n$

Thus $A$ is a product of elementary matrices. 

$5 \Rightarrow 1$

Given that $A$ is a product of elementary matrices, we can say that

$E_1 \cdot E_2 \cdot … E_n = A$ 

where $E_1$ to $E_n$ are all elementary matrices. We know that elementary matrices are invertible and therefore, we can keep left multiplying the inverse of these elementary matrices one - by one to get $I_n$ 

$I_n = E_1 ^{-1} \cdot  E_2^{-1} … E_n^{-1} \cdot A$
thus $(E_1^{-1} \cdot E_2^{-1} … E_n^{-1} = A^{-1}$ ) thus $A$ is invertible. 

__Theorem__: Let $A$ be a square matrix. If $B$ is a square matrix such that $AB = I$ pr $BA = I$ then $A$ is invertible and $B = A^{-1}$ 

(given without proof)

__Theorem__ Let $A$ be a square matrix. If a sequence of elementary row operations reduces $A$ to $I_n$ then the same sequence of elementary row operations transfers $I$ into $A^{-1}$ .

__proof:__ If $A$ is a row equivalent to $I$, then we can acheive the reduction by left multiplying a squence $E_1, E_2, .… E_k$ of elementary matrices. Therefore, 
$E_k… E_2 E_1 A = I_n$ and let $B = E_k \cdot … E_1$ 

$\Rightarrow B = E_k .… E_1$ and by previous theorem we have that $B = A^{-1}$. Now, by applying the same set of elementary row operations on $I$, we get the same thing as multiplying corresponding elementary matrices to $I$ i.e.

$E_k \cdot E_{k-1} \dot .… E_1 \cdot I= B \cdot I = B = A^{-1}$ 

Thus $I$ can be transformed to $A^{-1}$ by some sequence of elementary of row operations. 

This lays the basis for __The Gauss-Jordan method of finding Inverse__

# The Gauss-Jordan method of finding inverses

$[A \| I ] \rightarrow [I \| A^{-1}]$

The idea is simple, we subject $A$ to a bunch of elementary row operations to turn it to $I$, and $I$ is subjected to the same set of row operations and by the last theorem we know that it'll result in the inverse of $A$.


