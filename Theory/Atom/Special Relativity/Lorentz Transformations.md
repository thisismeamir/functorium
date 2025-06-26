---
sticker: lucide//atom
---
# Lorentz Transformations

## Derivation Using $k$-calculus

One can derive Lorentz Transformations by using the $k$-calculus method. Let us assume an event $P$ having coordinates $(t,x)$ measured by $A$ and $(t',x')$ measured by $B$. Assume that $A$ and $B$ both set their clocks to zero when they meet.

Let $A$ send out a signal at time $t_1$. Since, according to radar method $t=\frac12(t_1+t_2)$, and $x=\frac12(t_2-t_1)$ where $t_2$ is the time $A$ received the reflected signal. We can solve them for $t_1$ and $t_2$ to get:

$$
\begin{align}
t_1 &= t-x\\
t_2 &= t+x
\end{align}
$$

Using $k$-factor method we know that:

$$
\begin{align}
t_1' &= kt_1\\
t_2' &= \frac1k t_2
\end{align}
$$

Which we also have the following for:

$$
\begin{align}
t_1' &= t'-x'\\
t_2' &= t'+x'
\end{align}
$$
setting right hand sides equal to one another we find:

$$
\begin{align}
t'-x' &= k(t-x)\\
t'+x' &=\frac1k (t+x)
\end{align}
$$
solving these two equations for $t'$ and $x'$  

$$
\begin{align}
2t' &= k(t-x) + \frac1k (t +x) \\
&= t (k + \frac1k) + x(\frac1k -k)\\
&=\left(\frac{k^2+1}{k}\right) t + \left(\frac{1-k^2}{k}\right)x\\
&=\frac{\left(1+k^2\right)t + \left(1-k^2\right)x}{k}
\end{align}
$$
similarly
$$
\begin{align}
2x' &=  \left(\frac{1- k^2}{k}\right)t + \left(\frac{1+k^2}{k}\right)x\\
&=\frac{\left(1-k^2\right)t + \left(1+k^2\right)x}{k}
\end{align}
$$
more simply:

$$
2t' = \frac1k\left(
t+x +k^2\left(t-x\right)
\right)
$$
and 

$$
2x' =\frac1k (t+x+k^2(x-t))
$$
Now from the [[K-Calculus]]we know that:

$$
k = \sqrt{\frac{1+v}{1-v}}
$$
substituting this into out equations we get:

$$
\begin{align}
t' &= \frac{1}{2\left(\frac{1+v}{1-v}\right)^{\frac12}}\left[
\frac{1+v}{1-v}\left(t-x\right) + \frac{1-v}{1-v}\left(t+x\right)
\right]\\
&= \frac{1}{(1-v^2)^{1/2}}(t-vx)
\end{align}
$$
and

$$
\begin{align}
x' &= \frac{1}{2\left(\frac{1+v}{1-v}\right)^{\frac12}}\left[
\frac{1+v}{1-v}\left(x-t\right) + \frac{1-v}{1-v}\left(t+x\right)
\right]\\
&= \frac{1}{(1-v^2)^{1/2}}(x-vt)
\end{align}
$$

This would give us the final **special Lorentz transformation**:

> [!IMPORTANT] Special Loretntz Transformation
> $$
> \boxed{
> \begin{matrix}
> t'=\frac{t-vx}{(1-v^2)^{1/2}} & x' =\frac{x-vt}{(1-v^2)^{1/2}}
> \end{matrix}
> }
> $$
> This is also referred to as a **boost in the $x$-direction with speed $v$**, since it takes one from $A$'s coordinates to $B$'s coordinates, and $B$ is moving away from $A$, with speed $v$.

Some simple algebra reveals the result:

$$
t'^2 -x'^2 = t^2-x^2
$$
Showing that this quantity is invariant under a special Lorentz transformation or boost.

## Morphisms
- Depends on
- Is included in
- Refined by
- Is Equivalence to

## Tags
#atom #theory 