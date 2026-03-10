
# The Core Idea

Manifolds are like curves and surfaces. Every manifold comes with a special non-negative integer, called the dimension of the manifold (least number of parameters needed to specify a point on the manifold). 

An $n$-dimensional manifold is an object modeled locally in $\mathbb R^n$; Meaning that it takes exactly $n$ parameters to specify a point at least if we do not stray too far from a given starting point.

> A physicist would say that an $n$-dimensional manifold is an object with $n$ degrees of freedom.


## Some Basic Examples

**One Dimensional Manifolds** are curves and lines. The easiest example would be the real line. Other examples can be a curve [[Embedding|embedded]]in $n$ dimensional space by a single parameter.

![[../../attachments/Pasted image 20260118122210.png]]

In each of these examples, a point can be unambiguously specified by a single real number. For example, a point on the real line *is* a real number. We might identify a point on the circle by its angle, a point on a graph by its $x$-coordinate, and a point on a parameterized curve by its parameter $\lambda$.

“Note that although a parameter value determines a point, different parameter values may correspond to the same point, as in the case of angles on the circle. But in every case, as long as we stay close to some initial point, there is a one-to-one correspondence between nearby real numbers and nearby points on the line or curve.”

**ُTwo Dimensional Manifolds** are surfaces. The most common examples are planes and spheres. 

The key feature of these examples is that an $n$-dimensional manifold "look like" $\mathbb R^n$ locally. To make sense of it, we say that two subsets of Euclidean spaces $U\subseteq \mathbb R^k$ and $V\subseteq \mathbb R^n$ are *topologically equivalent* or *homeomorphic* if there exists a one-to-one correspondence $\varphi: U\rightarrow V$ such that both $\varphi$ and its inverse are continuous maps. This correspondence is called [[Homeomorphism]]. Describing manifolds, there's a homeomorphism between the manifold and $\mathbb R^n$ *locally*.

