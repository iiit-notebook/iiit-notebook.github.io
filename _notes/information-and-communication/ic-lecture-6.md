---
date: 2021-06-04
title: IC Lecture 6
author: Agrim Rawat
code: ec5.102
number: 6
---

**Claim:** In Jensen's Inequality, the equality holds when either the function is a straight line or all the pints coincide.

$$
f\left(\sum_{i=1}^n\lambda_ix_i\right)=\sum_{i=1}^n\lambda_if\left(x_i\right)
$$

For this, the function should be neither convex nor concave $\implies$ *function is a straight line*.

But in case the function is either strictly convex or strictly concave, *then all the points will coincide*.

**Proof:**

We know, $\lambda_i\neq0,\sum_{i=1}^n\lambda_i=1$

Suppose $x_1=x_2=...=x_n=x$

$$
\text{LHS}=f\left(\sum_{i=1}^n\lambda_ix_i\right)=f\left(x\cdot\sum_{i=1}^n\lambda_i\right)=f(x)
$$


$$
\text{RHS}=\sum_{i=1}^n\lambda_if(x_i)=f(x)\cdot\sum_{i=1}^n\lambda_i=f(x)
$$

So, $\text{LHS} = \text{RHS}$

Hence, proved.

## Condition when $H(X)=\log_2|\mathfrak{X}|$

(where $\mathfrak{X}$ is the domain of $P_X$).

We know,

$$
H(X)=\sum_{x\in\text{supp}(P_X)}P(x)\cdot\log{\frac{1}{P(x)}}
$$

Now, by concavity of $\log$ and Jensen's Inequality,

$$
H(X)=\sum_{x\in\text{supp}(P_X)}P(x)\cdot\log_2\left(\frac{1}{P(x)}\right)\leq\log_2\left(\sum_{s\in\text{supp}(P_X)}P(x)\cdot\frac{1}{P(x)}\right)=\log_2{|\text{supp}(P_X)|}
$$

For the equality to hold, all $\frac{1}{P(x)}$ should be equal (as proved in the above claim) to some non-zero constant. Let that constant be $c$.

Hence,

$$
\sum_{x\in\text{supp}(P_X)}P(x)=1\implies c\cdot|\text{supp}(P_X)|=1\implies c=\frac{1}{|\text{supp}(P_X)|}
$$

So, for the equality $H(X)=\log_2{|\text{supp}(P_X)|}$

$$
P_X(x)=\frac{1}{|\text{supp}(P_X)|}
$$

If $\text{supp}(P_X)=\mathfrak{X}$, then the probability distribution will be,

$$
\boxed{P_X(x)=\frac{1}{|\mathfrak{X}|}\ \ \ \forall x\in\mathfrak{X}}
$$

This is called the **Uniform Probability Distribution**.

### Lemma

$H(X)=\log_2{|\mathfrak{X}|}$ iff $P_X$ has a uniform probability distribution.

## Relative Entropy

- Also Information Divergence / Kullback–Leibler Divergence

Suppose a random variable $X$ over which two probability distributions $P_X$ and $Q_X$ are defined, then the relative entropy is defined as
$$
\boxed{D(P||Q)\triangleq\sum_{x\in\text{supp}(P_X)}P(x)\cdot\log_2{\frac{P(x)}{Q(x)}}}
$$

**Important:** $D(P||Q)\neq D(Q||P)$

### Claim: $D(P||Q)\geq 0$

**Proof:**

Using Jensen's Inequality and concavity of $\log$ function,

$$
\begin{aligned}
\sum_{x\in\text{supp}(P_X)}P(x)\cdot\log_2{\frac{P(x)}{Q(x)}}&\leq\log_2\left(\sum_{x\in\text{supp}(P_X)}P(x)\cdot\frac{Q(x)}{P(x)}\right)\\
\implies-\sum_{x\in\text{supp}(P_X)}P(x)\cdot\log_2{\frac{P(x)}{Q(x)}}&\geq-\log_2\left(\sum_{x\in\text{supp}(P_X)}P(x)\cdot\frac{Q(x)}{P(x)}\right)\\
\implies D(P||Q)&\geq-\log_2\left(\sum_{x\in\text{supp}(P_X)}Q(x)\right)
\end{aligned}
$$

Since,

$$
\sum_{x\in\text{supp}(P_X)}Q(x)\leq 1\implies-\log_2\left(\sum_{x\in\text{supp}(P_X)}Q(x)\right)\geq 0
$$

Therefore, $D(P||Q)\geq 0$. Hence, proved.

### Claim: $D(P||Q)=0$ iff $P=Q$

- If $P=Q$, it is trivial to see $D(P||Q)=0$.

- If $D(P||Q)=0$, using equality in Jensen's Equations,

$$
\frac{P(x)}{Q(x)}=c\\
\sum_{x\in\text{supp}(P_X)}P(x)=\sum_{x\in\text{supp}(P_X)}c\cdot Q(x)
$$

These equations imply $P=Q$.

### Claim: $0\leq H(X|Y)\leq H(X)$

**Proof:**

$$
H(X|Y)=\sum_{y\in\text{supp}(P_Y)}P_Y(y)\cdot H(X|Y=y)
$$

Since, $P_Y(y)\geq 0$ and $H(X|Y=y)\geq 0$. Therefore, $H(X|Y)\geq 0$.

Now, consider ($\mathcal{X}=\text{supp}(P_X),\mathcal{Y}=\text{supp}(P_Y)$)

$$
\begin{aligned}
H(X)-H(X|Y)&=\sum_{x\in\mathcal{X}}P(x)\cdot\log_2{\frac{1}{P(x)}}-\sum_{x\in\mathcal{X},y\in\mathcal{Y}}P(x,y)\log_2{\frac{1}{P(x|y)}}\\
&=\sum_{x\in\mathcal{X},y\in\mathcal{Y}}P(x,y)\cdot\log_2{\frac{1}{P(x)}}-\sum_{x\in\mathcal{X},y\in\mathcal{Y}}P(x,y)\cdot\log_2{\frac{1}{P(x|y)}}\\
&=\sum_{x\in\mathcal{X},y\in\mathcal{Y}}P(x,y)\cdot\log_2\left(\frac{P(x,y)}{P(x)\cdot P(y)}\right)\\
&=D(P(x,y)||P(x)\cdot P(y))\geq 0
\end{aligned}
$$

Since, both $P(x,y)$ and $P(x)\cdot P(y)$ are valid probability distributions over $X,Y$ so this is the information divergence between the two.

Therefore, $H(X)-H(X|Y)\geq 0\implies H(X|Y)\leq H(X)$.