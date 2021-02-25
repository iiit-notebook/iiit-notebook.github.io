---
title: Linear Algebra Lecture 4
date: 2021-02-25
author: Pratyaksh Gautam
code: ma2.101
number: 4
---
## Linear Span of a Set
### Linear Combination of Vectors
IF $V(F)$ is a vector space, and $\alpha_i \in V$, $c_i \in F$, then a linear combination of vectors $\alpha$, is given by  
$$\alpha = \sum_{i = 1}^{k} c_i \alpha_i \in V$$

The operations used are only vector addition and scalar multiplication.

### Linear Span
The linear span of a non empty subset of $V(F)$ is the set of all linear combinations of any finite number of elements of S and is denoted by $L(S)$

In other words, all the vectors which we can represent or "reach" by linearly combining some vectors in $V(F)$, is known as the **linear span** of those vectors.

**Theorem:**
The linear span $L(S)$ of any subset S of a vector space $V(F)$ is a vector subspace of $V(F)$

**Proof:**
Let $\alpha, \beta \in L(S)$, then we have  
$$
\alpha = \sum_{i = 1}^{k_a} c_i \alpha_i \in V \\
\beta = \sum_{i = 1}^{k_b} c_i \beta_i \in V
$$  

Now for $a, b \in F$  
<div>
$$
\begin{align}
a \alpha + b \beta &= a \sum_{i = 1}^{k_a} (a_i \alpha_i) + b \sum_{i = 1}^{k_b} (b_i \beta_i) \\  
					&= \sum_{i = 1}^{k_a} a (a_i \alpha_i) + \sum_{i = 1}^{k_b} b (b_i \beta_i) \\  
					&= \sum_{i = 1}^{k_a} (a  a_i) \alpha_i + \sum_{i = 1}^{k_b} (b  b_i) \beta_i 
\end{align}
$$  
</div>

Since we know that $(a \times a_i) \in F$ and $(b \times b_i) \in F$,  
$\sum (a a_i) \alpha_i \in V$ and  $\sum (b b_i) \beta_i \in V$  

Thus, we can say $a \alpha, b \beta \in V$, and as a result, $a \alpha + b \beta \in V$.  

## Generator of a Vector Space
A set $S$ will be called as a **generator of a vector space** $V$, $\iff L(S) = V$

In other words, we can "reach" every vector in $V$ by linearly combining vectors in $S$.

## Linear Dependence and Independence
A finite set
<div>
$$\{ \alpha_1, \alpha_2, ... , \alpha_k\}$$
</div>
of $k$ vectors of $V(F)$ is said to be linearly dependent
if there exists a set of scalars 
<div>
$$\{ c_1, c_2, ... , c_k\}$$
</div>
such that 
$$ (c_1 \alpha_1 + c_2 \alpha_1 + ... + c_k \alpha_k) = \phi $$  
where for some $c_i$ in the set of scalars, $c_i \neq 0$,
then the set of vectors is said to be **linearly dependent**.

However if for the same situation, the only way for the linear combination to be $\phi$, is for *all* $c_i = 0$,
then the set of vectors is said to **linearly independent**.

**Theorem:**
If two vectors are linearly dependent, then one of the vectors is a scalar multiple of the other.

**Proof:**
Let the two vectors be $\alpha, \beta \in V(F)$,
and let there be two scalars $a, b \in F$ such that $a, b\neq 0$, then
<div>
$$
\begin{align}
a \alpha + b \beta &= \phi  \\
a \alpha + b \beta - b \beta &= \phi - b \beta &&\text{(existence of vector additive inverse)} \\
a \alpha + \phi &= \phi - b \beta \\
a^{-1} a \alpha &= a^{-1} (- b \beta) &&\text{(existence of scalar multiplicative inverse)} \\
(a^{-1} a) \alpha &= (a^{-1} (- b)) \beta \\
\alpha &= - (a^{-1} b) \beta \\
\end{align}
$$
</div>

Similarly, we can show that $\beta = - (b^{-1} a) \alpha$.  
Note that $a^{-1}$ only exists when $a \neq 0$.

**Theorem:**
The superset of a set of linearly dependent vectors is also a set of linearly dependent vectors

**Proof:**
Let 
<div>
$$W = \{ \alpha_1 + \alpha_2 + ... + \alpha_k\}$$
</div>
be a linearly dependent set of vectors in $V(F)$, such that
<div>
$$c_1 \alpha_1 + c_2 \alpha_2 + ... + c_k \alpha_k = \phi$$
</div>
where all $c_i \in F$.

Now consider another set of vectors,
<div>
$$X = W \cup \{ \beta_1, \beta_2, ... , \beta_j \}$$
</div>
so $W \subset X$.

Then we have
<div>
$$
\begin{align}
c_1 \alpha_1 + c_2 \alpha_2 + ... + c_k \alpha_k &= \phi \\
c_1 \alpha_1 + c_2 \alpha_2 + ... + c_k \alpha_k + \phi &= \phi \\
c_1 \alpha_1 + c_2 \alpha_2 + ... + c_k \alpha_k + 0 (\beta_1 + \beta_2 + ... + \beta_j) &= \phi \\
c_1 \alpha_1 + c_2 \alpha_2 + ... + c_k \alpha_k + 0 \beta_1 + 0 \beta_2 + ... + 0 \beta_j &= \phi \\
\end{align}
$$
</div>
and since $W$ itself is a linearly dependent set of vectors, one of $c_i$ must be non-zero.  
Thus, $X$ must also be a linearly dependent set of vectors.
