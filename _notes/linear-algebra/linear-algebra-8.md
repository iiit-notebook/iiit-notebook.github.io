---
title: Linear Algebra Lecture 8
date: 2021-03-06
author: Pratyaksh Gautam
code: ma2.101
number: 8
---
## Linear Mapping

**Theorem**: Let $$\{ x_1, x_2 ..., x_n\}$$ be a basis for a finite dimensional vector space $V(F)$ and $$\{ y_1, y_2 ..., y_n\}$$ be an arbitrary set of vectors in $W(F)$.
Then there exists a linear mapping from the $V$ to $W$.

**Proof**:  
Let $x \in V$, then $x = a_1 x_1 + a_2 x_2 + ... + a_n x_n$, where $a_i \in F$.

Then we define our function as


## Kernel and Image of Linear Map
Let $f:U \rightarrow W$ be a linear mapping from a vector space $U(F)$ to a vector space $W(F)$.
Then $ker(f)$ is the set of all $x \in U$ which map onto $\phi_W$, the vector additive identity element of W.
$$ ker(f) = \{x \in U \| f(x) = \phi_W \in W \} $$

Let $f: U \rightarrow W$ be a linear mapping. Then the set of all images of all elements $x \in U$ is called the range of the mapping, $R_f$

**Theorem**: Let $f: V \rightarrow W$ be a linear mapping from a vecotr space $V(F)$ to a vector space $W(F)$ over the same field F. Then
1. $ker(f)(F)$ is a subpace of $V(F)$.
2. $f(v)(F)$ is a subpace of $W(F)$.

**Proof**:
1. Let $x, y \in ker(f)$ then $x, y \in U$, since $f$ is a linear mapping, we have

2. 

$ker(f)$ is the **null space**, and $dim(ker(f))$ is called the **nullity** of the space.

$f(v)(F)$ is called the **range space** of f and the dimension of $f(V)$ is called the rank $r(f)$ of a linear transformation $f$.

(Sylvester law - rank nullity theorem)
