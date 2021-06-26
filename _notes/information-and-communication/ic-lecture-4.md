---
date: 2021-05-31
title: IC Lecture 4
author: Agrim Rawat
code: ec5.102
number: 4
---

**NOTE : Support of a function**

Given a function $f:X\mapsto\mathbb{R}$ then support of $f$ is defined as

$$
\boxed{\text{supp}(f)=\{x\in X|f(x)\neq 0\}}
$$

---

## Joint Entropy for Independent RVs

The **joint entropy** of two ***independent*** random variables $X$ and $Y$ is defined as follows

$$
\boxed{H(X,Y)=H(X)+H(Y)}
$$

### Proof

Take  two random variables $X$ and $Y$. Here $\Omega$ is the domain of $Y$

**Claim 1 :** If $X$ and $Y$ are independent, then

$$
P(X=x,Y=y)=P(X=x)\cdot P(Y=y)\ \ \forall x,y
$$

**Claim 2 :** The following holds regardless if $X$ and $Y$ are independent or not

$$
\sum_{y\in\Omega}P(X=x,Y=y)=P(X=x)
$$

**Proof of Claim 2 :**
1. For two disjoint events $A$ and $B$, $P(A\cap B)=0$ and $P(A\cup B)=P(A)+P(B)$
2. If $B_i$ are disjoint events, then for any set $A$, $A\cap B_i$ are also disjoint; since, $A\cap B_i\subseteq B_i$
3. $(A\cap B)\cup(A\cap C)=A\cap(B\cup C)$
Now, since all values of $Y$ will be disjoint, therefore, $(X=x)\cap(Y=y)$ is also disjoint. So,

$$
\begin{aligned}
\sum_{y\in\Omega}P(X=x,Y=y)&=\sum_{y\in\Omega}P((X=x)\cap(Y=y))\\
&=P\left(\bigcup_{y\in\Omega}(X=x)\cap(Y=y)\right)\\
&=P\left((X=x)\cap\left[\bigcup_{y\in\Omega}(Y=y)\right]\right)\\
&=P((X=x)\cap\Omega)\\
&=P(X=x)
\end{aligned}
$$

Let $\mathcal{X}=\text{supp}(P_X),\mathcal{Y}=\text{supp}(P_Y)$.

Using the above claims we can proceed with the final proof as follows,

$$
\begin{aligned}
H(X,Y)&\triangleq-\sum_{x\in\mathcal{X}}\sum_{y\in\mathcal{Y}}P_{XY}(x,y)\cdot\log_2{P_{XY}(x,y)}\\
&=-\sum_{x\in\mathcal{X}}\sum_{y\in\mathcal{Y}}P_{XY}(x,y)\cdot\{\log_2{P_X(x)}+\log_2{P_Y(y)}\}\\
&=-\sum_{x\in\mathcal{X}}\sum_{y\in\mathcal{Y}}P_{XY}(x,y)\cdot\log_2{P_X(x)}-\sum_{x\in\mathcal{X}}\sum_{y\in\mathcal{Y}}P_{XY}(x,y)\cdot\log_2(P_Y(y))\\
&=-\sum_{x\in\mathcal{X}}\log_2{P_X(x)}\cdot\sum_{y\in\mathcal{Y}}P_{XY}(x,y)-\sum_{x\in\mathcal{Y}}\log_2{P_Y(y)}\cdot\sum_{x\in\mathcal{X}}P_{XY}(x,y)\\
&=-\sum_{x\in\mathcal{X}}P_X(x)\cdot\log_2{P_X(x)}-\sum_{y\in\mathcal{Y}}P_Y(y)\cdot\log_2{P_Y(y)}\\
&=H(X)+H(Y)
\end{aligned}
$$

## Conditional Probability Distribution

**Probability Distribution :** $\boxed{P_X(x)\ \ \forall x\in X\ \text{and}\sum_{x\in X}P_X(x)=1}$

**Conditional Probability :** Given $P_Y(y)\neq 0$, $\boxed{P_{X|Y}(x|y)\triangleq\frac{P_{XY}(x,y)}{P_Y(y)}}$

**Conditional Probability Distribution :** Define $Q$ as, $\boxed{Q(x)=P(x|y)}$. This is a probability distribution over $X$ as,

$$
\sum_{x\in X}Q(x)=\sum_{x\in X}P_{P|Y}(x|y)=\sum_{x\in X}\frac{P_{XY}(x,y)}{P_Y(y)}=1
$$

Here, $Q$ is called *conditional probability distribution*.

## Conditional Entropy

Let $\mathcal{X}=\text{supp}(P_X),\mathcal{Y}=\text{supp}(P_Y)$.

1. $H(X|Y)\triangleq\sum_\limits{y\in\mathcal{Y}}P(y)\cdot H(X|Y=y)$
2. $H(X|Y=y)\triangleq-\sum_\limits{x\in\mathcal{X}}P_{X|Y}(x|y)\cdot\log_2{P_{X|Y}(x|y)}$