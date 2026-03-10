---
sticker: lucide//atom
---
# The Zeroth Law

The zeroth law of thermodynamics describes the transitive nature of thermal equilibrium.

***If two systems, $A$ and $B$, are separately in equilibrium with a third system $C$, then they are also in equilibrium with one another.***

This law looks very simple, but it has a great implication. It implies the existence of an important state function, the empirical temperature $\Theta$, such that systems in equilibrium are are the same temperature.

![[../../../attachments/Pasted image 20251121191250.png]]

What this means? Let the equilibrium state of systems $A$, $B$, and $C$ be described by the coordinates $\{A_i\}$, $\{B_i\}$ and $\{C_i\}, respectively. The assumption that $A$ and $B$ are in equilibrium states implies a **constraint*** between $A$ and $C$ coordinates. This means if $A_j$ were to change, it would do so to hold the equilibrium with $C_j$ coordinates. 

One can write this using mathematics as a function $f$:

$$
f_{AC}(A_i;C_j) = 0
$$
This also is implied between $B$ and $C$:


$$
f_{BC}(B_i;C_j)=
$$

Note that each system is assumed to be separately in mechanical equilibrium. If they could also do work on one another additional constraints were needed. One can write this a bit differently:

$$
\begin{align}
C_k = f_{AC}(A_i;C_{j\not = k})\\
C_k = f_{BC}(B_i;C_{j\not = k})
\end{align}
$$
which means:
$$
f_{AC}(A_i;C_{j\not = k}) = f_{BC}(B_i;C_{j\not = k})
$$
However we know that by the zeroth law:

$$
f_{AB}(A_i;B_j)= 0 
$$

If we choose a set of $A_i$s and $B_i$s that satisfy this, they would also satisfy the equality between $f_{AC}$ and $f_{BC}$. This happens regardless of choosing $C_j$ coordinates, namely if the two functions free-variables are only of $C_j$ they equality holds.

This would mean we can reduce the equality to separation of $A$ and $B$ coordinates from $C$ and write:

$$
\Theta(A_i) = \Theta(B_j)
$$

that is, equilibrium is characterized by a function $\Theta$ of thermodynamic coordinates. This function specifies the *equation of state*, and the *isotherms*, of $A$ are described by the condition $\Theta_A(A_i)=\Theta$.

While at this point there are many potential choices for this function, the key point is the existence of a function that constraints the parameters of each system in thermal equilibrium.

$\Theta$ is rather similar to the force in a mechanical system. Consider two one-dimensional systems that can do work on each other as in the case of two springs connected together. Equilibrium is achieved when the forces exerted by each body on the other are equal.
