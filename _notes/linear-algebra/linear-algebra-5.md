---
title: Linear Algebra Lecture 5
date: 2021-02-27
author: Shashwat Singh
code: ma2.101
number: 5
---
# Lecture

**Theorem**:
The set of non-zero vectors $\{\bar\alpha_1\, \bar\alpha_2\ … \bar\alpha_k\}$ is linearly dependent,
if and only if there exists an $\bar\alpha_r, 2 \leq r \leq k$, such that it is the linear combination of preceeding vectors.

**Proof**:  
*Note: this proof is taken primarily from the book "Finite-Dimensional Vector Space by P.R. Halmos"
(Note that prof uses the terms sufficient and necessity condition terminology,
it's the same proof, just a different way of looking at it. I am more comfortable with this.)*

**RTP**:  
- $\{\bar\alpha_1\, \bar\alpha_2\ … \bar\alpha_k\}$ is linearly dependent
then there is an $\bar\alpha_r$ which can be represented as a linear combination of the vectors before it.  
- If there exists an $\bar\alpha_r$ such that it is a linear combination of all the vectors before it,
then the set $\{\bar\alpha_1\, \bar\alpha_2\ .… \bar\alpha_k\}$ is linearly dependent.

Let $W = \{\bar\alpha_1\, \bar\alpha_2\ .… \bar\alpha_r....  \bar\alpha_k\}$  

**The first part**:  
We assume that $r$ is the first integer for which the set $\{\bar\alpha_1, \bar\alpha_2 … \bar\alpha_r\}$ is linearly dependent (notice that is a _subset_ of $W$ ).
Note that this is not an unfair assumption, because we can always say that $r =k$ and the set will become $W$
which is linearly dependent as per the left side of implication condition in the first part of the RTP.

Thus, now we can say
$a_1\cdot \bar\alpha_1 + ... + a_r \cdot \bar\alpha_r = 0 \ \ ... (i)$  
such that _not all_ $a_1, … a_r$ are 0

Note that $a_r$ _cannot_ be $0$ because that would imply that the set $\{\bar\alpha_1, \bar\alpha_2 … \bar\alpha_{r-1}\}$ is linearly dependent,
which it can't be by our definition of the $r$ (we assumed that $\bar\alpha_r$ is the first element such that everything before it and including it gives us a linearly dependent set).
Thus we can re-write $(i)$

$- a_1\cdot \bar\alpha_1 - .... - a_{r-1}\bar\alpha_{r-1}  = a_r \cdot \bar\alpha_r$

and since $a_r$ is non-zero, it has a multiplicative inverse, thus

$(-a_1  a_r^{-1}) \cdot \bar\alpha_1 + (-a_2  a_r^{-1}) \cdot \bar\alpha_2 + … + (-a_{r-1}  a_r^{-1}) \cdot \bar\alpha_{r-1} = \bar\alpha_r$

**The second part**:
This is trivial because if there exists such an $\bar\alpha_r$ then the set $\{\bar\alpha_1, \bar\alpha_2 .. \bar\alpha_r\}$ is linearly dependent and the super set of any linearly dependent set is itself linearly dependent.

*Note to the reader: the professor here goes into a mini discussion about why $r$'s range goes from $2$ to $k$ and why it can't be $1$. I haven't included that entire discussion because the theorem talks about _preceding vectors_ in the set and there is nothing preceding $\bar\alpha_1$ and therefore $r$ can't be $1$.*

Also note that we're strictly concerned with a finite set.

**Theorem**:
If the vectors space $V(F)$ is spanned by a linearly dependent set of vectors say
$$
W = \{\bar\alpha_1, \bar\alpha_2, ... \bar\alpha_k\}
$$
then there exists a __proper subset__ of $W$ that can span the entire vector space $V(F)$

**Proof**:
Let $W$ be linearly dependent.
We proved earlier that there exists an $\bar\alpha_r$ in $W$ such that it can be expressed as a linear combination of the vectors preceding it. We can trivially say that this implies that $\bar\alpha_r$ can be represented as a linear combination of _all the elements_ of $W$.

therefore, let

$$
\bar\alpha_r = c_1 \cdot \bar\alpha_1 + c_2 \cdot \bar\alpha_2 + ... + c_k \cdot \bar\alpha_k
$$

where $c_1, c_2, … c_k \in F$

consider an arbitrary vector $\bar\beta$
we know that $W$ spans the entire $V(F)$ and therefore $V(F) = L(W)$
thus $\bar\beta \in L(W)$
thus

$$
\bar\beta = b_1 \cdot \bar\alpha_1 + b_2 \cdot \bar\alpha_2 + ... + b_k \cdot \bar\alpha_k \\

\text{where, } b_1 .. b_k \text{ are scalars} \\

\bar\beta = b_1 \cdot \bar\alpha_1 + b_2 \cdot \bar\alpha_2 + ... + b_r \cdot \bar\alpha_r + ... b_k \cdot \bar\alpha_k
$$

replacing $\bar\alpha_r$

$$
\bar\beta = b_1 \cdot \bar\alpha_1 + b_2 \cdot \bar\alpha_2 + ... + b_r \cdot (c_1 \cdot \bar\alpha_1 + c_2 \cdot \bar\alpha_2 + ... + c_k \cdot \bar\alpha_k) + ... b_k \cdot \bar\alpha_k \\
\\

\bar\beta = (b_1 + b_r c_1)\cdot\bar\alpha_1 + (b_2 + b_r c_2)\cdot\bar\alpha_2 + ... + (b_{r-1} + b_r c_{r-1})\cdot\bar\alpha_{r-1} + ... + (b_k + b_r c_k)\cdot\bar\alpha_k
$$

So $\bar\beta$ has been represented by the set of vectors $W' = \{\bar\alpha_1, \bar\alpha_2, … \bar\alpha_{r-1}, … \bar\alpha_k\}$ which clearly _does not_ have $\bar\alpha_r$ thus $W'$ _proper subset_ of $W$ . Since $\bar\beta$ was an arbitrary vector, we can say that $W'$ spans the entire vector space.

Hence proved.

## Basis
**Definition**: A linear **basis** _(pl. bases)_ (or a _coordinate system_) in a vector space, is a set $X$ such that:
- $X$ is an independent set, i.e. a linear combination of all it's elements results in $\phi$ if and only if all the coefficients are $0$
- Every vector in the vector space is a linear combination of the elements of $X$


## Dimension
**Definition**:
The number of vectors in a basis of the vector space $V(F)$ is called the dimension pf $V(F)$ and is defined by $dimm(V)$

Note: A vector space is _finite dimensional_ if it has a finite basis.
Note: A vector space may have more than one basis.

_Note: number of elements of all bases are equal (proof pending)_  

To prove that note, I first need to introduce another theorem:  

__Theorem__  
If $V$ has a basis with $n$ elements then every set of vectors in $V$ which has more than $n$ elements is linearly dependent  
__Proof__  
consider $B = \{v_1, v_2, … v_n\}$ to be a basis (with $n$ elements)  
consider a set $W = \{w_1, w_2, … w_k\}$ and $k > m$  

To prove that $W$ is linearly dependent we need to prove that the equation  

$$
x_1 \cdot w_1 + x_2 \cdot w_2 + .. + x_k \cdot w_k = 0
$$  

has a solution in which not all $x_i$ are $0$.   


since $B$ is a basis, then it is an independent set that spans the whole vector space $V$ and therefore we can represent any vector as a _unique_ linear combination of all the vectors in $B$.   

This leads us to:  

$$
w_1 = a_{11} \cdot v_1 + a_{12} \cdot v_2 + ... + a_{1n} \cdot v_n \\
w_2 = a_{21} \cdot v_1 + a_{22} \cdot v_2 + ... + a_{2n} \cdot v_n \\
.     . \\
.. \\
.. \\
w_k = a_{k1} \cdot v_1 + a_{k2} \cdot v_2 + ... + a_{kn} \cdot v_n
$$

where $a_{ij} \in F$   

this allows us to rewrite $x_1 \cdot w_1 + x_2 \cdot w_2 + .. + x_k \cdot w_k = 0$ as   

$$
x_1(a_{11} \cdot v_1 + a_{12} \cdot v_2 + ... + a_{1n} \cdot v_n) + x_2(a_{21} \cdot v_1 + a_{22} \cdot v_2 + ... + a_{2n} \cdot v_n) + .. + x_k(a_{k1} \cdot v_1 + a_{k2} \cdot v_2 + ... + a_{kn} \cdot v_n) = 0 \\

\Rightarrow (a_{11}x_1 + a_{21}x_2 + ... + a_{k1}x_k) \cdot v_1 + ... + (a_{1n}x_1 + a_{21}x_2 + ... + a_{kn}x_k) \cdot v_n = 0
$$

as the $B$ is independent, the only way the final version of the equation works is if all the coefficients have to be $0$.   

$$
a_{11}x_1 + a_{21}x_2 + ... + a_{k1}x_k = 0 \\
.. \\
.. \\

a_{1n}x_1 + a_{21}x_2 + ... + a_{kn}x_k = 0

$$

these are $n$ homogenous  equations with $k$ variables (all the $x_i$)  with more variables than equations (as $n < k$), thus we know that there need to be infinitely many solutions, in which there has to be a solution in which not all $x_i$ are $0$ 
Hence proved that $W$ is dependent   

__Now, to prove that all bases have the same number of elements__  
Let there exist two bases $B$ and $W$, such that $B$ has $m$ elements and $W$ has $n$ elements and $m \not = n$. Without loss of generality, I assume that $n > m$ .
Since, they're bases we know that they're linearly independent sets. 
As per the last theorem, we know that any set with more elements than a basis has to be _linearly independent_ this is a contradiction to our original assumption that both $B$ and $W$ are bases. 
Hence proved by contradiction that $m=n$ and consequently that all bases have the same number of elements.  


**Question**: Show that the vectors $(1, 1, 1, 1), (0, 1, 1, 1), (0, 0, 1, 1), \text{and } (0, 0, 0, 1)$ form a basis of $\mathbb{R^4(R)}$.

## Linear sum of two subspaces

If $W_1$ and $W_2$ are two subspaces of $V(F)$ then the linear sum of two subspaces is denoted by $W_1 + W_2$
and is the set of the sums $\bar\alpha_1 + \bar\alpha_2$ such that $\bar\alpha_1 \in W_1$ and $\bar\alpha_2 \in W_2$.
More formally:
$$
W_1 + W_2 = \{\bar\alpha_1 + \bar\alpha_2: \bar\alpha_1 \in W_1, \bar\alpha_2 \in W_2\}
$$

**Theorem**:
If $W_1$ and $W_2$ are subspaces of the vector space $V(F)$, then $W_1 + W_2$ is a subspace of $V$

**Proof**:
Let $\bar\alpha, \bar\beta \in W_1 + W_2$ therefore

$$\bar\alpha = \bar\alpha_1 + \bar\alpha_2$$,
where $\bar\alpha_1 \in W_1$ and $\bar\alpha_2 \in W_2$

$$\bar\beta = \bar\beta_1 + \bar\beta_2$$,
where $\bar\beta_1 \in W_1$ and $\bar\beta_2 \in W_2$

Now, for $a, b \in F$  
$$
a \cdot \bar\alpha + b \cdot \bar\beta = a \cdot(\bar\alpha_1 + \bar\alpha_2) + b \cdot (\bar\beta_1 + \bar\beta_2) \\
\Rightarrow a \cdot \bar\alpha + b \cdot \bar\beta = (a \cdot \bar\alpha_1 + b \cdot \bar \beta) + (a \cdot \bar\beta_2 + b \cdot \bar\beta_2)
$$

as $\bar\alpha_1, \bar\beta_1 \in W_1$ we can say (due to closure of scalar multiplication and vector addition)
that $(a \cdot \bar\alpha_1 + b \cdot \bar \beta) \in W_1$  and similarly $(a \cdot \bar\beta_2 + b \cdot \bar\beta_2) \in W_2$
and thus their summation must belong to $W_1 + W_2$ by definition.  

Thus for arbitrary $\bar\alpha, \bar\beta \in W_1 + W_2$, $(a \cdot \bar\alpha + b \cdot \bar\beta) \in W_1 + W_2$.  

Thus, $W_1 + W_2$ must be subspace of $V(F)$ .
