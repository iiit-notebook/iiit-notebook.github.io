---
title: Linear Algebra Lecture 10
date: 2021-03-11
author: Abhinav S Menon
code: ma2.101
number: 10
---
## System of Linear Equations
A linear equation in the $n$ variables $x_1, x_2, ..., x_n$ is an equation of the form $a_1x_1 + a2x2 + \cdots + a_nx_n = b$, where the coefficients $a_i$ and the constant term $b$ are constant scalars.  
A solution of a linear equation is a vector $(s_1, s_2, ..., s_n)$ such that the substitution $x_i = s_i$ for all $0 < i \leq n$ satisfies the equation.  
A system of linear equations is a finite set of linear equations in the same variables. A solution of a system of linear equations is a vector which is a solution for each equation in the system. The solution set of a system of linear equations is the set of all solutions.  
A system of linear equations is consistent if it has at least one solution, *e.g.* $x + y = 1, x - y = 3$.  
A system of linear equations is inconsistent if it has no solutions, *e.g.* $x + y = 1, x + y = 3$.  

We note that solving a system of linear equations is almost trivial if
    (i) there is some equation containing only one variable, and
    (ii) each equation consists of all the variables of another one, plus one more.  
For example, to solve the system

$$x + y + z = 9,$$
$$3y - 4z = 4,$$
$$5z = 10,$$

we need only find $z = 2$ from the last equation, and substitute it into the second equation to directly obtain $y = 3$, and similarly find $x = 4$. This process is called back-substitution.  
The rest of the lecture is concerned with reducing any given system of equations to this form – this is called Gaussian Elimination. We begin by defining two helpful matrices.

## Coefficient Matrix and Augmented Matrix
The coefficient matrix of a system of linear equations is simply the matrix whose rows consist of lists of coefficients of each equation. For example, consider the system  

$$x + y + z = 9,$$
$$2x - 4y + z = -4,$$
$$x - y = -1.$$

The coefficient matrix for this system is $$\begin{bmatrix} 1 & 1 & 1 \\ 2 & -4 & 1 \\ 1 & -1 & 0 \end{bmatrix}.$$  
The augmented matrix just has another column to the right for the constant terms, *i.e.*, $$\begin{bmatrix} 1 & 1 & 1 & 9 \\ 2 & -4 & 1 & -4 \\ 1 & -1 & 0 & -1 \end{bmatrix}.$$  

Now, we note that given a system of linear equations, doing any of the following operations:  
    (i) changing the order of two equations,  
    (ii) multiplying an equation by a constant, and  
    (iii) adding one equation to a constant multiple of another,  
does not change the solution set. Therefore we can carry out the same operations on the augmented matrix or coefficient matrix without affecting the system; *i.e.*, we can  
    (i) interchange two rows,  
    (ii) multiply any row by a constant, and  
    (iii) add a constant multiple of one row to another.  
Now, we will use these operations to convert the system into a form that is easy to solve, like we saw in the previous section.  
Let us now formally define what form we would like the system to be in.  

## Row Echelon Form

A matrix is said to be in *row echelon form* if  
    (a) any zero rows are at the bottom, and  
    (b) in each row, the first nonzero element is to the left of the first nonzero element in the row immediately below.  
We can see that the augmented matrix of the system in the previous section, that is $$\begin{bmatrix} 1 & 1 & 1 & \\ 0 & 3 & -4 & 4 \\ 0 & 0 & 5 & 10 \end{bmatrix}$$ is in this form.  
In general, once we convert the matrix to row echelon form, we change it back to a system of equations and solve it by back-substitution. _Row echelon form is not unique_.   

This is the form that we will reduce the augmented matrices to, using the above listed operations (called elementary row operations). We will now try to do this for the matrix in the beginning of the section, $$\begin{bmatrix} 1 & 1 & 1 & 9 \\ 2 & -4 & 1 & -4 \\ 1 & -1 & 0 & -1 \end{bmatrix}.$$  

First, we will try to make the first entries of the second and third rows zero. We can do this with the transformations $R_2 \to R_2 - 2R_1$ and $R_3 \to R_3 - R_1$. Thus, we get the matrix $$\begin{bmatrix} 1 & 1 & 1 & 9 \\ 0 & -6 & -1 & -22 \\ 0 & -2 & -1 & -10 \end{bmatrix}.$$  

Now, the first nonzero entry in the third row should be to the right of $-6$ in the second row, for it to be in row echelon form. We can achieve this by subtracting $\frac{1}{3}$ of $R_2$ from $R_3$ (note that this will not affect the position of the zeroes because $0 - \frac{1}{3} \cdot 0 = 0 - 0 = 0$. This is why we are not using $R_1$ in this step; it would mess up the zeroes on the left).  
However, to avoid screwing around with fractions and negative numbers too much, we can multiply $R_3$ by $-3$ first. This gives us $$\begin{bmatrix} 1 & 1 & 1 & 9 \\ 0 & -6 & -1 & -22 \\ 0 & 6 & 3 & 30 \end{bmatrix}.$$  

Now we simply add $R_3 \to R_3 + R_2$ to make its second entry zero: $$\begin{bmatrix} 1 & 1 & 1 & 9 \\ 0 & -6 & -1 & -22 \\ 0 & 0 & 2 & 8 \end{bmatrix}.$$

This is a row echelon form of the given matrix. The corresponding linear equations are

$$x + y + z = 9,$$
$$-6y - z = -22,$$
$$2z = 8.$$


We solve these using back-substitution to obtain the solution $x = 2, y = 3, z = 4$.  

In summary, to solve a given system of equations using Gaussian elimination,  
1. write the corresponding augmented matrix,  
2. convert the matrix to row echelon form,  
3. write the corresponding linear equations, and  
4. solve using back-substitution.  


