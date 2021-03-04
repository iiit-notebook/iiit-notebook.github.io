---
title: Linear Algebra lecture 7
date: 2021-03-04
author: Pratyaksh Gautam
code: ma2.101
number: 7
---

## Linear Transformation
A linear transformation is a function $f: U \rightarrow V$ for two vector spaces $U$ and $V$ defined over the field $F$,
such that:  
- $f(\alpha + \beta) = f(\alpha) + f(\beta)$  
- $f(c \alpha) = c f(\alpha)$  

where $\alpha, \beta \in U$, $c \in F$.

**Theorem**:
If $U$ and $V$ are linear spaces on the same field then $f: U \rightarrow V$ is a linear mapping if and only if  
$$f(a \alpha + b \beta) = a f(\alpha) + b f(\beta)$$

**Proof**:

**Theorem**: If there is a set of linearly dependent vectors in $U$, then the set of the images of the elements of that set in $V$ will also be linearly dependent.

**Proof**:  
Let the set in the domain be $$\{ \alpha_1, \alpha_2, \alpha_3, ... \alpha_n \}$$,
and we have corresponding scalars in $F$ $$\{ a_1, a_2, a_3, ..., a_n \}$$ such that  
$$a_1 \alpha_1 + a_2 \alpha_2 + a_3 \alpha_3 + ... + a_n \alpha_n = \phi$$  
where not all $a_i$ are zero.

Taking both sides of the equation as the input for the function $f$, we have  
<div>
$$
\begin{align}
				f(a_1 \alpha_1 + a_2 \alpha_2 + a_3 \alpha_3 + ... + a_n \alpha_n) &= f(\phi) \\
\Rightarrow		f(a_1 \alpha_1 ) + f(a_2 \alpha_2) + f(a_3 \alpha_3) + ... + f(a_n \alpha_n) &= f(\phi) \\
\Rightarrow		a_1 f(\alpha_1 ) + a_2 f(\alpha_2) + a_3 f(\alpha_3) + ... + a_n f(\alpha_n) &= \phi_{\in V} \\
\end{align}
$$
</div>

Since at least one of the $a_i$'s must be non-zero, and all $f(\alpha_i) \in V$,  
we can say that the set $$\{ f(\alpha_1), f(\alpha_2), f(\alpha_3), ... f(\alpha_n) \}$$,
is a linearly dependent set of vectors.
