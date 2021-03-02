---
title: Linear Algebra Lecture 6
date: 2021-03-02
author: Pratyaksh Gautam
code: ma2.101
number: 6
---
## Direct sum
A vector space $V$ will be called a **direct sum** if it is the linear sum of two vector subspaces of $V$,
$W_1$ and $W_2$ and for all $\alpha \in W_1$ and $\beta \in W_2$,
there are no other vectors $\alpha\prime \in W_1$ and $\beta\prime \in W_2$, such that
$$\alpha + \beta = \alpha\prime + \beta\prime$$

In other words, the vector space $V$ is a direct sum of the vector subspaces $W_1$ and $W_2$,
if and only if each element in $V$ can be represented as the unique sum of a pair of elements,
one vector from $W_1$ and the other vector from $W_2$ respectively.

**Theorem**: If for a vector space $V$, $W_1 + W_2 = V$ and $$W_1 \cap W_2 = \{\phi\}$$, then $V$ is a direct sum of $W_1$ and $W_2$, and vice versa.

**Proof**:  
**Backward Implication**:
Let $V$ be the direct sum of $W_1$ and $W_2$, then it naturally follows that $V = W_1 + W_2$.

For the second condition, since the intersection of two vector subspaces also yields a vector subspace,  
$W_1 \cap W_2$ is guaranteed to contain the vector additive identity, $\phi$.
Let us now assume that some other element $\alpha$ belongs to both $\alpha$ and $\beta$.  
Then we have:  
$\alpha + \phi$ where $\alpha \in W_1$ and $\phi \in W_2$  
and $\phi + \alpha$ where $\phi \in W_1$ and $\alpha \in W_2$  
Clearly we have represented the same vector, $\alpha$ in the form of two different sums taking one vector from each subspace, so $V$ cannot be the direct sum of $W_1$ and $W_2$.  
This poses a contradiction, and thus no element other than $\phi$ can belong to both $W_1$ and $W_2$.  
Thus, $$W_1 \cap W_2 = \{\phi\}$$.

**Forward Implication**:
Given that $W_1 + W_2 = V$ and $$W_1 \cap W_2 = \{\phi\}$$,
let us assume that there exist pairs $\alpha, \alpha\prime \in W_1$ and $\beta, \beta\prime \in W_2$, such that
$\alpha \neq \alpha\prime$, $\beta \neq \beta\prime$, and
<div>
$$
\begin{align}
	\alpha + \beta &= \alpha\prime + \beta\prime \\
	\alpha - \alpha\prime &= \beta\prime - \beta \\
\end{align}
$$
</div>

By the property of closure, we can say that $\alpha - \alpha\prime \in W_1$, $\beta\prime - \beta \in W_2$.
Since they are equal, they represent an element present in **both** $W_1$ and $W_2$,
but we know there is only one element that the two have in common, i.e. $\phi$.  
Thus we can say that $\alpha - \alpha\prime = \phi = \beta\prime - \beta$  
which in turn tells us that $\alpha = \alpha\prime, \beta = \beta\prime$.

This poses a contradiction, and thus we can conclude that there must be no such pairs of elements.
Finally, this means that $V$ must be a direct sum of the vector subspaces $W_1$ and $W_2$.

**Theorem**: **(Steinitz Replacement Theorem)**  
If $$\{ \bar\alpha_1, \bar\alpha_2, ..., \bar\alpha_n \}$$ is a basis of $V(F)$ and $\bar\beta$ is a non zero vector belonging to V, then $\bar\beta = \sum_{i = 1}^{n} c_i \bar\alpha_i$,
where $c_i \in F$ and all $c_i$'s are non-zero.
If $c_j \neq 0$, then $$\{ \bar\alpha_1, \bar\alpha_2,..., \bar\alpha_{j-1}, \bar\beta, \bar\alpha\_{j+1}, ..., \bar\alpha_n \}$$

**Proof**:
Let $c_j$ be the non zero, then we have:  
<div>
$$
\begin{align}
	\bar\beta &= c_1 \bar\alpha_1 + c_2 \bar\alpha_2 + ... + c_{j-1} \bar\alpha_{j-1} + c_j \bar\alpha_j + c_{j+1} \bar\alpha_{j+1} + ... +  c_n \bar\alpha_n \\
	c_j \bar\alpha_j &= \bar\beta - (c_1 \bar\alpha_1 + c_2 \bar\alpha_2 + ... + c_{j-1} \bar\alpha_{j-1} + c_{j+1} \bar\alpha_{j+1} + ... +  c_n \bar\alpha_n) \\
	\bar\alpha_j &= c_j^{-1} \bar\beta - c_j^{-1} (c_1 \bar\alpha_1 + c_2 \bar\alpha_2 + ... + c_{j-1} \bar\alpha_{j-1} + c_{j+1} \bar\alpha_{j+1} + ... +  c_n \bar\alpha_n) \\

\end{align}
$$
</div>

**Theorem**:
