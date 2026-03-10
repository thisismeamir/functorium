---
sticker: lucide//atom
---
# Kinematics of Collision and Scattering

The integrand of this equation is a derivative of $f_{2}$ with respect to $\vec{q}$ along the direction of relative motion $\vec{p} = \vec{p}_{2}-\vec{p}_{1}$ of the colliding particles.

$$
\int \mathrm{d}^3\vec{p}_{2} \mathrm{d}^3\vec{q} \left( \frac{\vec{p}_{2}-\vec{p}_{1}}{m} \right) \cdot \frac{\partial}{\partial \vec{q}}f_{2}(\vec{p}_{1},\vec{q}_{1},\vec{p}_{2},\vec{q}_{2};t)
$$

![[../../../attachments/Pasted image 20260206193342.png]]

To perform this integration we introduce a convenient coordinate system for $\vec{q}$, guided by the formalism used to describe the scattering particles. Naturally, we choose one axis to be parallel to $\vec{p}_{2}-\vec{p}_{1}$, with the corresponding coordinate $a$ that is negative before a collision, and positive afterwards. The other two coordinates of $\vec{q}$ are represented by an impact factor $\vec{b}$ that is $\vec{0}$ for a head on collision $([\vec{p}_{1}-\vec{p}_{2}]|| [\vec{q}_{1}-\vec{q}_{2}])$. We can now integrate over $a$ to get

$$
\left. \frac{\mathrm{d}f_{1}}{\mathrm{d}t} \right\vert_{\text{coll.}} = \int \mathrm{d}^{3}\vec{p}_{2} \mathrm{d}^{2}\vec{b}\left| \vec{v}_{1}-\vec{v}_{2} \right| \left[ f_{2}(\vec{p}_{1},\vec{q}_{1},\vec{p}_{2},\vec{b},+;t) - f_{2}(\vec{p}_{1},\vec{q}_{1},\vec{p}_{2},\vec{b},-;t) \right]   
$$

where $\left| \vec{v}_{1}-\vec{v}_{2} \right| = \left| \vec{p}_{1}-\vec{p}_{2} \right|/m$ is the relative speed of the two particles, with $(\vec{b},-)$ and $(\vec{b},+)$ referring to the relative coordinates before and after the collision. Note that $\mathrm{d}^{2}\vec{b}\left| \vec{v}_{1}-\vec{v}_{2} \right|$ is just the flux of particles impinging on the element of area $\mathrm{d}^{2}\vec{b}$.

In principle, the integration over $a$ is from $-\infty$ to $+\infty$, but as the variations of $f_{2}$ are only significant over the interaction range $d$, we can evaluate the above quantities at separations of a few $d$ from the collision point. This is a good compromise, allowing us to evaluate $f_{2}$ away from the collisions, but at small enough separations so that we can ignore the difference between $\vec{q}_{1}$ and $\vec{q}_{2}$. This amount to coarse graining in space that eliminates variations on scales finer than $d$.

With these provisos, it is tempting to close the equation for $f_{1}$, by using the assumption of uncorrelated particles. Clearly some care is necessary as a naive substitution gives zero. The key observation is that the densities $f_{2}$ for situations corresponding to before and after the collision have to be treated differently. Collisions will tend to randomize momenta, yielding a more isotropic distribution. However, the densities $f_{2}$ before and after the collision are related by streaming, implying that:

$$
f_{2}(\vec{p}_{1},\vec{q}_{1},\vec{p}_{2},\vec{b},+;t) = f_{2}(\vec{p}_{1}',\vec{q}_{1}',\vec{p}_{2}',\vec{b},-;t)
$$
where $\vec{p}_{1}'$ and $\vec{p}_{2}'$ are momenta whose collision at an impact vector $\vec{b}$results in production of outgoing particles with momenta $\vec{p}_{1}$ and $\vec{p}_{2}$. They can be obtained using time reversal symmetry, by integrating the equations of motion for incoming colliding particles of momenta $-\vec{p}_{1}$ and $-\vec{p}_{2}$. In terms of these momenta we can write:

$$
\left. \frac{\mathrm{d}f_{1}}{\mathrm{d}t} \right\vert_{\text{coll.}} = \int \mathrm{d}^{3}\vec{p}_{2}\mathrm{d}^{2}\vec{b} \left| \vec{v}_{1}-\vec{v}_{2} \right| \left[ 
f_{2}(\vec{p}_{1}',\vec{q}_{1},\vec{p}_{2}',\vec{b},-;t) - f_{2}(\vec{p}_{2},\vec{q}_{1},\vec{p}_{2},\vec{b},-;t)
\right]  
$$

It is sometimes more convenient to describe the scattering of two prticles in terms of the relative momenta $\vec{p}=\vec{p}_{1}-\vec{p}_{2}$ and $\vec{p}'=\vec{p}_{1}'-\vec{p}_{2}'$, before and after the collision. For a given $\vec{b}$, the initial momentum $\vec{p}$ is deterministically transformed to the final momentum $\vec{p}'$. To find the functional form $\vec{p}'(|\vec{p}|,\vec{b})$, one must integrate the equations of motion. However, it is possible to make some general statements based on conservation laws:

In elastic collisions the magnitude of $\vec{p}$ is conserved, and it merely rotates to a final direction indicated by angles $(\theta, \phi) \equiv \hat{\Omega}(\vec{b})$ (a unit vector) in spherical coordinates. Since there is a one-to-one correspondence between the impact vector $\vec{b}$ and the solid angle $\Omega$, we make a change of variables between the two resulting in:

$$
\left. 
\frac{\mathrm{d}f_{1}}{\mathrm{d}t}
\right\vert_{\text{coll.}} = \int \mathrm{d}^{3}\vec{p}_{2} \mathrm{d}^{2}\Omega \left| \frac{\mathrm{d}\sigma}{\mathrm{d}\Omega} \right| \left| \vec{v}_{1}-\vec{v}_{2} \right| \left[ f_{2}(\vec{p}_{1}',\vec{q}_{1},\vec{p}_{2}',\vec{b},-;t)-f_{2}(\vec{p}_{1},\vec{q}_{1},\vec{p}_{2},\vec{b},-;t) \right]  
$$

The Jacobian of this transformation, $|\mathrm{d}\sigma / \mathrm{d}\Omega|$, has dimensions of area, and is known as the *differential cross-section*. It is equal to the area presented to an incoming beam that scatters into the solid angle $\Omega$. The outgoing momenta $\vec{p}_{1}'$ and $\vec{p}_{2}'$ are now obtained from the two conditions:

$$
\begin{align}
\vec{p}_{1}'+\vec{p}_{2}'  & = \vec{p}_{1}+\vec{p}_{2}  \\
\vec{p}_{1}'-\vec{p}_{2}'  & = |\vec{p}_{1}-\vec{p}_{2}|\hat{\Omega}(\vec{b})
\end{align}
$$
We find:

$$
\begin{cases}
\vec{p}_{1}' =\left( \vec{p}_{1}+\vec{p}_{2}+\left| \vec{p}_{1}-\vec{p}_{2} \right| \hat{\Omega}(\vec{b}) \right) / 2 \\
\vec{p}_{2}' =\left( \vec{p}_{1}+\vec{p}_{2}-\left| \vec{p}_{1}-\vec{p}_{2} \right| \hat{\Omega}(\vec{b}) \right) / 2 
\end{cases}
$$

For scattering of two hard spheres of diameter $D$, it is easy to show that the scattering angle is related to the impact parameter as below:

$$
\cos(\theta /2) = b /D
$$
for all $\phi$. The differential corss-section is then obtained from:

$$
\mathrm{d}^{2}\sigma = b\mathrm{d}b\mathrm{d}= D\cos \left( \frac{\theta}{2} \right) D \sin \left( \frac{\theta}{2} \right) \frac{\mathrm{d}\theta}{2}\mathrm{d}\phi = \frac{D^{2}}{4}\sin \theta \mathrm{d}\theta \mathrm{d}\phi = \frac{D^{2}}{4}\mathrm{d}^{2}\Omega
$$

Integrating over all angles leads to the total corss-section of $\sigma=\pi D^{2}$, which is evidently correct. The differential cross-section for hard spheres is independent of both $\theta$ and $|\vec{P}|$. This is not the case for soft potentials. 

The Boltzmann equation is obtained from:

$$
\left. 
\frac{\mathrm{d}f_{1}}{\mathrm{d}t}
\right\vert_{\text{coll.}} = \int \mathrm{d}^{3}\vec{p}_{2} \mathrm{d}^{2}\Omega \left| \frac{\mathrm{d}\sigma}{\mathrm{d}\Omega} \right| \left| \vec{v}_{1}-\vec{v}_{2} \right| \left[ f_{2}(\vec{p}_{1}',\vec{q}_{1},\vec{p}_{2}',\vec{b},-;t)-f_{2}(\vec{p}_{1},\vec{q}_{1},\vec{p}_{2},\vec{b},-;t) \right]  
$$

after the substitution:

$$
f_{2}(\vec{p}_{1},\vec{q}_{1},\vec{p}_{2},\vec{b},-;t) = f_{1}(\vec{p}_{1},\vec{q}_{1},t)f_{1}(\vec{p}_{2},\vec{q}_{1},t),
$$

known as the assumption of molecular chaos. Not that even if one starts with an uncorrelated initial probability distribution for particles, there is no guarantee that correlations are not generated as a result of collisions. The final result is the following closed form equation for $f_{1}$:

$$
\begin{align}
\left[ \frac{\partial}{\partial t}- \frac{\partial U}{\partial \vec{q}_{1}}\cdot \frac{\partial}{\partial \vec{p}_{1}} + \frac{\vec{p}_{1}}{m}\cdot \frac{\partial}{\partial \vec{q}_{1}} \right]f_{1}  & = \\
-\int \mathrm{d}^{3}\vec{p}_{2}\mathrm{d}^{2}\Omega \left| \frac{\mathrm{d}\sigma }{\mathrm{d}\Omega} \right| \left| \vec{v}_{1} - \vec{v}_{2} \right|  & \left[ f_{1}(\vec{p}_{1},\vec{q}_{1},t)f_{1}(\vec{p}_{2},\vec{q}_{1},t)-f_{1}(\vec{p}_{1}',\vec{q}_{1},t)f_{1}(\vec{p}_{2}',\vec{q}_{1},t) \right]  
\end{align}
$$
Given the complexity of the above *derivation* of the Boltzmann equation, it is appropriate to provide a heuristic explanation. The streaming terms on the left-hand side of the equation describe the motion of a single particle in the external potential $U$. The collision terms on the right-hand side have a simple physical interpretation:  the probability of finding a particle of momentum $\vec{p}_{1}$ at $\vec{q}_{1}$ is suddenly altered if it undergoes a collision with another particle of momentum $\vec{p}_{2}$. 

The probability of such collision is the product of kinematic factors described by the differential corss-section, the flux of incident particlee $(|\vec{v}_{1}-\vec{v}_{2}|)$, and the joint probability of the two particles, approximated by $f_{1}(\vec{p}_{1})f_{1}(\vec{p}_{2})$. The first term on the right-hand side subtracts this probability and integrates over all possible momenta and solid angles describing the collision. 

The second term represents an addition to the probability that results from the inverse process.