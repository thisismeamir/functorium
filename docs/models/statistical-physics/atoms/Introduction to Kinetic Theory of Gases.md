---
sticker: lucide//atom
---

# Introduction

> **Kinetic Theory** studies the macroscopic properties of large numbers of particles, starting from their (classical) equations of motion.

Thermodynamics describes macroscopic objects, their relations and behavior. It is a phenomenological theory to the processes in an ensemble. But at the microscopic level, we know that these systems are composed of particles (atoms, molecules), whose interactions and dynamics are reasonably well understood in terms of more fundamental theories. If these microscopic descriptions are complete, we should be able to account for the things we see in the macroscopic behavior.

Kinetic theory attempts to achieve this objective. In particular, we shall try to answer the following questions:

1. How can we define "equilibrium" for a system of moving particles?
2. Do all systems naturally evolve towards an equilibrium state?
3. What is the time evolution of a system that is not in equilibrium?

The simplest form of a system to describe can be considered to be a gas. Assuming a volume of gas contains about $10^{23}$ particles each with momentum $p_i$ and position $q_i$ we know that such system has a $6N$-dimensional phase space. The time evolution of a point in this space (which describes the state of the system completely because it contains all the momentums and positions) is governed by the canonical equations:


$$
\begin{cases} \frac{\mathrm d\vec q_i}{\mathrm d t}=\frac{\partial\mathcal H}{\partial \vec p_i}\\
\frac{\mathrm d \vec p_i}{\mathrm d t} = -\frac{-\partial\mathcal H}{\partial \vec q_i}
\end{cases}
$$

Where the Hamiltonian describes the total energy in terms of the set of coordinates $\mathbf{q}\equiv\{\vec q_i\}$, and momenta $\mathbf{p}\equiv\{\vec p_i\}$. 

As formulated in thermodynamics, the macrostate $M$ of an ideal gas in equilibrium is described by a small number of state functions such as $E$, $T$, $P$, and $N$. The space of macrostates is considerably smaller than the phase space spanned by microstates. Therefore, there must be a very large number of microstates $\mu$ corresponding to the same macrostate $M$.

This many-to-one correspondence suggests the introduction of a statistical ensemble of microstates. Consider $\mathcal N$ copies of a particular macrostate, each described by a different representative point $\mu(t)$ in the phase space $\Gamma$. 

Let $\mathrm d\mathcal N(\mathbf p, \mathbf q, t)$ equal the number of representative points in an infinitesimal volume $\mathrm d \Gamma = \prod_{i=1}^N \mathrm d^3\vec p_i \mathrm d^3\vec q_i$ around the point $(\mathbf p, \mathbf q)$. A phase space density is then defined as below:

$$
\rho(\mathbf p ,\mathbf q, t)\mathrm d \Gamma = \lim_{\mathcal N\rightarrow \infty}\frac{\mathrm d \mathcal N(\mathbf p , \mathbf q , t)}{\mathcal N}
$$

This quantity can be compared with [[../../statistics/atoms/Objective Probability|Objective Probability]].
Clearly, $\int \mathrm d \Gamma\rho = 1$ and $\rho$ is a properly normalized probability density function in phase space. To compute macroscopic values for various functions $\mathcal O(\mathbf p, \mathbf q)$, we shall use the ensemble averages:

$$
\langle\mathcal O \rangle = \int \mathrm d\Gamma \rho(\mathbf p , \mathbf q, t)\mathcal O (\mathbf p, \mathbf q)
$$

When the exact microstate $\mu$ of the system is known, the system is said to be in a *pure state*. But if our account for the system is probabilistic, in the sense of its being taken from an ensemble with density $\rho(\Gamma)$, it is said to belong to a *mixed state*.

Obviously a systems microstate changes constantly and therefore, not only it is difficult, but also absurd to define equilibrium of a system based on its microstate. Thus, Equilibrium is more conveniently described for mixed states by examining the time evolution of the phase space density $\rho(t)$, which is governed by the Liouville equation.