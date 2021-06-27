---
date: 2021-06-11
title: IC Lecture 8
author: Agrim Rawat
code: ec5.102
number: 8
---

## Mutual Information

Given, random variable $X$. Then entropy $H(X)$ is average uncertainly about $X$. Suppose some observer sees $X$.

1. - Uncertainty about $X$ after observing $X=H(X|X)=0$.
   - Reduction in average uncertainty of $X$ after observing $X=H(X)-H(X|X)=H(X)$.

2. Suppose $X$ and $Y$ are related to each other. (captured by a given joint probability distribution $P_{XY}(x,y)=P(X=x,Y=y)\ \forall x,y$).
   - Uncertainty about $X$ after observing $Y=H(X|Y)$.
   - Reduction in average uncertainty of $X$ after observing $Y=H(X)-H(X|Y)$.
   - Also called the information gained about $X$ after observing $Y$ or Mutual Information between $X$ and $Y$.

### Definition

Information obtained about one random variable through observing the other random variable.

$$
\boxed{I(X;Y)\triangleq H(X)-H(X|Y)=H(Y)-H(Y|X)}
$$

On simplifying,

$$
\begin{aligned}
I(X;Y)&=H(X)-H(X|Y)\\
&=-\sum_{x\in\text{supp}(P_X)}P_X(x)\cdot\log_2{P_X(x)}+\sum_{\{x,y\}\in\text{supp}(P_{XY})}P_{XY}(x,y)\cdot\log_2{\frac{P_{XY}(x,y)}{P_Y(y)}}\\
&=-\sum_{\{x,y\}\in\text{supp}(P_{XY})}P_{XY}(x,y)\cdot\log_2{P_X(x)}+\sum_{\{x,y\}\in\text{supp}(P_{XY})}P_{XY}(x,y)\cdot\log_2{\frac{P_{XY}(x,y)}{P_Y(y)}}\\
&=\sum_{\{x,y\}\in\text{supp}(P_{XY})}P_{XY}(x,y)\cdot\log_2{\frac{P_{XY}(x,y)}{P_X(x)\cdot P_Y(y)}}
\end{aligned}
$$

$$
\implies\boxed{I(X;Y)=\sum_{\{x,y\}\in\text{supp}(P_{XY})}P_{XY}(x,y)\cdot\log_2\left(\frac{P_{XY}(x,y)}{P_X(x)\cdot P_Y(y)}\right)=D(P_{XY}||P_X\otimes P_Y)}
$$

### Bounds

1. $I(X;Y)\leq\min(H(X),H(Y))$
2. $I(X;Y)\geq 0$

## Overview of Source Coding

Suppose we have $X\in\{a,b\}$ a binary source with probability distribution $p_X$.

Suppose observer observes one instance of $X$, then wants to communicate through some noise-free medium which can only carry $\{0,1\}$ bits.

In general, we need 1 bit. For example $\cases{a\mapsto 0\\b\mapsto 1}$

Case 1:

- If $R_X$ knows $p_X$ and it happens that $p_X(b)=1,p_X(a)=0$
- Then $R_X$ need not even receive the encoded value of $X$. It can simply declare the value of $X$ to be $b$ as this will be error-free with probability 1 $\implies$ we need 0 length code.

Case 2:

- Suppose we are allowing for a small probability of error $p(\text{error})\leq\epsilon$ for some small $\epsilon\in[0,1)$ but the code length we use is still 0.
- If the receiver always declares the value of $X$ to be $b$ then he is correct with $p_X(b)=1-\epsilon$ and wrong with $p_X(a)=\epsilon$.

