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
E =-g_{\mu \nu}\xi^{\mu}\dot{x}^{\nu}= -g_{tt} \dot{t} = \left( 1 - \frac{2GM}{r} \right) \dot{t}.
$$
Which is the energy. We set the angular velocity component to zero because of the symmetry of our metric, thus we are with the norm condition below:

$$
-f \dot{t}^{2} +f^{-1} \dot{r}^{2}=-1;
$$
Substituting the conserved quantity (first solving for the time velocity component and then replacing it to the norm) we get

$$
-f \cdot \frac{E^{2}}{f^{2}} +f^{-1}\dot{r}^{2}=-1
$$
Solving this for $\dot{r}$ and noticing that $f$ won't be zero so we can cancel it in the left hands first term we have:

$$
\dot{r}^{2} = E^{2}-1 + \frac{2GM}{r}
$$

We then take $E\to0$, which exactly saturates the lower bound we found earlier.

Let's evaluate $\tau_{\text{max}}$, using the constraint we found earlier and integrating the component to find $\tau$,

$$
\tau_{\text{max}} = \int _{0}^{2GM} \frac{\mathrm{d}r}{\sqrt{ \frac{2GM}{r} -1 }}
$$

I'll be using Mathematica for the dirty works of the calculations here, the indefinite integral would yield:

$$
- \sqrt{ -1 + \frac{2GM}{r} } r -2GM \arctan \left[ \sqrt{ -1+ \frac{2GM}{r} } \right] 
$$
Taking the limit $r\to 0$ for the lower bound and substituting $2 GM$ for the upper bound gives

$$
\begin{cases}
r\to 0 & - \sqrt{ -1 + \frac{2GM}{r} } r -2GM \arctan \left[ \sqrt{ -1+ \frac{2GM}{r} } \right] =- G M \pi \\
r = 2GM & - \sqrt{ -1 + \frac{2GM}{r} } r -2GM \arctan \left[ \sqrt{ -1+ \frac{2GM}{r} } \right] =0
\end{cases}
$$
Thus:

$$
\tau_{\text{max}} = GM \pi
$$
Why is this the maximum and not a minimum? It is possible to show for a general energy (not assuming it was zero), we can have the same integration:

$$
\tau(E)=\int _{0}^{2GM} \frac{\mathrm{d}r}{\sqrt{ E^{2}-1+ \frac{2GM}{r} }}
$$

Obviously the denominator here is larger and thus the integration would be smaller. Therefore, for by monotonicity of integration (Monotonicity refers to a function consistently increasing or decreasing across its domain without reversing direction) we have:

$$
\tau(E) < \tau(E=0)=\pi GM, \forall E > 0
$$
Our final work would be to turn this into the SI units and calculate for a mass measured in solar masses.

$$
\tau_{\max}= \pi GM / c^{3}
$$
and numerical calculations (of course with a calculator) would reveal:

$$
\tau_{\max} \approx 1.55 \times 10^{-5} \left( \frac{M}{M_{\odot}} \right) \sec. 
$$
# 2

We first start to solve the Einstein Field Equations for he general spherically symmetric metric. The most general spherically symmetric line element is

$$
\mathrm{d}s^{2}= -e^{2\alpha}\mathrm{d}t^{2}+e^{2\beta}\mathrm{d}r^{2}+r^{2}\mathrm{d}\theta + r^{2}\sin ^{2} \theta \mathrm{d}\phi^{2}
$$
where $\alpha$ and $\beta$ are functions of $r$.

The nonzero Christoffel symbols are as follows:

$$
\begin{align}
\Gamma^{0}_{01} & =\alpha'(r) \\
\Gamma^{1}_{00} & = e^{2\alpha(r)-2\beta(r)} \alpha'(r) \\
\Gamma^{1}_{11} & = \beta'(r) \\
\Gamma^{1}_{22} & =-e^{-2\beta(r)}r \\
\Gamma^{1}_{33} & = -e^{-2\beta(r)}r\sin ^{2} \theta \\
\Gamma^{2}_{21} & = \frac{1}{r} \\
\Gamma^{2}_{33} & =-\cos \theta \sin \theta \\
\Gamma^{3}_{13} & =\frac{1}{r} \\
\Gamma^{3}_{23} & =\cot \theta \\
\end{align}
$$
And their symmetric counter-parts (Calculated using xAct Mathematica). The next to compute is the Ricci tensor. For them we have only four diagonal components that are non-zero:

$$
\begin{align}
R_{00}  & = \left[ e^{2\alpha-2\beta}\left( r \alpha'^{2}+\alpha'(2-r\beta')+r\alpha^{\prime\prime} \right)  \right] /r \\
R_{11} & = -\alpha'^{2}+ \frac{2\beta'}{r}+\alpha'\beta'-\alpha^{\prime\prime}  \\
R_{22} & = e^{-2\beta}\left( -1+e^{2\beta}-r \alpha'+r\beta' \right) \\
R_{33} & = e^{-2\beta}\sin ^{2}\theta \left( -1+e^{2\beta}-r \alpha'+r\beta' \right)
\end{align}
$$
Now we take a step back to EFEs. As one can easily derive:

$$
\begin{align}
0 & = G_{\mu \nu}+\Lambda g_{\mu \nu} \\
 & = g^{\mu \nu}\left( \Lambda g_{\mu \nu}+ R_{\mu \nu}-\frac{1}{2}g_{\mu \nu}R \right) \\
 &  =n\Lambda + \frac{2-n}{2} R, 
\end{align}
$$
where $n$ is the dimension of the manifold. Substituting with 4 we have an equation:

$$
R = 4\Lambda
$$
Which means

$$
R_{\mu \nu}=\Lambda g_{\mu \nu}
$$

Resulting in these four equations:

$$
\begin{align}
R_{00}= \Lambda g_{00}  & \to -\Lambda = e^{-2\beta}\left( r\alpha'^{2}+\alpha'(2-r\beta')+r\alpha^{\prime\prime} \right) / r \\
R_{11}= \Lambda g_{11} & \to e^{2\beta}\Lambda = -\alpha'^{2}+ \frac{2\beta'}{r}+\alpha'\beta'-\alpha^{\prime\prime} \\
R_{22}=\Lambda g_{22} & \to \Lambda r^{2}=e^{-2\beta}\left( -1+ e^{2\beta}-r\alpha' +r\beta'\right) \\
R_{33}=\Lambda g_{33} & \to \Lambda r^{2}=e^{-2\beta}\left( -1 + e^{2\beta}-r \alpha' +r\beta' \right) 
\end{align}
$$
The last two equations are the same therefore we would use only one from now on. It is obviously expected and nothing to be worried about.

It is possible to derive some constraints from these equations. Take the first two equations, obviously:

$$
-e^{2\alpha}\Lambda=e^{2\alpha-2\beta}\left( \alpha'^{2}+\frac{2\alpha'}{r}-\alpha'\beta'+\alpha^{\prime\prime} \right) 
$$
can be written:

$$
-\Lambda\equiv e^{-2\beta}\left( \alpha'^{2}+\frac{2\alpha'}{r}-\alpha'\beta'+\alpha^{\prime\prime} \right) 
$$
and for the second one multiplying by $e^{-2\beta}$ would transform it to:

$$

$$