---
date: 2021-02-18
title: Linear Algebra Lecture 1
code: ma2.101
author: Pratyaksh Gautam
number: 1
---

## Vector Spaces
Let F be a given field whose elements are called *scalars* and V be a non-void set whose elements are called **vectors**.
The set V is a **vector space** or a **linear space** over the field F if the following conditions are satisfied:  
1. For any two vectors $\alpha, \beta \in V$, $\alpha + \beta \in V$ i.e the vectors are **closed under vector addition**.
2. For any two vectors, $\alpha, \beta \in V$, $\alpha + \beta = \beta + \alpha$ i.e **vector addition is commutative**.
3. For any two vectors, $\alpha, \beta, \gamma \in V$, $\alpha + (\beta + \gamma) = (\alpha + \beta) + \gamma$ i.e **vector addition is associative**.
4. There exists a unique vector $\phi \in V$ such that $\alpha + \phi = \alpha = \phi + \alpha$ for all $\alpha \in V$ i.e there exists an **additive identity** in V.
5. For any vector $\alpha \in V$, there exists a unique vector $\omega \in V$ such that $\alpha + \omega = \phi$ i.e there exists **additive inverse** for each element in V.

*Note: Associativity is a [hereditary property](https://en.wikipedia.org/wiki/Hereditary_property).*

[**More on algebraic systems (click here)**]({{ site.baseurl }}{% link _notes/discrete-structures/ds-lecture-22.md %})  
from Discrete Structures Notes by Abhinav Menon
