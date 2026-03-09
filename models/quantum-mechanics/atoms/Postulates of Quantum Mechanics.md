---
sticker: lucide//atom
---
# Postulates of Quantum Mechanics 

The following are postulates of non-relativistic quantum mechanics. We consider first a system with one degree of freedom, namely, a single particle in one space dimension. 

- The state of the particle is represented by a vector $\left| \psi(t)\right\rangle$ in a Hilbert space.
- The independent variables $x$ and $p$ of classical mechanics are represented by Hamiltonian operators $X$ and $P$ with the following matrix elements.
  $$ \begin{align}\left\langle x\right| X\left|x'\right\rangle &= x\delta(x-x') \\ \left\langle x\right| P\left|x'\right\rangle &= -i\hbar \delta'(x-x')\end{align}$$
  The operators corresponding to dependent variables $\omega(x,p)$ are given Hamiltonian operators:
  $$ \Omega(X,P) = \omega(x\rightarrow X, p\rightarrow P)$$
- If the particle is in a state $\left|\psi \right\rangle$, measurement of the variable $\Omega$ will yield one of the eigenvalues $\omega$ with probability $P(\omega)\propto \left|\left\langle\omega|\psi\right\rangle\right|^2$. The state of the system will change from $|\psi\rangle$ to $|\omega\rangle$ as a result of the measurement.
- The state vector $|\psi(t)\rangle$ obeys the Schroedinger equation:
  $$ i\hbar \frac{\mathrm d}{\mathrm dt}|\psi(t)\rangle = H|\psi(t)\rangle$$
  where $H(X,P)=\mathcal H(x\rightarrow X, p\rightarrow P)$ is the quantum Hamiltonian operator and $\mathcal H$ is the Hamiltonian for the corresponding classical problem.

These postulates fall naturally into two sets, the first three, which tell us how the system is depicted at a given time, and the last, which specifies how this picture changes with time. 

The first postulate states that a particle is described by a ket in a Hilbert space which, you will recall, contains proper vectors normalizable to unity as well as inproper vectors, normalizable only to the Dirac delta functions. 

This ket can be represented by an infinite set of numbers each corresponding to the scalar multiplied by each basis vector. The question arises that *why a particle, which had only two independent degrees of freedom, $x$ and $p$, in classical mechanics, now needs to be specified by an infinite number of variables?*

