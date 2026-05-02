# 1

We start with the most universal identity we have, namely, the four-velocity is known mathematically to satisfy
$$
g_{\mu \nu} \frac{\mathrm{d}x^{\mu}}{\mathrm{d}\tau} \frac{\mathrm{d}x^{\nu}}{\mathrm{d}\tau} = -1. 
$$

We want to therefore calculate a constrains on the radial velocity in the Schwarzschild metric;

$$
\mathrm{d}s^{2} = -\left( 1- \frac{2GM}{r} \right) \mathrm{d}t^{2} +\left( 1- \frac{2GM}{r} \right)^{-1}\mathrm{d}r^{2} +r^{2} \mathrm{d}\Omega^{2}.
$$

Using this metric we construct the timelike normalization condition as:

$$
-\left( 1- \frac{2GM}{r} \right) \left( \frac{\mathrm{d}t}{\mathrm{d}\tau} \right)^{2}  +\left( 1- \frac{2GM}{r} \right)^{-1} \left( \frac{\mathrm{d}r}{\mathrm{d}\tau} \right)^{2}  +r^{2} \left( \frac{\mathrm{d}\Omega}{\mathrm{d}\tau} \right)^{2}  =-1.
$$
For easier following we introduce a notation choice and a function definition:

$$
\begin{align}
\dot{x}^{2} &= \left( \frac{\mathrm{d}x}{\mathrm{d}\tau} \right)^{2}  \\
f(r) &=\left( 1- \frac{2GM}{r} \right) 
\end{align}
$$

Thus rewriting the equation:

$$
-f(r) \dot{t}^{2} +f^{-1}(r) \dot{r}^{2} +r^{2} \dot{\Omega}^{2}=-1
$$
Inside the horizon a key change happens in the metric, because of the function $f(r)$, the signs of the radial component and the time component would flip. Meaning that $r$ would be timelike and $t$ would be spacelike. Let's assume:

$$
f(r) =- \left| f \right| 
$$

Inside the horizon were $|f|$ is positive, the metric undergoes the following changes:

$$
\begin{align}
\text{Inside the horizon}  & \to & f(r) \dot{t}^{2} - f^{-1}(r) \dot{r}^{2} - r^{2} \dot{\Omega}^{2}=1 \\
\text{Assumption about the function} & \to & - |f| \dot{t}^{2} + |f|^{-1}\dot{r}^{2}-r^{2} \dot{\Omega}^{2}=1
\end{align}
$$
We solve for $\dot{r}$,

$$
\dot{r}^{2} = |f| \left[ 1+|f| \dot{t}^{2} +r^{2} \dot{\Omega}^{2} \right] 
$$
It is obvious that the term inside brackets is a positive term since $\dot{t}^{2}\geq 0$, and $\dot{\Omega}^{2} \geq 0$ therefore, inside the brackets would actually be greater equal to $1$. Therefore,

$$
\dot{r}^{2}=|f| \left[ 1 + |f| \dot{t}^{2} + r^{2} \dot{\Omega}^{2} \right] \geq |f| \cdot 1 
$$
Leading to the conclusion:

$$
\dot{r}^{2} \geq |f|
$$
Simplifying to:

$$
\left| \frac{\mathrm{d}r}{\mathrm{d}\tau} \right| = \sqrt{ \frac{2GM}{r}-1 }
$$
QED.


---

The Schwarzschild metric has a Killing vector $\xi^{\mu}=(1,0,0,0)$. The conserved quantity along a geodesic is:

$$
E =-g_{\mu n}
$$