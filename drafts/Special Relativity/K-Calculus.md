---
sticker: lucide//atom
---
# K-Calculus
## Overview
We would use [[K-Factor]] here to develop the K Calculus.

## Development

Here we calculate some scenarios that would give us a clear picture of K-Calculus.

### **Relative Speed of Two Inertial Observers**
Consider that $A$ and $B$ are two inertial observers, who had synchronized their clocks to zero when they crosses at event $O$. After a time $T$, $A$ sends a signal to $B$, which is reflected back at event $P$. From  $B$'s point of view, a light signal is sent to $A$ after a time lapse of $kT$ by $B$'s clock. It follows from the definition of the $k$-factor that $A$ receives this signal after a time lapse of $k(kT)$. Therefore:

$$
\begin{align}
t_1 &= T \\
t_2 &= k^2 T
\end{align}
$$
and via the definition in [[K-Factor]]we can find the coordinates of $P$ according to $A$ as:
$$
(t,x)_P = \frac T2\left(
k^2+1, k^2-1
\right)
$$

But $P$ was just an event on the [[Worldline]] of $B$, therefore, as $T$ increases, $P$ is the line on which $B$ is moving relative to $A$. From this one can calculate the velocity of $B$ with respect to $A$'s point of view:

$$
v = \frac{x}{t} = \frac{k^2-1}{k^2+1}
$$
Solving this for $k$ we find:

$$
\begin{align}
(k^2+1)v &= (k^2-1)\\
k^2(v-1) &= -(v+1)\\
\end{align}
$$
which leads to:

$$
\boxed{
k = \left(\frac{1+v}{1-v}\right)^{\frac12}
}
$$
This formula is just the usual [[Relativistic Doppler Shift]]
- If $B$ is moving away from $A$ then $k>1$, which represents a [[Redshift | redshift]].
- If $B$ is approaching $A$ then, $k<1$ which represents a [[Blueshift | blueshift]]


> [!IMPORTANT] Transformation  $v\rightarrow -v$
> Note that trasformation $v\rightarrow-v$ corresponds to interchanging the roles of $A$ and $B$ and results in $k\rightarrow \frac1k$

### **Composition Law for Velocities**
Now assume that there are three observers moving the different velocities relative to each other, $A$, $B$, and $C$.

Again $A$ would start sending signals within $T$ intervals. By the previous deduction we know that the signals would reach $B$ at $k_{AB}$. 

Now imagine that $B$ starts sending signals each time it gets one from $A$ but instead of re-sending signals to $A$, it will send them to $C$. Therefore, $C$ receives signals in $k_{BC}k_{AB}T$. It is obvious that:

$$
k_{AC} = k_{BC}k_{AB} 
$$
Now re-writing this in terms of the relative velocities we get the composition law for velocities:


> [!IMPORTANT] Composition Law for Velocities
> $$
> v_{AC}= \frac{v_{AB} + v_{BC}}{1+v_{AB}v_{BC}}
> $$

Although the composition law for velocities is not simple, the one for $k$-factors is and, in special relativity, it is the $k$-factors which are directly measurable quantities. Note also that , formally, if we substitute $v_{BC}=1$, representing the speed of a light signal relative to $B$, then the resulting speed of the light signal relative to $A$ is also $1$.


> [!DANGER] Note
> From the composition law, we can show that, if we add two speeds less than the speed of light, then we again obtain a speed less than the speed of light. This does not mean, as is sometimes stated, that nothing can move faster than the speed of light in special relativity, but rather that the speed of light is a border which can not be crossed or even reached. More on this [[Three Classes of Particles in Special Relativity]]

## Morphisms
- Depends on
- Is included in
- Refined by
- Is Equivalence to

## Tags
#atom #theory 