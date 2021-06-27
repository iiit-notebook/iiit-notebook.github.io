---
date: 2021-06-09
title: IC Lecture 7
author: Agrim Rawat
code: ec5.102
number: 7
---

## Joint Entropy of Multiple RVs

$$
\boxed{H(X_1,...,X_n)=\sum_{\{x_1,...,x_n\}\in\text{supp}(P_{X_1,...X_n})}P(X_1,...,X_n)\cdot\log_2{\frac{1}{P(X_1,...,X_n)}}}
$$

### Chain Rule for Joint Entropy

$$
\boxed{H(X_1,...X_n)=H(X_1)+H(X_2|X_1)+H(X_3|X_1,X_2)+...+H(X_n|X_1,...,X_{n-1})=H(X_1)+\sum_{i=2}^{n-1}H(X_i|X_1,\dots,X_{i-1})}
$$

## Conditional Entropy of Multiple RVs

$$
H(X,Y|U,V)\triangleq\sum_{\{u,v\}\in\text{supp}(P_{UV})}P_{UV}(u,v)\cdot H(X,Y|U=u,V=v)
$$


$$
H(X,Y|U=u,V=v)\triangleq\sum_{\{x,y\}\in\text{supp}(P_{XY|UV})}P_{XY|UV}(x,y|u,v)\cdot\log_2{\frac{1}{P_{XY|UV}(x,y|u,v)}}
$$
This can be extended to any number of variables before and after the conditioning.

## Chain Rule in Probability

$$
\begin{aligned}
p(x_1,\dots,x_n)&=p(x_1)\cdot p(x_2,\dots,x_n|x_1)\\
&=p(x_1)\cdot p(x_2|x_1)\cdot p(x_3,\dots,x_n|x_1,x_2)\\
&=p(x_1)\cdot p(x_2|x_1)\cdot p(x_3|x_1,x_2)\cdot p(x_4,\dots,x_n|x_1,x_2,x_3)\\
&=\cdots\\
&=p(x_1)\cdot p(x_2|x_1)\cdot p(x_3|x_1,x_2)\cdots p(x_n|x_1,\dots,x_{n-1})
\end{aligned}
$$

### With Conditional Probability

$$
\boxed{p(x,y|z)=p(x|z)\cdot p(y|x,z)}
$$

**Example:**

$$
\begin{aligned}
p(x_1,x_2,x_3|y_1,y_2)=\frac{p(x_1,x_2,x_3,y_1,y_2)}{p(y_1,y_2)}\\
\end{aligned}
$$

LHS can also be written as,

1.
$$
p(x_1,x_2,x_3|y_1,y_2)=p(x_1,x_2|y_1,y_2)\cdot p(x_3|x_1,x_2,y_1,y_2)
$$

2.
$$
p(x_1,x_2,x_3|y_1,y_2)=\frac{p(x_1,x_2,x_3,y_2|y_1)}{p(y_2|y_1)}=\frac{p(x_3,y_2|y_1)\cdot p(x_1,x_2|x_3,y_1,y_2)}{p(y_2|y_1)}
$$
