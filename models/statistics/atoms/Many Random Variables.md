---
sticker: lucide//atom
---
# Many Random Variables

With more than one random variable, the set of outcomes is an $N$-dimensional space, $\mathcal S_x = \{-\infty < x_1,x_2,\dots,x_N<\infty\}$.

- The joint PDF $p(x)$ is the probability density of an outcome in a volume element $d^N\mathbf x= \prod_{i=1}^N dx_i$, around the point $x =\{x_1,x_2,\dots,x_N\}$. The joint PDF is normalized such that.
$$
p_x(\mathcal S)=\int d^N\mathbf x p(\mathbf x) = 1
$$
If and only if, the $N$ random variables are independent, the joint PDF is the product of individual PDF,

$$
p(\mathbf x) = \prod_{i=1}^N p_i(x_i)
$$

- The unconditional PDF describes the behavior of a subset of random variables, independent of the values of the others.
