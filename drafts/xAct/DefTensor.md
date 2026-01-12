---
sticker: lucide//atom
---
# DefTensor

Any vector, tensor and even scalar field can be defined using the def tensor function in xAct mathematica
$$
\begin{align}
0&\rightarrow \text{Scalar Field}\\
1 &\rightarrow \text{Vector Field}\\
n > 1&\rightarrow \text{Tensor Field}
\end{align}
$$

```mathematica
DefTensor[v[], M]; (* scalar field *)
DefTensor[u[a],M]; (* vector field *)
DefTensor[F[-a,-b],M]; (* Tensor field of rank 2 *)
```


## Tags
#atom #theory 