---
title: Linear Algebra Lecture 17
date: 2021-04-01
author: Pratyaksh Gautam
code: ma2.101
number: 17
---
## Eigenvectors and Eigenvalues
$v \neq 0$ is said to be an **eigenvector** of $M$ iff there exists $\lambda \neq 0 \in F$, such that
$$M \cdot v = \lambda \cdot v$$
and $\lambda$ is the eigenvalue of $v$.

Also note, that if we have $w = \lambda \cdot v$ then  
$$
\begin{align}
	M \cdot w &= (M \lambda) \cdot v \\
			&= (\lambda M) \cdot v \\
			&= \lambda (M \cdot v) \\
			&= \lambda \lambda \cdot v \\
			&= \lambda^2 \cdot v \\
\end{align}
$$

Thus, $w$ is also an eigenvector.  
Similarly, we can see that $M^t \cdot v = \lambda^t \cdot v$.

### Finding eigenvectors and eigenvalues
Given a linear transform $M$, let us suppose there exists some eigenvector $v$.  
Then,
$$\begin{align}
	M \cdot v &= \lambda \cdot v \\
\implies M \cdot v - \lambda I_n \cdot v &= 0 \\
\implies (M - \lambda I_n ) \cdot v &= 0 \\
\implies (M - \lambda I_n ) \cdot v &= 0 \\
\end{align}
$$

So this means that the vector $v$ belongs to the null space of the transformation $M - \lambda I_n$.  
However note that we explicitly took $v$ to be a non-zero vector, so in addition to the trivial element $\phi$ in the kernel,
we have this additional element $v$, so the transformation cannot be one-one anymore.  
This implies that the transform cannot be bijective, and thus the matrix associated with it must be singular.

$$
\implies det(M - \lambda I_n) = 0 \\
$$

Thus, we are left with a polynomial in $\lambda$, of degree $n$ (the dimension of the transform) at most.
Upon solving this for it's roots, which may be at most $n$ in number, we get the possible values of $\lambda$, i.e the possible eigenvalues.

Now that we have obtained the possible eigenvalues for the transform, we can substitute it into
$$M \cdot v = \lambda \cdot v$$
giving us a set of $n$ linear equations, for the $n$ unknown components of $v$, thus we have a solvable system of equations for $v$.  
In this manner, we can find the corresponding eigenvectors for each eigenvalue.

<!-- TODO \lambda_i 's form the elements in a diagonal matrix, there standard basis form the eigenvectors -->
