---
sticker: lucide//atom
---
# Rotation Matrix With and Without the Constancy of the Speed of Light - Gifted Amateur - Page 13 - Example 1.1

![[Pasted image 20250811121401.png]]
The two-dimensional $xy$ plane is shown in figure above. The point $(x,y)$ is at a distance defined:

$$
d = \sqrt{x^2 + y^2}
$$
from the origin. If we rotate the coordinates so that:
$$
\begin{align}
x&\rightarrow x' \\ 
y&\rightarrow y'
\end{align}
$$
we want this distance to be unchanged (invariant), so that:
$$
\boxed{x^2+y^2 = x'^2 + y'^2}
$$
A linear transformation that accomplishes this is given by:
$$
\begin{pmatrix}x'\\ y'\end{pmatrix} = \begin{pmatrix}\cos\theta & \sin\theta \\-\sin\theta & \cos\theta\end{pmatrix} \begin{pmatrix}x \\ y\end{pmatrix}
$$
which works because $\sin^2\theta +\cos^2\theta =1$.


> [!DANGER] Note
> The matrix in this equation is known as a **rotation matrix**. 

If you ask what are the set of points which are equidistant from the origin then, obviously, you will end up with a cocentric circles centered on the origin. the shortest distance between the origin and a point $(x,y)$ is, of course, a straight line and that straight line will intersect with all of those circles at right angles


---

 Let's see how to transform between two frames in spacetime. We shall deal with the $xt$ plane because time now is a coordinate itself. The point $(x,t)$ is now at an interval $\sqrt{-c^2t^2 + x^2}$ from the origin. The interval is somewhat like distance like in section above, but the minus sign in the definition of [[Minkowski Metric (Flat Spacetime)]]will change things.

The analogue of rotating the coordinates, mapping:
$$
\begin{align}
x&\rightarrow x'\\
t&\rightarrow t'
\end{align}
$$

which preserves the squared interval is the linear transformation by:
$$
\begin{pmatrix}x' \\ ct'\end{pmatrix} = \begin{pmatrix}\cosh \theta & \sinh \theta \\ \sinh\theta & \cosh\theta\end{pmatrix}\begin{pmatrix}x \\ t\end{pmatrix}
$$
which works because $\cosh^2\theta - \sinh^2\theta = 1$.  This is known as [[Lorentz Transformations]]. If some $S'$ moves at the speed $v\equiv \beta c$ with respect to frame $S$, a particle located at a point in space which is stationary in $S$, is moving in $S'$ at speed $-v$. If we then set $x=0$ we have that $x' = ct\sinh\theta$ and $t'=t\cosh\theta$. But $\frac{x'}{t'} = -v$ so we deduce that $v = -c\tanh\theta$, This means that with the definition $\gamma = (1-\beta^2)^{-1/2}$ we have
$$
\begin{pmatrix}x' \\ ct'\end{pmatrix} = \begin{pmatrix}\gamma & -\gamma\beta \\ -\gamma\beta & \gamma\end{pmatrix}\begin{pmatrix}x \\ t\end{pmatrix}
$$
