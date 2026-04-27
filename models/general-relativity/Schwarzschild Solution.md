
After Einstein wrote down the field equation of general relativity he did not expect it to admit exact solutions owning to its complexity. He himself used an approximate solution in his 1915 article about the perihelion of Mercury. 

It therefore came as something of a surprise when Einstein received a letter from Karl Schwarzschild at the end of 1915 detailing a rather simple exact solution. 

The Schwarzschild Solution is a solution of the Einstein field equations for the geometry outside  a spherically symmetric, gravitating mass distribution.

## The Answer

The Schwarzschild metric line element for the space outside a static, spherically symmetric gravitating body of mass $M$ at the origin of a set of coordinates $(t,r,\theta,\phi)$ is written as:

$$
\mathrm{d}s^{2} = -\left( 1- \frac{2M}{r} \right) \mathrm{d}t^{2} + \left( 1 - \frac{2M}{r} \right) ^{-1} \mathrm{d}r^{2} + r^{2}\left( \mathrm{d}\theta^{2} + \sin ^{2} \theta \mathrm{d}\phi^{2} \right). 
$$

Notable features of this line element include:
- It is static: none of the components of the metric depend on time;
- It is asymptotically flat: as $r\to \infty$ it looks like the Minkowski metric;
- It appears badly behaved at the origin, and also when $r=2M$, where the second term becomes singular.
One additional reason why this line element is so special is that [[Birkhoff's Theorem]] tells us that any spherically symmetric solution to the Einstein equation outside a gravitating object, will be identical to Schwarzschil'd static solution.

# Construction and Structural Understanding

The solution of Schwarzschild is a solution in vacuum therefore, the stress-energy tensor in Einstein's Field Equation should be set to zero:

$$
T^{\mu\nu}=0
$$
Which implies Ricci tensor being zero as well:

$$
\begin{align}

G_{\mu \nu}  & = 0 \\
R_{\mu \nu} - \frac{1}{2}g_{\mu \nu}R  & = 0 \\
g^{\mu \nu}R_{\mu \nu} &  = \frac{1}{2} g^{\mu \nu}g_{\mu \nu}R \\
R  & =2R \\
 \therefore R  & =0
\end{align}
$$

## The Metric Ansatz

Now we need to write down the most general case of a metric that is static and spherically symmetric and derive our solution from it. If the metric is to be spherically symmetric it means that it cannot depend on the values of $\theta,$ and $\phi$.  Also if the metric is to be static it cannot depend on time. 

With this deduction the only coordinate left is the radius (assuming that we are speaking in the spherical coordinates). The Ansatz we put is the following:

$$
\mathrm{d}s^{2} = -e^{ 2\alpha } \mathrm{d}t^{2} + e^{ 2\beta }\mathrm{d}r^{2} + r^{2} (\mathrm{d}\Omega^{2}).
$$

Some key points to note of:

1. The exponential parameterization is a choice to make sure that the signature doesn't change.
2. We've already used coordinate freedom to set $g_{\theta \theta}= r^{2}$ (this is the definition of the areal radius $r$).
3. We've also used symmetry to eliminate the $\mathrm{d}t\mathrm{d}r$ cross term.

Spherical symmetry means the metric is invariant under the action of $SO(3)$. If $\alpha = \alpha(t,r,\theta,\phi)$ then a rotation would map $\alpha \to \alpha'$, which means the metric changes.