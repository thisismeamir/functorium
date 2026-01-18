---
sticker: lucide//atom
---
# Simple Metric Spaces in Vector Spaces

A metric space is a set \( M \) equipped with a distance function \( d: M \times M \to \mathbb{R} \) that satisfies the following properties for all points \( x, y, z \in M \):

1. **Non-negativity**: \( d(x, y) \geq 0 \)
2. **Identity of indiscernibles**: \( d(x, y) = 0 \) if and only if \( x = y \)
3. **Symmetry**: \( d(x, y) = d(y, x) \)
4. **Triangle inequality**: \( d(x, z) \leq d(x, y) + d(y, z) \)

## Euclidean Metric

In an \( n \)-dimensional vector space \( \mathbb{R}^n \), the most common metric is the Euclidean metric, defined as:

$$
d(\mathbf{x}, \mathbf{y}) = \| \mathbf{x} - \mathbf{y} \| = \sqrt{(x_1 - y_1)^2 + (x_2 - y_2)^2 + \cdots + (x_n - y_n)^2}
$$

where \( \mathbf{x} = (x_1, x_2, \ldots, x_n) \) and \( \mathbf{y} = (y_1, y_2, \ldots, y_n) \).

## Manhattan Metric

Another simple metric is the Manhattan metric (or taxicab metric), defined as:

$$
d(\mathbf{x}, \mathbf{y}) = \| \mathbf{x} - \mathbf{y} \|_1 = |x_1 - y_1| + |x_2 - y_2| + \cdots + |x_n - y_n|
$$

## Supremum Metric

The supremum metric (or uniform metric) is defined as:

$$
d(\mathbf{x}, \mathbf{y}) = \| \mathbf{x} - \mathbf{y} \|_\infty = \max\{|x_1 - y_1|, |x_2 - y_2|, \ldots, |x_n - y_n|\}
$$

## Discrete Metric

The discrete metric is defined as:

$$
d(x, y) =
\begin{cases} 
0 & \text{if } x = y \\
1 & \text{if } x \neq y 
\end{cases}
$$

In this metric space, every point is isolated from all others except itself.