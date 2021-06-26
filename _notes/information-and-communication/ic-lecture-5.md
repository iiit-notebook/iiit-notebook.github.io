---
date: 2021-06-02
title: IC Lecture 5
author: Agrim Rawat
code: ec5.102
number: 5
---

*Continuing from Lecture 4,*

Using (1) and (2)

$$
\begin{aligned}
H(X|Y)&=\sum_{y\in\mathcal{Y}}P(y)\cdot H(X|Y=y)\\
&=-\sum_{y\in\mathcal{Y}}P(y)\cdot\sum_{x\in\mathcal{X}}P(x|y)\cdot\log_2{P(x|y)}\\
&=-\sum_{y\in\mathcal{Y}}\sum_{x\in\mathcal{X}}P(y)\cdot P(x|y)\cdot\log_2{P(x|y)}\\
&=-\sum_{y\in\mathcal{Y}}\sum_{x\in\mathcal{X}}\left(P(y)\cdot\frac{P(x,y)}{P(y)}\right)\cdot\log_2{\frac{P(x,y)}{P(y)}}\\
\end{aligned}
$$

$$
\implies\boxed{H(X|Y)=-\sum_{y\in\mathcal{Y}}\sum_{x\in\mathcal{X}}P_{XY}(x,y)\cdot\log_2{\frac{P_{XY}(x,y)}{P_Y(y)}}}
$$

Where $\mathcal{X}=\text{supp}(P_X),\mathcal{Y}=\text{supp}(P_Y)$.

## Chain Rule

$$
\boxed{H(X,Y)=H(X)+H(Y|X)=H(Y)+H(X|Y)}
$$

**Proof :**

Before proving, we know that (refer Lecture 4) (taking domain of $X$ as $\mathfrak{X}$ and $\mathcal{X}=\text{supp}(P_X)$

$$
\begin{aligned}
P_Y(y)&=\sum_{x\in\mathfrak{X}}P_{XY}(x,y)\\
&=\sum_{x\in\mathcal{X}}P_{XY}(x,y)+\sum_{x\in\mathfrak{X}\texttt{\\}\mathcal{X}}P_{XY}(x,y)\\
&=\sum_{x\in\mathcal{X}}P_{XY}(x,y)+\sum_{x\in\mathfrak{X}\texttt{\\}\mathcal{X}}P_{Y|X}(y|x)P_X(x)\\
&=\sum_{x\in\mathcal{X}}P_{XY}(x,y)
\end{aligned}
$$

Also we know,

$$
\begin{aligned}
H(X|Y)&=-\sum_{y\in\mathcal{Y}}\sum_{x\in\mathcal{X}}P_{XY}(x,y)\cdot\log_2{\frac{P_{XY}(x,y)}{P_Y(y)}}\\
&=-\sum_{y\in\mathcal{Y}}\sum_{x\in\mathcal{X}}P_{XY}(x,y)\cdot\log_2{P_{XY}(x,y)}+\sum_{y\in\mathcal{Y}}\sum_{x\in\mathcal{X}}P_{XY}(x,y)\cdot\log_2{P_Y(y)}\\
&=-\sum_{y\in\mathcal{Y}}\sum_{x\in\mathcal{X}}P_{XY}(x,y)\cdot\log_2{P_{XY}(x,y)}+\sum_{y\in\mathcal{Y}}P_Y(y)\cdot\log_2{P_Y(y)}\\
&=H(X,Y)-H(Y)
\end{aligned}
$$

$$
\implies H(X,Y)=H(Y)+H(X|Y)
$$

Hence, proved.

## Some Properties of Entropy

Can we bound $H(X)$ from above and below? Domain of $P_X$ is $\mathfrak{X}$

$$
\boxed{0\leq H(X)\leq\log_2|\mathfrak{X}|}
$$

1.  Proof for $H(X)\geq 0$:

$$
H(X)=-\sum_{x\in\text{supp}(P_X)}P(x)\cdot\log{P(x)}
$$

Since $x\in\text{supp}(P_X)$, therefore $P_X(x)>0$. So, $H(X)\geq 0$.

Also, $H(X)=1$ if and only if there exists some $x_0$ such that, $P_X(x_0)=1$ and $P_X(x)=0\ \forall\ x\neq x_0$. Meaning the support of $P_X$ is a singleton set.

**Some statements before we prove part 2**

- Convex Combination: $\sum_{i=1}^n\lambda_ix_i$ where $\lambda_i\geq0$ and $\sum_{i=1}^n\lambda_i=1$

- Jensen's Inequalities:

	For Convex Function,

	$$
	f\left(\sum_{i=1}^n\lambda_ix_i\right)\leq \sum_{i=1}^n\lambda_if\left(x_i\right)
	$$

	For Concave Function,

	$$
	f\left(\sum_{i=1}^n\lambda_ix_i\right)\geq \sum_{i=1}^n\lambda_if\left(x_i\right)
	$$


2.  Proof for $H(X)\leq\log_2{|X|}$ :

$$
H(X)=-\sum_{x\in\text{supp}(P_X)}P(x)\cdot\log{P(x)}
$$

Since $x\in\text{supp}(P_X)$ so $P(x)>0$. Also $\sum_{i=1}^nP(x)=1$. Thus, using concavity of $\log$ function,

$$
\begin{aligned}
H(X)&=\sum_{x\in\text{supp}(P_X)}P(x)\cdot\log_2\left(\frac{1}{P(x)}\right)\\
&\leq\log_2\left(\sum_{s\in\text{supp}(P_X)}P(x)\cdot\frac{1}{P(x)}\right)\\
&=\log_2|\text{supp}(P_X)|\leq\log_2{|\mathfrak{X}|}
\end{aligned}
$$