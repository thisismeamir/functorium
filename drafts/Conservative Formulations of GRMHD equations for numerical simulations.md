---
sticker: lucide//newspaper
---
# Conservative Formulations
The equations of [[Relativistic Hydrodynamics]], and [[General Relativistic Magnetohydrodynamics]] can be written in the generic first-order-in-time form:
$$
\partial_t U + A\cdot\nabla U = S
$$
and the system above is said to be hyperbolic if the matrix of coefficients $A$ is diagonalisable with a set of real eigenvalues, or eigenspeeds, $\lambda_1, \lambda_2, \dots, \lambda_N$, and a corresponding set of $N$ linearly independent right eigenvectors $R^{(1)}, \dots, R^{(m)}$, such that:
$$
AR^{(i)} = \lambda_i R^{(i)},
$$
and also:
$$
\Lambda :=R^{-1}A R = \text{diag}(\lambda_1, \dots, \lambda_N)
$$
is the diagonal matrix of eigenvalues and $R$ the matrix of right eigenvectors. ==The most important property of *hyperbolic equations* is that they are well-posed and therefore, suitable for numerical solutions==. Moreover, if the matrix $A$ is the Jacobian of a flux vector $F(U)$ with respect to the state vector $U$, namely if:
$$
A(U) := \frac{\partial F}{\partial U},
$$
then the homogeneous version of the system can be written in **conservative form** as:
$$
\partial_t U + \nabla F(U) = 0
$$
Here $U$ is called the vector of *conserved variables*. 

Now we can discuss two theorems underlining the importance of a conservative formulation they loosely speaking state:
1. Conservative Numerical schemes -- that is, a numerical scheme based on the conservative formulation of the equations -- if convergent, do converge to the weak solution of the problem.
2. Non-Conservative Numerical schemes, schemes in which the equations are not written in the conservative form, do not converge to the correct solution if a shock wave is present in the flow. 
In other words the two theorems above state that if a conservative formulation is used, then we are guaranteed that the numerical solution will converge to the correct one, while if a conservative formulation is not used, we are guaranteed to converge to the incorrect solution in the likely event in which the flow develops a discontinuity.