---
date: 2021-05-28
title: IC Lecture 3
author: Agrim Rawat
code: ec5.102
number: 3
---

## Information

### Definition

- **Information** can be thought of as the measure of uncertainty.
- Anything which interests us in an experiment can be considered as information.
- An experiment can generate a variety of signals but we may not be interested in all of them, then the signal in which we are interested is called information while the other signals will be classified as noise.

### Hartley's Measure

#### Definition

For a given set $X$ from which a sample is uniformly picked, the information in outcome is given as
$$
I(X)=\log_2(|X|)
$$
where $|X|$ is the cardinality of $X$.

#### Disadvantage

The weakness of Hartley's measure is that it ignores the probabilities of the various values of $X$. So, in cases where probabilities are involved Hartley's measure cannot be applied.

### Extending Hartley's Measure of Information to Probabilities

Since the information is the uncertainty/surprise in an event, we can say that,

$$
\text{Information content in Event}\propto\frac{1}{P(\text{Event})}
$$

Consider two independent random variables $X_1$ and $X_2$. We know that their joint probability,

$$
P(X_1=x_1,X_2=x_2)=P(X_1=x_1)\cdot P(X_2=x_2)
$$

Let the information content be represented by function $I$. The joint information in $X_1$ and $X_2$ is

$$
I(P(X_1=x_1,X_2=x_2))=I(P(X_1=x_1)\cdot P(X_2=x_2))
$$

But intuitively, joint information in $X_1$ and $X_2$ is the sum of the individual information in $X_1$ and $X_2$. So,

$$
I(P(X_1=x_1,X_2=x_2))=I(P(X_1=x_1))+I(P(X_2=x_2))
$$

Thus, $I$ is a function such that

$$
I(P(X_1=x_1)\cdot P(X_2=x_2))=I(P(X_1=x_1)+I(P(X_2=x_2))
$$

This property is satisfied if $I$ is the $\log$ function.
So, Information contained in a random variable $X$ is given as

$$
I(X=x)=\log_2\left(\frac{1}{P(X=x)}\right)
$$

### Shannon's Measure

#### Definition

The **average information content** or the **entropy** in random variable $X$ is defined as the weighted sum of the individual information contents. This is called the **Shannon's Measure**

$$
H(X)\triangleq-\sum_{i=1}^{|X|}P(X=x_i)\log_2(P(X=x_i))
$$

#### Joint Entropy

The **joint entropy** of two random variables $X\to\mathcal{X}$ and $Y\to\mathcal{Y}$  (where $\mathcal{X}$ and $\mathcal{Y}$ represent the set of outcomes) is defined as follows

$$
H(X,Y)\triangleq-\sum_{x\in\mathcal{X}}\sum_{y\in\mathcal{Y}}P(X=x,Y=y)\log_2(P(X=x,Y=y))
$$