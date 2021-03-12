---
title: Linear Algebra Lecture 8
date: 2021-03-06
author: Shashwat Singh, Pratyaksh Gautam
code: ma2.101
number: 8
---
## Linear Mapping

**Theorem**: Let $$\{ x_1, x_2 ..., x_n\}$$ be a basis for a finite dimensional vector space $V(F)$ and $$\{ y_1, y_2 ..., y_n\}$$ be an arbitrary set of vectors in $W(F)$.
Then there exists a unique linear mapping from the $V$ to $W$ such that
$f(x_1) = y_1, f(x_2) = y_2 … f(x_n) = y_n$ 

**Proof**:  
__proof that $f$ is a linear mapping__
Let $x \in V$, then $x = a_1 x_1 + a_2 x_2 + ... + a_n x_n$, where $a_i \in F$.

Then we define our function $f: V \rightarrow W$ such that
$$
f(\bar x) = a_1 \cdot \bar y_1 + a_2 \cdot \bar y_2 + ... + a_n \cdot \bar y_n
$$
Note: since $a_1 .. a_n$ are _unique_ for a given $\bar x$, we can say that the function is well defined. 

Now we can write an $x_i \in \{x_1, x_2, .. x_n\}$ as $x_i = 0 \cdot x_1 + … + a_i \cdot x_i + ...$ and thus
$$
f(x_i) = 0 \cdot y_1 + ... + a_i \cdot y_i + ... + 0 \cdot y_n
$$
and so on.
consider another vector $\bar \beta \in V$ such that:   

$\bar \beta = b_1 \cdot x_1 + b_2 \cdot x_2 + .… + b_n \cdot \bar x_n$

thus, by definition of the function, we have:

$$
f(\bar\beta) = b_1 \cdot y_1 + b_2 \cdot y_2 + ... + b_n \cdot y_n
$$

now, consider $\bar x + \bar\beta = (a_1 + b_1) \cdot x_1 + … + (a_n + b_n) \cdot x_n$ 
and accordingg to the definition of the function we have:  

$$
f(\bar x + \bar\beta) = (a_1 + b_1) \cdot y_1 + ... + (a_n + b_n) \cdot y_n \\
\Rightarrow f(\bar x + \bar\beta) = a_1 \cdot y_1 + ... + a_n \cdot y_n + b_1 \cdot y_1 + ... + b_n \cdot y_n \\
\Rightarrow f(\bar x + \bar\beta) = f(\bar x) + f(\bar \beta) \\
\text{.......... i}
$$

This is the first required stipulation for a linear mapping.

Now, consider an arbitrary $a \in F$ and consider an arbitrary $\bar x \in V$ i.e. $\bar x = a_1 \cdot x_1 + … + a_n \cdot x_n$.  
now $a \cdot \bar x = a a_1 \cdot x_1 + … + a a_n \cdot x_n$  
which is $a \cdot \bar x = (a a_1) \cdot x_1 + … + (a a_n) \cdot x_n$
now, by definition of the function, we have
$f(a \cdot \bar x) = (a a_1) \cdot y_1 + … + (a a_n) \cdot y_n$
and by distribution, we have

$$
f(a \cdot \bar x) = a(a_1 \cdot y_1 + ... + a_n \cdot y_n) \\
\Rightarrow f(a \cdot \bar x) = a \cdot f(\bar x)
$$ 

This is the second required stipulation of a linear mapping.
Thus $f$ is indeed a linear mapping. 

__proof that $f$ is unique (given that it is a linear mapping)__:
Now suppose we had another linear mapping $g$ such that $g(x_1) = y_1, g(x_2) = y_2 … g(x_n) = y_n$ 
let $\bar x \in V$ thus $\bar x = a_1 \cdot x_1 + … + a_n \cdot x_n$ thus 
 
$$
g(\bar x) = a_1 \cdot g(x_1) + ... + a_n \cdot g(x_n) \text{ due to linearity } \\
\Rightarrow g(\bar x) = a_1 \cdot y_1 + ... + a_n \cdot y_n
$$ 

which is exactly for $f$ was, thus $f=g$ and thus $f$ has to be unique.

## Kernel and Image of Linear Map
__Definition:__ Let $f:U \rightarrow W$ be a linear mapping from a vector space $U(F)$ to a vector space $W(F)$.
Then $ker(f)$ is the set of all $x \in U$ which map onto $\phi_W$, the vector additive identity element of W.
$ker(f) = \{x \in U \| f(x) = \phi_W \in W \}$

__Definition:__ Let $f: U \rightarrow W$ be a linear mapping. Then the set of all images of all elements $x \in U$ is called the range of $f$, also written as $R_f$  
Thus, $r_f = f(U) = \{y \in W | y = f(x) x \in U\}$ 

**Theorem**: Let $f: V \rightarrow W$ be a linear mapping from a vecotr space $V(F)$ to a vector space $W(F)$ over the same field F. Then
1. $ker(f)(F)$ is a subpace of $V(F)$.
2. $f(v)(F)$ is a subpace of $W(F)$.

**Proof**:
__of part 1__  
 Let $\bar x, \bar y \in ker(f)$ then $\bar x, \bar y \in U$, since $f$ is a linear mapping, we have 
 $f(a\cdot \bar x + b \cdot \bar y) = a \cdot f(\bar x) + b \cdot f(\bar y)$ and we know by defunution of Kernel that $f(\bar x) =  f(\bar y) = \bar\phi_W$ and thus we have:  
$$
f(a\cdot \bar x + b \cdot \bar y) = a \cdot \bar\phi_W + b \cdot \bar\phi_W \\
\Rightarrow f(a\cdot \bar x + b \cdot \bar y) = \bar\phi_W \\
$$
and thus by definition of Kernel, we can say that $(a \cdot \bar x + b \cdot y) \in kerr(f)$ and therefore $kerr(f)$ is a subspace of $U$.

__of part 2__  
Let $\bar y_1, \bar y_2 \in f(U)$ then there exist $\bar x_1, \bar x_1 \in U$ such that $f(\bar x_1) = \bar y_1$ and $f(\bar x_2) = \bar y_2$   
Since $U$ is a vector space and let $a, b \in F$ we know $(a \cdot \bar x_1 + b \cdot \bar x_2) \in U$ and thus by definition of $f(V)$ we can say that $f(a \cdot \bar x_1 + b \cdot \bar x_2) \in f(V)$   
which is equal to 
$$
f(a \cdot \bar x_1) + f(b \cdot \bar x_2) \\
= a \cdot f(\bar x_1) + b \cdot f(\bar x_2) \\
= a \cdot \bar y_1 + b \cdot \bar y_2 \\
$$
thus if $\bar y_1, \bar y_2 \in f(V) \Rightarrow a \cdot \bar y_1 + b \cdot \bar y_2 \in f(V)$ making it a subspace.


$ker(f)$ is the **null space**, and $dim(ker(f))$ is called the **nullity** of the space.

$f(v)(F)$ is called the **range space** of f and the dimension of $f(V)$ is called the rank $r(f)$ of a linear transformation $f$.

(Sylvester law - rank nullity theorem)
__Theorem__: Let $f: V \rightarrow W$ be linear mapping. Both the vector spaces are on the field $F$ then $dimm(V) = dimm(kerr(f)) + dimm(f(V))$  
Say, $dimm(kerr(f)) = r \leq n$   
and let $\{x_1, x_2 … x_r\}$ be a basis of $kerr(f)$ then we can extend it to a basis $\{x_1, x_2, … x_r, y_1, y_2 .. y_{n-r}\}$ (__proof is pending on this statement__)
Now, for any $y \in f(V)$, there exists $x \in V$ such that $y = f(x)$ in terms of the basis, the $x$ can be written as $x = a_1 \cdot x_1 + a_2 \cdot x_2 +  … + a_r \cdot x_r + b_1 \cdot y_1 + b_2 \cdot y_2 + … + b_{n-r} \cdot y_{n-r}$ 
and let $z = f(x) = a_1 \cdot f( x_1) + a_2 \cdot f(x_2) +  … + a_r \cdot f(x_r) + b_1 \cdot f(y_1) + b_2 \cdot f(y_2) + … + b_{n-r} \cdot f(y_{n-r})$
Now,   
note that  

$$
f(a_1\cdot x_1 + a_2\cdot x_2 ... a_r\cdot x_r) = \bar\phi_W
$$

as $\{x_1, x_2 .. x_r\}$ spans the kernel.
and thus we can reqrite $z$ as $z = f(x) =  b_1 \cdot f(y_1) + b_2 \cdot f(y_2) + … + b_{n-r} \cdot f(y_{n-r})$ thus an arbitrary $z \in f(V)$ can be represented as a linear combination of $\{f(y_1), f(y_2), … f(y_{n-r}\}$ ..… (I) 

so let $B = \{f(y_1), f(y_2), … f(y_{n-r}\}$  
to prove that $B$ is linearly independent. 
let

$$
a_1 \cdot f(x=y_1) + a_2 \cdot f(y_2) + .. + a_{n-r} \cdot f(y_{n-r}) = \bar \phi \\
\Rightarrow f(a_1 \cdot y_1 + a_2 \cdot y_2 + a_3 \cdot y_3 + ... + a_{n-r} \cdot y_{n-r}) = \bar\phi
$$

thus $a_1 \cdot y_1 + … + a_{n-r} \cdot y_{n-r} \in kerr(f)$
since $\{x_1, x_2, … x_{r} \}$ is a bsasis of kernel, thus there must exist $d_1, d_2, … d_r$ such that 

$a_1 \cdot y_1 + … + a_{n-r} \cdot y_{n-r} = d_1 \cdot x_1 + d_2 \cdot x_2 + .. + d_r \cdot x_r$
and thus 
$a_1 \cdot y_1 + … + a_{n-r} \cdot y_{n-r} -  d_1 \cdot x_1 - d_2 \cdot x_2 - .. - d_r \cdot x_r = \phi$ 
but we know that $\{x_1, x_2, … x_r, y_1, y_2 .. y_{n-r}\}$ is a basis and therefore is independent and thus we can say 
$a_1 = a_2 = … = a_{n-r} = d_1 = d_2 = … = d_r = 0$ and thus
$a_1 = a_2 = … = a_{n-r} = 0$ 

in summary, 

$$
a_1 \cdot f(x=y_1) + a_2 \cdot f(y_2) + .. + a_{n-r} \cdot f(y_{n-r}) = \bar \phi \\

\Rightarrow  a_1 = a_2 = … = a_{n-r} = 0
$$

therefore we can say the $B$ is independent .… (II)

thus, by (I) and (II) we can say that $B$ makes a bsis of $f(V)$ and $dimm(f(V)) = n - r$ 
thus

$$
dim(V) = n \\
\Rightarrow dim(V) = r + (n - r)
= dim(kerr(f)) + dim(f(V))
$$

