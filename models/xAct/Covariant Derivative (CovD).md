---
sticker: lucide//atom
---
# Covariant Derivative (CovD)

Using `CovD` command one can take the covariant derivative
Directional derivative along a curve with tangent vector $\vec U$ is:

$$
\frac{dv}{du} = \vec U \cdot \vec\nabla v = \frac{dv^\alpha}{du} e_\alpha + v^\alpha \frac{\partial e_\alpha}{\partial x^\beta}\frac{dx^\beta}{du} = \left(\frac{dv^c}{du} + v^\alpha \Gamma^c_{\alpha\beta}\frac{dx^b}{du}\right)e_c
$$
In Mathematica we write
```mathematica
CD[-a] @ v[b];
```
another example
```mathematica
u[a] CD[-a] @ v[b];
```
