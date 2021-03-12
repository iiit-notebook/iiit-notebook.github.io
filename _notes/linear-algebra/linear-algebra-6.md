---
title: Linear Algebra Lecture 6
date: 2021-03-02
author: Pratyaksh Gautam, Shashwat Singh
code: ma2.101
number: 6
---

## Direct sum
A vector space $V$ will be called a **direct sum** if it is the linear sum of two vector subspaces of $V$,
$W_1$ and $W_2$ and for all $\alpha \in W_1$ and $\beta \in W_2$,
there are no other vectors $\alpha\prime \in W_1$ and $\beta\prime \in W_2$, such that
$$\alpha + \beta = \alpha\prime + \beta\prime$$

In other words, the vector space $V$ is a direct sum of the vector subspaces $W_1$ and $W_2$,
if and only if each element in $V$ can be represented as the unique sum of a pair of elements,
one vector from $W_1$ and the other vector from $W_2$ respectively.

**Theorem**: If for a vector space $V$, $W_1 + W_2 = V$ and $$W_1 \cap W_2 = \{\phi\}$$, then $V$ is a direct sum of $W_1$ and $W_2$, and vice versa.

**Proof**:  
**Backward Implication**:
Let $V$ be the direct sum of $W_1$ and $W_2$, then it naturally follows that $V = W_1 + W_2$.

For the second condition, since the intersection of two vector subspaces also yields a vector subspace,  
$W_1 \cap W_2$ is guaranteed to contain the vector additive identity, $\phi$.  
Let us now assume that some other element $\alpha$ belongs to both $W_1$ and $W_2$.  
Then we have:  
$\alpha + \phi$ where $\alpha \in W_1$ and $\phi \in W_2$  
and $\phi + \alpha$ where $\phi \in W_1$ and $\alpha \in W_2$  
Clearly we have represented the same vector, $\alpha$ in the form of two different sums taking one vector from each subspace, so $V$ cannot be the direct sum of $W_1$ and $W_2$.  
This poses a contradiction, and thus no element other than $\phi$ can belong to both $W_1$ and $W_2$.  
Thus, $$W_1 \cap W_2 = \{\phi\}$$.

**Forward Implication**:
Given that $W_1 + W_2 = V$ and $$W_1 \cap W_2 = \{\phi\}$$,
let us assume that there exist pairs $\alpha, \alpha\prime \in W_1$ and $\beta, \beta\prime \in W_2$, such that
$\alpha \neq \alpha\prime$, $\beta \neq \beta\prime$, and
<div>
$$
\begin{align}
	\alpha + \beta &= \alpha\prime + \beta\prime \\
	\alpha - \alpha\prime &= \beta\prime - \beta \\
\end{align}
$$
</div>

By the property of closure, we can say that $\alpha - \alpha\prime \in W_1$, $\beta\prime - \beta \in W_2$.
Since they are equal, they represent an element present in **both** $W_1$ and $W_2$,
but we know there is only one element that the two have in common, i.e. $\phi$.  
Thus we can say that $\alpha - \alpha\prime = \phi = \beta\prime - \beta$  
which in turn tells us that $\alpha = \alpha\prime, \beta = \beta\prime$.

This poses a contradiction, and thus we can conclude that there must be no such pairs of elements.
Finally, this means that $V$ must be a direct sum of the vector subspaces $W_1$ and $W_2$.

**Theorem**: **(Steinitz Replacement Theorem)**  
If $$\{ \bar\alpha_1, \bar\alpha_2, ..., \bar\alpha_n \}$$ is a basis of $V(F)$ and $\bar\beta$ is a non zero vector belonging to V, then $\bar\beta = \sum_{i = 1}^{n} c_i \bar\alpha_i$,
where $c_i \in F$ and not all $c_i$'s are zero.
If $c_j \neq 0$, then $$\{ \bar\alpha_1, \bar\alpha_2,..., \bar\alpha_{j-1}, \bar\beta, \bar\alpha_{j+1}, ..., \bar\alpha_n \}$$] is a basis of $V(F)$ 

**Proof**:
Let $c_j$ be the non zero, then we have:  
<div>
$$
\begin{align}
	\bar\beta &= c_1 \bar\alpha_1 + c_2 \bar\alpha_2 + ... + c_{j-1} \bar\alpha_{j-1} + c_j \bar\alpha_j + c_{j+1} \bar\alpha_{j+1} + ... +  c_n \bar\alpha_n \\
	c_j \bar\alpha_j &= \bar\beta - (c_1 \bar\alpha_1 + c_2 \bar\alpha_2 + ... + c_{j-1} \bar\alpha_{j-1} + c_{j+1} \bar\alpha_{j+1} + ... +  c_n \bar\alpha_n) \\
	\bar\alpha_j &= c_j^{-1} \bar\beta - c_j^{-1} (c_1 \bar\alpha_1 + c_2 \bar\alpha_2 + ... + c_{j-1} \bar\alpha_{j-1} + c_{j+1} \bar\alpha_{j+1} + ... +  c_n \bar\alpha_n) \\

\end{align}
$$
</div>

We now need to prove that the set $W = \{\bar\alpha_1, \bar\alpha_2, ... , \bar\alpha_{j-1}, \bar\beta, \bar\alpha_{j+1}, ... , \bar\alpha_n\}$ is linearly independent.  

Let   

$$
\delta_1 \cdot \bar\alpha_1 + \delta_2 \cdot \bar\alpha_2 + … + \delta_{j-1} \cdot \bar\alpha_{j-1} + \delta_{j+1} \cdot \alpha_{j+1} + … + \delta_n \cdot \bar\alpha_n + \delta_j \cdot  \bar\beta = \bar\phi
$$
  
where $\delta_i \in F$   

Now, we replace $\bar\beta$ with the summation $\sum_{i=1}^n c_i \cdot \bar\alpha_i$ Note that this __includes__ $\bar\alpha_j$ as a term.  
Therefore, the whole expression can be written as:  
  
$$
\delta_1 \cdot \bar\alpha_1 + \delta_2 \cdot \bar\alpha_2 + … + \delta_{j-1} \cdot \bar\alpha_{j-1} + \delta_{j+1} \cdot \alpha_{j+1} + … + \delta_n \cdot \bar\alpha_n + \delta_j \cdot  \sum_{i=1}^n c_i \cdot \bar\alpha_i = \bar\phi
$$  


That can be re-written as   

$$
\sum_{i=1, i \not=j} ^ n (\delta_i + \delta_j  c_i) \cdot \bar\alpha_i + \delta_j c_j \bar\alpha_j = \bar\phi
$$

Since $\{\bar\alpha_1, \bar\alpha_2, … \bar\alpha_n \}$ is known to be independent, all the coefficients in the above expression must turn out to be $0$ and thus $\delta_i + \delta_j c_i = 0 \forall i \not= j$ and $\delta_j c_j = 0$ but we know $c_j \not= 0$ (from the original assumption) thus $\delta_j = 0$ and since $\delta_i + \delta_j c_i = 0 \forall i \not= j$ , we can say $\delta_i = 0$. Thus, a linear combination of vectors in $W$ being $\bar\phi$ implies that all the coefficients are $0$ and thus we can say that $W$ is linearly independent.  

Now, we need to prove that $W$ spans the entire space.  

Let $\bar\gamma$ be any vector in $V$ and since $\{\bar\alpha_1, \bar\alpha_2, … , \bar\alpha_n\}$ is a basis  
  
$$
\bar\gamma = \sum_{i=1} ^ n \mu_i \cdot \bar\alpha_i, \mu_i \in F \\

\Rightarrow \bar\gamma = \sum_{i=1, i\not=j} ^n \mu_i \cdot \bar\alpha_i + \mu_j \cdot \bar\alpha_j \\

$$


We have already seen that $\bar\alpha_j$ can be represented as a linear combination of the vectors of $W$ i.e. all $\bar\alpha_i$ with $i \not=j$  and $\bar\beta$ 

thus we make the following substitution
$\bar\alpha_j = c_j^{-1} \bar\beta - c_j^{-1} (c_1 \bar\alpha_1 + c_2 \bar\alpha_2 + ... + c_{j-1} \bar\alpha_{j-1} + c_{j+1} \bar\alpha_{j+1} + ... +  c_n \bar\alpha_n)$ 

and we get

$$
\bar\gamma = \sum_{i=1, i\not=j}^n \mu_i \cdot \bar\alpha_i + \mu_j \cdot (c_j^{-1} \bar\beta - c_j^{-1} (c_1 \bar\alpha_1 + c_2 \bar\alpha_2 + ... + c_{j-1} \bar\alpha_{j-1} + c_{j+1} \bar\alpha_{j+1} + ... +  c_n \bar\alpha_n))

$$

So after simplifying we'll get the $\bar\gamma$ has been represented as a linear combination of all vectors in $W$ and thus $\bar\gamma \in L(W)$ and since $\bar\gamma$ was an arbitrary vector in the vector space, we have $V(F) \subseteq L(W)$ and since $L(W) \subseteq V(F)$ we can say that $L(W) = V(F)$  

Thus we have proven that $W$ is independent and spans the entire vector space, it is therefore a basis of the vector space.





**Theorem**: In a Vector space $V(F)$ with the basis set $B = \{ \bar\alpha_1, \bar\alpha_2, …, \bar\alpha_n \}$ every vector $\bar \gamma \in V(F)$ is  __uniquely__ expressible in a linear combination of vectors in $B$. 

__Proof__: 
Since $B$ is a basis set of $V(F)$  
Consider an arbitrary vector $\bar\gamma \in V(F)$  
We will prove the theorem by contradiction therefore we assume that $\bar\gamma$ can be expressed in two different linear combinations of $B$ i.e.

$$
\bar\gamma = a_1 \cdot \bar\alpha_1 + a_2 \cdot \bar\alpha_2 + ... + a_n \bar\alpha_n \\
\bar\gamma = b_1 \cdot \bar\alpha_1 + b_2 \cdot \bar \alpha_2 + ... + b_n \bar\alpha_n
$$
  
where $a_1, … a_n , b_1, … b_n \in F$   
and $(a_1, a_2, … a_n) \not= (b_1, b_2, … b_n)$   
Now we subtract the second equation from the first to get

$$
\bar\phi = (a_1 - b_1) \cdot \bar\alpha_1 + (a_2 - b_2) \cdot \bar\alpha_2 + ... + (a_n - b_n) \cdot \bar\alpha_n
$$

Notice that the RHS of the above equation is a linear combination of all the vectors in $B$ , which we know to be a basis set and therefore we know it to be linearly independent. Linear independence dictates that the only way for a linear combination leads to $\bar\phi$ is when all the coeffecients are $0$ i.e. if $a_i = b_i \forall i \text{ such that } 1\leq i\leq n$ which we __assumed to be untrue__ therefore _we have a contradiction_

Hence proved by contradiction. 
