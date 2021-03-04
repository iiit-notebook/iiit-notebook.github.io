---
title: Linear Algebra Lecture 3
date: 2021-02-23
author: Pratyaksh Gautam
code: ma2.101
number: 3
---
## Vector Subspaces

Let $(V, \times)$ be a vector space over the field $(F, +, \cdot)$.  
Now, if $(W, \times)$ ... is a sub

#### **Theorem**
A non empty subset $W$ of $V$ is a subspace of V $iff$:  

1. $W$  is closed with respect to vector addition.

2. $W$ is closed with respect to scalar multiplication.

#### **Proof**
*Forward implication*

Closure with respect to vector addition and scalar multiplication is given.  
Commutative property and associative property are hereditary properties, and thus since they apply to $V$, they must also hold for $W$.

Now, since $F$ is a field, $1 \in F \Rightarrow -1 \in F$  
If $\alpha \in W$, then we have $(-1) \times \alpha \in W$ (since $W$ is close wrt scalar multiplication.)  
So, $- \alpha \in W$.  

Now, since we know that $W$ is closed wrt vector addition:
$$\alpha + (- \alpha) = \phi \in W$$
Thus, from this we have existence of inverse, as well as existence of identity.

Rest of the properties needed can be proven trivially.

*Backward implication*:

Trivial proof.

#### **Theorem**
The intersection of any two subspaces of a vector space, is also a subspace.

#### **Proof**
Let $W_1, W_2$ be two subspaces of the vector space $V$.  
Then $W_1 \Cap W_2$ is non empty.

#### **Theorem**
The union of any two subspaces of a vector space, is also a subsspace, $iff$ one subspace is a subset of the other.

*Forward implication*:

Trivial proof.

*Backward implication*:

Assume that there is such a union of two vector subspaces, such that neither is the subset of the other, and the union itself is a vector subspace.

Now if neither is the subset of the other, there must be some element that belongs to *only* the second subspace, but not the first,
and similiarly another element that belonges to the first of the subspaces but not the second.

let these be alpha and beta,
then alpha + beta belongs to the union of the two subspaces
(by closure of addition of vectors)

Which means alpha + beta is in W1 or it is in W2.

Case 1: alpha + beta belongs to W1

then since alpha is in W1, implies its inverse, -alpha is also in W1
so (alpha + beta) - alpha is also in W1
implies beta is in W1
which is a contradiction

Case 2: alpha + beta belongs to W2

Similarly we get a contradiction telling us that alpha is in W2
