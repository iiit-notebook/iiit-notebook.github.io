---
title: Linear Algebra lecture 7
date: 2021-03-04
author: Pratyaksh Gautam, Shashwat Singh
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
$$f(a \cdot \bar\alpha + b \cdot \bar\beta) = a f(\bar\alpha) + b f(\bar\beta)$$

**Proof**:
This is an if and only statement, therefore the proof has two parts, for vector spaces $U$ and $V$ and $\bar\alpha, \bar\beta \in U$ and $a, b \in F$:
1. $f:U \rightarrow V$ is a linear mapping $\Rightarrow$ $f(a\cdot \bar\alpha + b \bar\beta) = a \cdot f(\bar\alpha) + b \cdot f(\bar\beta)$
2. $f(a\cdot \bar\alpha + b \bar\beta) = a \cdot f(\bar\alpha) + b \cdot f(\bar\beta)$ $\Rightarrow$ $f: U \rightarrow B$ is a linear mapping.

__The first part:__  
Given that $f: U \rightarrow V$ is a linear mapping, we get two stipulations:
1. $f(\bar\alpha + \bar\beta) = f(\bar\alpha) + f(\bar\beta)$ for arbitrary $\bar\alpha, \bar\beta \in U$ 
2. $f(c \cdot \bar\alpha) = c \cdot f(\bar\alpha)$ for $c \in F$ and $\bar\alpha \in U$   


Now, let us consider $f(a \cdot \bar\alpha + b \cdot \bar\beta)$, by closure of scalar multiplication we know that $a \cdot \bar\alpha, b \cdot\bar\beta \in U$ thus by the first stipulation we can say
$$
f(a \cdot \bar\alpha + b \cdot \bar\beta) = f(a \cdot \bar\alpha) + f(b \cdot \bar\beta) \\
$$

and using the second stipulation we get (for each term on the right):

$$
f(a \cdot \bar\alpha) + f(b \cdot \bar\beta)  = a \cdot f(\bar\alpha) + b \cdot f(\bar \beta)
$$

Hence
$$
f(a \cdot \bar\alpha + b \cdot \bar\beta) = a \cdot f(\bar\alpha) + b \cdot f(\bar\beta)
$$
  

__The second part:__  
Given that  

$$
f(a \cdot \bar\alpha + b \cdot \bar\beta) = a \cdot f(\bar\alpha) + b \cdot f(\bar\beta)
$$ 

for arbitrary vectors in $U$ and arbitrary scalars in $F$   
since $1 \in F$ we let $a = b = 1$, after making that substitution we get
$$
f(\bar\alpha + \bar\beta) = f(\bar\alpha) + f(\bar \beta)
$$

for arbitrary vectors in $U$, this is the _first stipulation required for a linear transformation_.

since $0 \in F$, we let $b = 0$, after making this substitution in the given statement, we have

$$
f(a \cdot \bar\alpha) = a \cdot f(\bar\alpha)
$$

for abitrary vectors in $U$ and arbitrary scalars in $F$. We have obtained the _second stipulation of a linear transformation_

Having obtained the two required stipulations for linear transformation, we claim that $f$ is a linear transformation. Hence proved.




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
