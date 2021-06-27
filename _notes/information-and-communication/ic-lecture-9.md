---
date: 2021-06-14
title: IC Lecture 9
author: Agrim Rawat
code: ec5.102
number: 9
---

## Ideas

1. If we are willing to live with / tolerate some small probability of decoding error, we can compress the source better $\implies$ we can have smaller length code for representing the source.<br>By ignoring source symbols which have very low probability of occurrence.<br>We ignore source symbols which have very low probability of occurrence.

2. "Club" multiple RV instances, $X_1,X_2,X_3$ are the three instances.<br>$X_1,X_2,X_3\in\{\{a,a,a\},...,\{b,b,b\}\}=\{a,b\}^3$.<br>Assume $X_1,X_2,X_3$ are independent RVs.<br>$P_{X_1,X_2,X_3}(x_1,x_2,x_3)=P_{X_1}(x_1)\cdot P_{X_2}(x_2)\cdot P_{X_3}(x_3)\ \forall x_1,x_2,x_3\in\{a,b\}$<br>We know joint distribution from the individual distributions (also called **marginal distributions**).<br>$P_{X_1,X_2,X_3}(x_1,x_2,x_3)=P_{X_1,X_2,X_3}(\vec{x})=p^{n_a(\vec{x})}\cdot(1-p)^{n_b(\vec{x})}$<br>Where $\vec{x}=(x_1,x_2,x_3)$; $n_a(\vec{x})$ is the number of times $a$ occurs in $\vec{x}$; $p$ is probability of occurrence of $a$.

## Compression Schemes

Suppose we have a compression scheme $C_S$ (a mapping) for a single RV<br>
$$a
C_S:\{a,b\}\mapsto\{0,1\}
$$

For three RV it will become<br>
$$
C'_S:\{a,b\}^3\mapsto\{0,1\}^3
$$

This new code $C'_S$ taking 3 bits for 3 RVs is as good as original code $C_S$ taking 1 bit for 1 RV.

### How to do better

To do better than this, we have to use less than 3 bits, i.e. 0, 1 , 2 bits.

In the case of encoding only one source symbol, our possible code length choices are either 0 or 1.

Here we have more choices 0, 1, 2, 3 length binary strings can be used

$$
C'_S=\{a,b\}^3\mapsto\{0,1\}
$$

This is good code for the following case:
- $(a,a,a)$ has very high probability.
- The rest of the 7 vectors have very small probability.
- $C'_S((a,a,a))=0$ and $C'_S(\vec{x})=1\forall \vec{x}\in\{a,b\}^3\setminus(a,a,a)$.

---

#### Normalized length

It is the ratio of the length of source code to the length of source symbols.

- $C_S:\{a,b\}^3\mapsto\{0,1\}^3\longrightarrow \frac{3}{3}=1$
- $C_S:\{a,b\}^3\mapsto\{0,1\}\ \longrightarrow \frac{1}{3}$

---

Suppose we are allowed to combine multiple source symbols and encode them together into some fixed length binary string, then this gives a more efficient source code (smaller normalized length)

#### Example

$$
\text{Source }X\sim p_X\\
p_X(a)=p\ \ \ ,\ \ \ p_X(b)=1-p
$$

**Requirements:**

1. We are allowing for encoding long strings and we can tolerate some small probability of error.
2. We have **fixed length source code** (every $n$-length source string gets encoded as an $l$-length binary vector, where $l$ is fixed for all sources strings)

**Assumptions:**

1. $n$-length random source vector is represented by $(X_1,X_2,\dots,X_n)$, where $X_i$ is the RV representing $i^{th}$ output of the source which will belong to $\{a,b\}$.

2. The following is true,<br>
   $$
   \cases{p_{X_i}(a)=p_X(a)\\p_{X_i}(b)=p_X(b)}\implies p_{X_i}=p_X
   $$
   <br>
   So, all $X_i$ have the same distribution and are independent.<br>And so all $X_i$ are said to be **independent and identically distributed**.

**Question:**

Suppose $n$ is a very large number. How many $a$ and $b$ do we expect to see in the random sequence $(X_1,X_2,\dots,X_n)$?

$$
\begin{aligned}
&\text{Number of }a=n\cdot p\\
&\text{Number of }b=n\cdot(1-p)\\
&\text{Total number of sequences}=2^n\\
&\text{Number of sequences with }(n\cdot p)\ a\text{'s and }(n\cdot(1-p))\ b\text{'s}={n\choose np}
\end{aligned}
$$

So the source code we want to use will encode only these $n\choose np$ sequences with unique codewords. All other sequences are combined under a single dummy codeword.