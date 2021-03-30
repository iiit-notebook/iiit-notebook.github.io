---
title: Linear Algebra Lecture 14
date: 2021-03-23
author: Pratyaksh Gautam
code: ma2.101
number: 14
---

**Theorem**: Let $B$ be an $n \times n$ matrix and let $E$ be an $n \times n$ elementary matrix.  
Then
$$det(EB) = det(E)det(B)$$

**Proof**: trivial

**Theorem**: A square matrix is invertible iff $det(A) \neq 0$

**Proof**:  
Let A be an $n \times n$ matrix and $R$ be the reduced row echelon form of $A$.
Then we know that we can represent it as 
$$E_r ... E_2 E_1 A = R$$
where $E_i$ are the elementary matrices corresponding to the elemantry transformations needed to convert $A$ to $R$

Taking the determinant on both sides, and by repeated application of the previous theorem, we have
$$det(E_r) ... det(E_2) det(E_1) det(A) = det(R)$$
Thus we get
