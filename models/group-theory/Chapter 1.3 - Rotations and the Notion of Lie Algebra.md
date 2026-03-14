# Rotations and the Notion of Lie Algebra
---
**Table of Content**
```toc
    style: number
    min_depth: 1
    max_depth: 6
```
---
## Cartesian Coordinates and Trigonometry
As we know in rotation, we either rotate the body or we rotate the axis. Here we consistently rotate the axis of coordinates (namely the observer)

![[Pasted image 20211113093432.png]]

From simple trigonometry we can say that each coordinates have different values to represent $P$ but these values are connected to each other with:
$$
\begin{cases}
x' = \cos\theta x+\sin\theta y \\
y' = -\sin\theta x +\cos\theta y
\end{cases}
$$
with this relation we easily can see that the distance between $\vec O$ and $\vec P$ are same in both coordinates:
$$
\sqrt{x'^2+y'^2} = \sqrt{x^2+y^2}
$$
also we know how to write these in matrix form:
$$
\begin{pmatrix}
\cos\theta &\sin\theta \\
-\sin\theta & \cos\theta
\end{pmatrix} 
\begin{pmatrix} x \\ y \end{pmatrix}
=\begin{pmatrix} x' \\ y' \end{pmatrix}
$$

## Invariance Under Linear Transformation
Assuming two vectors $\vec p =\begin{pmatrix} p_1 \\ p_2 \end{pmatrix}$ and$\vec q =\begin{pmatrix} q_1 \\ q_2\end{pmatrix}$ . The dot product of two vectors is defined as:
$$
\vec  p^T\cdot \vec q = p_1q_1+p_2q_2
$$
where $\vec p^T$ is the transpose of $\vec p$.
with this definition using the Pythagoras theorem we could find the length (magnitude) if a vector:
$$
\vec p^T \cdot \vec p = |\vec p|^2 \rightarrow 
|\vec p| =\sqrt{p_1^2+p_2^2} 
$$
we can see that in this definition of dot product, in a coordinate system $A$ and $B$ which are different by a rotation, the magnitude would be the same. *just use the magnitude definition and it will be easy to prove.*
**Because rotation leaves the dot product invariant, between any two vectors**.

From this fact we can define one property of rotational matrices:
$$
R^TR=I
$$
Matrices that satisfies this are called orthogonal, these **Orthogonal matrices** generate the group $O(2)$.

## Reflections
We know that the determinant of a product of matrices is equal to the product of the determinants: $\det(M_1M_2) = \det(M_1)\det(M_2)$ .
and that the determinant of the transpose of a matrix is the same as the determinant of that matrix: $\det(M^T)=\det(M)$. now if we apply these two equations we can see that for $R^TR=I$:
$$
\det(R^TR) =\det(R^t)\det(R) = \det(R)^2 = det(I) = 1
$$
therefore:
$$\det(R) = \pm1$$
This shows that the Orthogonal matrices group $O(2)$ has two types of matrices one which has $\det(R) = 1$ which are ordinary rotations and one which has $\det(R) = -1$ which are reflection matrices such as:
$$
P = \begin{pmatrix} 1&0\\0&-1\end{pmatrix}
$$

> Matrices with unit determinant are called special

**We define rotation as a matrix that is orthogonal and special** Therefore the rotation group of the plane consists of the set of all special orthogonal 2-by-2 matrices and is known as $SO(2)$.

## Act a Little Bit at a Time
The Norwegian physicist Marius Sophus Lie (1842–1899) had the almost childishly obvious but brilliant idea that to rotate through, say, 29◦, you could just as well rotate through a zillionth of a degree and repeat the process 29 zillion times.
So, consider a really small angle $\theta$:
$$
R(\theta) \approx I+A
$$
\
an infinitesimal rotation is like no rotation at all so it is nearly equal to $I$ the identity matrix plus another matrices of order $\theta$, $\theta^2$,... but since $\theta^n$  with $n>1$ are so small we can neglect them and work with the presented equation.
\
now this new infinitesimal rotation definition must be orthogonal:
$$
R^TR\approx (I+A^T)(I+A) = I +A^T+A = I
$$
This implies that $A$ has to be antisymmetric mean that:
$$
A^T= -A
$$
But luckily there is basically only one 2-by-2 antisymmetric matrix:
$$
\jmath \equiv \begin{pmatrix} 0&1\\-1&0\end{pmatrix}
$$
therefore $A$ must be in the form:
$$
A = \theta\jmath
$$
for some real number $\theta$.

\
Then we have:
$$
R=I+\theta\jmath +O(\theta^2) =
\begin{pmatrix} 1&\theta\\-\theta &1\end{pmatrix} + O(\theta^2)
$$
The antisymmetric matrix $\jmath$ is known as the generator of the rotation group.
\
therefore we can have for a big angle $\theta$.
$$
R(\theta)=\lim_{N\rightarrow\infty}\bigg(
R\big(
\frac{\theta}{N}
\big)
\bigg)^N = \lim_{N\rightarrow\infty}
\bigg(1+\frac{\theta\jmath}{N}\bigg)^N = e^{\theta\jmath}
$$

## From the Plane to Higher-Dimensional Spaces
The reader who has wrestled with Euler angles in a mechanics course knows that the analog of (2) for 3-dimensional space is already quite a mess. In contrast, Lie’s approach allows us, as mentioned above, to immediately jump to $N$-dimensional Euclidean space, defined by specifying the distance squared between two nearby points as given by the obvious generalization of Pythagoras’s theorem:
$$
ds^2=\sum_{i=1}^N (dx^i)^2 
$$
Rotations are defined as linear transformations $\vec dx' = R\vec dx$ (with $R$ an $N$-by$N$ matrix) that leave $ds^2$  unchanged.
\
The preceding discussion allows us to write this condition as $R^TR = I$. As before, we want to eliminate reflection and to focus on rotations by imposing the additional condition $\det R = 1$. 
\
The set of $N$-by-$N$ matrices $R$ that satisfy these two conditions forms the simple orthogonal group $SO(N)$, which is just a fancy way of saying the rotation group in $N$-dimensional space.
\
 Let us first show that indeed $SO(N)$ is a group. The product of two rotations is a rotation: 
 $$
 (R_1R_2)^T(R_1R_2) =  (R_2^TR_1^T)(R_1R_2) = R_2^T(R_1^TR_1)R_2 = I
 $$
 and 
 $$
 \det(R_1R_2) = \det R_1 \det R_2 = 1
$$ 
\
Matrix multiplication is associative. The condition $\det R = 1$ guarantees the existence of the inverse.

## Lie in Higher Dimensions
The power of Lie now shines through when we want to work out rotations in higher dimensional spaces. All we have to do is satisfy the two conditions $R^TR = I$ and $\det R = 1$.
Lie shows that for the first condition we can easily solve it by considering:
$$
R\cong I +A
$$ 
Where $A = -A^T$ which means it is antisymmetric.
\
==That’s it. We could be in a zillion-dimensional space, but still, the rotation group is fixed by requiring $A$ to be antisymmetric.==
\
But it is very easy to write down all possible antisymmetric $N$-by-$N$ matrices! For $N = 2$, there is only one, namely, the $\jmath$ introduced earlier. For $N = 3$, there are basically three of them:
$$
\begin{matrix}
\jmath_x = \begin{pmatrix}
0&0&0\\
0&0&1\\
0&-1&0
\end{pmatrix},
&
\jmath_y = \begin{pmatrix}
0&0&-1\\
0&0&0\\
1&0&0
\end{pmatrix}
&
\jmath_z = \begin{pmatrix}
0&1&0\\
-1&0&0\\
0&0&0
\end{pmatrix}
\end{matrix}
$$
Any $3$-by-$3$ antisymmetric matrix can be written as $A = \theta_x\jmath_x+\theta_y\jmath_y+\theta_z\jmath_z$, with three real numbers $θ_x$ , $θ_y$, and $θ_z$. The three $3$-by-$3$ antisymmetric matrices $\jmath_x$,$\jmath_y$,$\jmath_z$ are known as generators. 
\
They generate rotations, but are of course not to be confused with rotations, which are by definition $3$-by-$3$ orthogonal matrices with determinant equal to $1$.
\
One upshot of this whole discussion is that any $3$-dimensional rotation (not necessarily infinitesimal) can be written as	
$$
R(\theta)=e^{\theta_x\jmath_x+\theta_y\jmath_y+\theta_z\jmath_z} = e^{\sum_i\theta_i\jmath_i}
$$
and is thus characterized by three real numbers $θ_x$ , $θ_y$ , and $θ_z$. As I said, those readers who have suffered through the rotation of a rigid body in a course on mechanics surely would appreciate the simplicity of studying the generators of infinitesimal rotations and then simply exponentiating them.
\
If you have studied quantum mechanics, you know that the generators $J$ of rotation studied here are related to angular momentum operators.
\
You would also know that in quantum mechanics observables are represented by hermitean operators or matrices. In contrast, in our discussion, the $\jmath$s come out naturally as real antisymmetric matrices and are thus antihermitean.
\
To make them hermitean, we multiply them by some multiples of the imaginary unit $i$. Thus, define 
$$J_x ≡−i\jmath_x,\ \ \ \ \ 
J_y ≡−i\jmath_y
, \ \ \ \ \  J_z ≡−i\jmath_z,$$ 
and write a general rotation as
$$
R(\theta) = e^{i\sum_k\theta_kJ_k} = e^{i\vec\theta\cdot\vec J}
$$
\
Any student of physics knows that many physical situations exhibit spherical symmetry, in which case the rotation group $SO(3)$ plays a central role.


---
## Lie Algebra
in general, rotations do not commute. Following Lie, we could try to capture this essence of group multiplication by focusing on infinitesimal rotations.
\
Let $R \simeq I + A$ be an infinitesimal rotation. For an arbitrary rotation $R'$, consider $RR'R^{−1} \simeq (I + A)R''(I − A) = R' + AR' − R'A$ (where we have consistently ignored terms of order A2). If rotations commute, then $RR'R^{−1}$ would be equal to $R'$. Thus, the extent to which this is not equal to $R'$ measures the lack of commutativity. 

\
Now, suppose $R'$ is also an infinitesimal rotation $R' \simeq I +B$. Then $RR'R−1 \simeq I +B +AB −BA$, which differs from $R'\simeq I + B$ by the matrix:
$$
[A,B] = AB-BA 
$$
which is called the commutator of $A$ and $B$.

For $SO(3)$ for example $A$ is a linear combination of the $J_i$s, which we shall call the generators of the Lie Algebra of $SO(3)$. Thus, we can write $A=i\sum_i\theta_iJ_i$ and similarly $B=i\theta_j\theta'_jJ_j$. Hence$[A,B] = i^2\sum_{ij}\theta_i\theta_j'[J_i,J_j]$ and so it suffices to calculate the commutators $[J_i,J_j]$ once and for all.
\
Recall that for two matrices $M_1$ and $M_2$, $(M_1M_2)^T = (M_2^TM_1^T)$. Transposition reverses the order. Thus, $([J_i,J_j])^T = -[J_i,J_j]$ in other words the commutator $[J_i,J_j]$ is itself as antisymmetric $3\times3$ matrix and this can be written as a linear combination of the $J_k$s:
$$
[J_i,J_j] = ic_{ijk}J_k
$$

The summation over $k$ is implied by the repeated index summation convention. The coefficients $c_ijk$ in the linear combination, with a factor of $i$ taken out explicitly, are real (convince yourself of this) numbers. Evidently, $c_{ijk} =−c_{jik}$.

We can therefore show that:
$$
\begin{equation}
\begin{split}
[J_x,J_y] = iJ_z
\\
[J_y,J_z] = iJ_x
\\
[J_z,J_x] = iJ_y
\end{split}
\end{equation}
$$
This can be summarized with:
$$[J_i,J_j] = i\epsilon_{ijk}J_k$$

Lie’s great insight is that the preceding discussion holds for any group whose elements $g(θ_1, θ_2, ...)$ are labeled by a set of continuous parameters such that $g(0, 0, ...)$ is the identity $I$.
For these groups, now known as Lie groups, this is what you do in four easy steps:
\ 
1. Expand the group elements around the identity by letting the continuous parameters go to zero: $g\simeq I+A$.
2. Write $A = i\sum_a  θ_aT_a$ as a linear combination of the generators $T_a$ as determined by the nature of the group. 
3. Pick two group elements near the identity: $g_1 \simeq I + A$ and $g_2\simeq I+B$. Then $g_1g_2g_1^{-1}\simeq I+B+[A, I+B]\simeq I+B+[A,B]$. The commutator $[A, B]$ captures the essence of the group near the identity.
4. As in step $2$, we can write $B = i\sum_b \theta'_bT_b$as a linear combination of the generators $T_b$. Similarly, we can write $[A, B]$ as a linear combination of the generators $T_c$. (We know this because, for $g_1$ and $g_2$ near the identity, $g_1g_2g_1^{−1}$ 1 is also near the identity.) Plugging in, we then arrive at the analog of ($[J_i,J_j] = ic_{ijk}J_k$) for any continuous group, namely, the commutation relations

	$$[T_a,T_b] = if_{abc}T_c$$
	**==The commutator between any two generators can be written as a linear combination of the generators.==**
	
---
The commutation relations between the generators define a Lie algebra, with $f_{abc}$ referred to as the **structure constants** of the algebra. 
\
The structure constants determine the Lie algebra, which essentially determines the Lie group. This brief introduction to Lie algebra at this stage is necessarily somewhat vague, but we will go into more details soon enough. The key idea is that we can go a long way toward understanding a continuous group by studying its Lie algebra. Note that, while a Lie group is characterized by multiplication, its Lie algebra is characterized by commutation. 
\
> Confusio said, “When I first studied group theory, I did not clearly distinguish between Lie group and Lie algebra. That they allow totally different operations did not sink in. I was multiplying the $J_i$s together and couldn’t make sense of what I got.” Absolutely, it is crucial to keep in mind that Lie group and Lie algebra are mathematically rather different structures. 
   \
   In a group, you multiply (or if one wants to pick nits, compose) two elements together to get another element. In the corresponding algebra (assuming of course that the group is continuous), you take two elements, and you commute them to get another element of the algebra. (Again, to keep the nitpickers at bay, it may be perhaps better to say two members of the algebra, since we have spoken often of group elements.)
   
  
  
The rotation group offers a good example. The members J of its algebra are real antisymmetric matrices,∗ but if you multiply two real antisymmetric matrices together, you certainly do not get a real antisymmetric matrix. The algebra does not close under multiplication, only under commutation. Perhaps one confusing point for the beginner is that to calculate the commutator, one has to, in an intermediate step, multiply two real antisymmetric matrices together.
Speaking somewhat colloquially, one has to first get out of the algebra before one can get back in.