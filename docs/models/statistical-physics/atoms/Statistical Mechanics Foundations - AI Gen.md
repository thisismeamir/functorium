---
sticker: lucide//atom
---
# Classical Statistical Mechanics: Foundations

## Chapter 4, Sections 4.1-4.2

---

## 4.1 General Definitions

### The Fundamental Problem

**Statistical mechanics** provides a probabilistic approach to equilibrium properties of macroscopic systems with many degrees of freedom.

**The hierarchy of description:**

1. **Macrostate** $M$: Described by few thermodynamic coordinates (e.g., $E$, $V$, $N$)
2. **Microstate** $\mu$: Complete specification of all microscopic degrees of freedom (requires enormous information)
3. **Ensemble**: Collection of microstates corresponding to a given macrostate

### Key Philosophy

Instead of tracking individual microstates (which evolve via complicated Hamiltonian dynamics), we examine **ensembles** and assign probabilities $p_M(\mu)$ to microstates.

**Central assumption (justified by Liouville's theorem):**

> All accessible microstates are equally likely in equilibrium.

### Important Notes

- Probability assignment is **subjective** (as discussed in information theory)
- We provide **unbiased estimates** of $p_M(\mu)$ for different ensembles
- **Thermodynamic limit**: With $N \to \infty$, all ensembles become equivalent
- Statistical mechanics is **time-independent**: it describes equilibrium, not how systems reach it (contrast with kinetic theory)

---

## 4.2 The Microcanonical Ensemble

### Physical Setup

Consider a system that is:

- **Mechanically isolated** (no work input)
- **Adiabatically isolated** (no heat input)

Therefore:

- Internal energy $E$ is fixed
- Generalized coordinates $\mathbf{x}$ are fixed

**Macrostate:** $M \equiv (E, \mathbf{x})$

### Phase Space Description

In classical mechanics, microstates are points $\mu$ in phase space: $$\mu = (\mathbf{q}_1, \ldots, \mathbf{q}_N, \mathbf{p}_1, \ldots, \mathbf{p}_N)$$

Evolution is governed by Hamiltonian $\mathcal{H}(\mu)$ via Hamilton's equations.

**Energy conservation** confines all accessible microstates to the **constant energy surface**: $$\mathcal{H}(\mu) = E$$

**Assumption:** No other conserved quantities exist, so all points on this surface are mutually accessible.

### The Central Postulate

**The equilibrium probability distribution is:**

$$\boxed{p(E, \mathbf{x}) = \begin{cases} \frac{1}{\Omega(E, \mathbf{x})} & \text{if } \mathcal{H}(\mu) = E \ 0 & \text{otherwise} \end{cases}}$$

where $\Omega(E, \mathbf{x})$ is the **area of the constant energy surface** in phase space.

### Critical Remarks

#### **1. Boltzmann's Equal A Priori Probabilities**

This postulate is:

- The **unbiased probability estimate** subject to constant energy constraint
- **Consistent with** (but not required by) Liouville's theorem
- **Coordinate-independent**: Under canonical transformations $\mu \to \mu'$, phase space volumes are invariant (Jacobian = 1)

If $\mu \to \mu'$ is canonical, then: $$p(\mu') = p(\mu) \frac{\partial \mu}{\partial \mu'} = p(\mu) \cdot 1 = p(\mu)$$

The uniform distribution remains uniform.

#### **2. Energy Shell vs. Energy Surface**

**Technical subtlety:** A surface has measure zero, making the density distribution singular.

**Practical solution:** Define the microcanonical ensemble using an **energy shell**: $$E - \delta \leq \mathcal{H}(\mu) \leq E + \delta$$

Then the accessible phase space has volume: $$\Omega_{\delta} \approx 2\delta \Omega$$

where $\Omega$ is the surface "area".

**Key observation:** Since $\Omega$ typically grows **exponentially** with $E$ (or $N$): $$\Omega(E) \sim e^{N f(E/N)}$$

As long as $\delta \sim E^0$ or even $\delta \sim E^1$, in the thermodynamic limit $E \propto N \to \infty$: $$\frac{\Omega_{\delta}}{\Omega} \approx 2\delta \to \text{negligible}$$

Therefore $\Omega$ and $\Omega_{\delta}$ are **interchangeable**.

#### **3. Entropy Definition**

The entropy of the microcanonical ensemble is:

$$\boxed{S(E, \mathbf{x}) = k_B \ln \Omega(E, \mathbf{x})}$$

**Properties:**

- **Boltzmann constant** $k_B$ gives correct dimensions: [energy/temperature]
- **Coordinate invariant**: Canonical transformations don't change $\Omega$, so $S$ is invariant
- **Extensive**: For independent systems, $$\Omega_{\text{total}} = \prod_i \Omega_i \implies S_{\text{total}} = \sum_i S_i$$

---

## Derivation of Thermodynamic Laws

### The Zeroth Law: Thermal Equilibrium

#### Setup

Two isolated systems with energies $E_1$ and $E_2$ are brought into **thermal contact** (can exchange energy but not work).

**Combined system:**

- Total energy: $E = E_1 + E_2$ (fixed)
- Microstates: $\mu = \mu_1 \otimes \mu_2$
- Hamiltonian: $\mathcal{H}(\mu_1 \otimes \mu_2) = \mathcal{H}_1(\mu_1) + \mathcal{H}_2(\mu_2)$

**Joint microcanonical distribution:**

$$p(E, \mu_1 \otimes \mu_2) = \begin{cases} \frac{1}{\Omega(E)} & \text{if } \mathcal{H}_1(\mu_1) + \mathcal{H}_2(\mu_2) = E \ 0 & \text{otherwise} \end{cases}$$

#### Calculating the Total Phase Space

The total number of accessible states is:

$$\Omega(E) = \int dE_1 , \Omega_1(E_1) \Omega_2(E - E_1)$$

**Derivation:** For each choice of $E_1$:

- System 1 has $\Omega_1(E_1)$ accessible states
- System 2 has $\Omega_2(E_2) = \Omega_2(E - E_1)$ accessible states
- Total for this $E_1$: $\Omega_1(E_1) \Omega_2(E - E_1)$
- Integrate over all possible $E_1$ divisions

Converting to entropy using $S_i = k_B \ln \Omega_i$:

$$\Omega_i(E_i) = \exp\left(\frac{S_i(E_i)}{k_B}\right)$$

Therefore:

$$\boxed{\Omega(E) = \int dE_1 \exp\left[\frac{S_1(E_1) + S_2(E - E_1)}{k_B}\right]}$$

#### The Saddle Point Approximation

Since $S_i \propto N_i$ (extensive), the integrand is: $$\exp\left[\frac{S_1(E_1) + S_2(E - E_1)}{k_B}\right] \sim e^{N}$$

This is an **exponentially large** quantity.

**Mathematical principle:** For integrals of the form $\int dx , e^{Nf(x)}$ with $N \gg 1$: $$\int dx , e^{Nf(x)} \approx e^{Nf(x^_)} \sqrt{\frac{2\pi}{N|f''(x^_)|}}$$

where $x^*$ maximizes $f(x)$.

**Application here:** $$\Omega(E) \approx \exp\left[\frac{S_1(E_1^_) + S_2(E_2^_)}{k_B}\right]$$

where $E_2^* = E - E_1^*$.

**The entropy of the combined system:**

$$\boxed{S(E) = k_B \ln \Omega(E) \approx S_1(E_1^_) + S_2(E_2^_)}$$

#### Finding the Equilibrium Energy Distribution

The maximum occurs where: $$\frac{d}{dE_1}\left[S_1(E_1) + S_2(E - E_1)\right] = 0$$

Computing: $$\frac{\partial S_1}{\partial E_1}\bigg|_{\mathbf{x}_1} - \frac{\partial S_2}{\partial E_2}\bigg|_{\mathbf{x}_2} \cdot \frac{dE_2}{dE_1} = 0$$

Since $E_2 = E - E_1$, we have $dE_2/dE_1 = -1$, so:

$$\boxed{\frac{\partial S_1}{\partial E_1}\bigg|_{\mathbf{x}_1} = \frac{\partial S_2}{\partial E_2}\bigg|_{\mathbf{x}_2}}$$

#### Physical Interpretation

**Key insight:** Although all joint microstates are equally probable, there are **exponentially more** states near $(E_1^_, E_2^_)$ than anywhere else.

**Time evolution:**

1. Initially: system at some $(E_1^0, E_2^0)$ with $E_1^0 + E_2^0 = E$
2. After thermal contact: system explores all accessible microstates
3. Equilibrium: system found at $(E_1^_, E_2^_)$ with **overwhelming probability**

**Temperature definition:**

The condition for equilibrium defines a state function: $$\frac{\partial S}{\partial E}\bigg|_{\mathbf{x}}$$

Comparing with thermodynamics, this is:

$$\boxed{\frac{\partial S}{\partial E}\bigg|_{\mathbf{x}} = \frac{1}{T}}$$

This is the **statistical mechanical definition of temperature**.

---

### The First Law: Energy and Work

#### Reversible Change in Coordinates

Consider changing the generalized coordinates reversibly: $\mathbf{x} \to \mathbf{x} + \delta\mathbf{x}$

**Work done on the system:** $$\bar{dW} = \mathbf{J} \cdot \delta\mathbf{x}$$

where $\mathbf{J}$ is the generalized force conjugate to $\mathbf{x}$.

**Energy change:** $$E \to E + \mathbf{J} \cdot \delta\mathbf{x}$$

#### Change in Entropy

The first-order variation in entropy is:

$$\Delta S = S(E + \mathbf{J} \cdot \delta\mathbf{x}, \mathbf{x} + \delta\mathbf{x}) - S(E, \mathbf{x})$$

Taylor expanding to first order:

$$\boxed{\Delta S = \frac{\partial S}{\partial E}\bigg|_{\mathbf{x}} (\mathbf{J} \cdot \delta\mathbf{x}) + \sum_i \frac{\partial S}{\partial x_i}\bigg|_{E, x_{j \neq i}} \delta x_i}$$

#### Condition for Spontaneous Change

A change occurs **spontaneously** if it increases entropy (or leaves it unchanged at equilibrium).

**Equilibrium condition:** The change should not occur spontaneously, so: $$\Delta S = 0$$

This requires the expression in brackets to vanish:

$$\frac{\partial S}{\partial E}\bigg|_{\mathbf{x}} (\mathbf{J} \cdot \delta\mathbf{x}) + \sum_i \frac{\partial S}{\partial x_i}\bigg|_{E, x_{j \neq i}} \delta x_i = 0$$

Using $\partial S/\partial E = 1/T$:

$$\frac{\mathbf{J} \cdot \delta\mathbf{x}}{T} + \sum_i \frac{\partial S}{\partial x_i}\bigg|_{E, x_{j \neq i}} \delta x_i = 0$$

Since this must hold for **arbitrary** $\delta\mathbf{x}$, we identify:

$$\boxed{\frac{\partial S}{\partial x_i}\bigg|_{E, x_{j \neq i}} = -\frac{J_i}{T}}$$

#### The First Law

Now we can write the **total differential** of $S(E, \mathbf{x})$:

$$dS = \frac{\partial S}{\partial E}\bigg|_{\mathbf{x}} dE + \sum_i \frac{\partial S}{\partial x_i}\bigg|_{E, x_{j \neq i}} dx_i$$

Substituting our identifications:

$$dS = \frac{dE}{T} - \frac{\mathbf{J} \cdot d\mathbf{x}}{T}$$

Rearranging:

$$\boxed{dE = T , dS + \mathbf{J} \cdot d\mathbf{x}}$$

This is the **first law of thermodynamics**!

**Identification:**

- $\bar{dQ} = T , dS$ (heat input)
- $\bar{dW} = \mathbf{J} \cdot d\mathbf{x}$ (work input)

Therefore: $$dE = \bar{dQ} + \bar{dW}$$

---

### The Second Law: Entropy Increase

#### The Fundamental Inequality

By construction, the equilibrium point $(E_1^_, E_2^_)$ maximizes the number of accessible states:

$$\Omega_1(E_1^_, \mathbf{x}_1) \Omega_2(E_2^_, \mathbf{x}_2) \geq \Omega_1(E_1, \mathbf{x}_1) \Omega_2(E_2, \mathbf{x}_2)$$

for any $(E_1, E_2)$ with $E_1 + E_2 = E$.

Taking logarithms:

$$\ln \Omega_1(E_1^_) + \ln \Omega_2(E_2^_) \geq \ln \Omega_1(E_1) + \ln \Omega_2(E_2)$$

Multiplying by $k_B$:

$$\boxed{S_1(E_1^_) + S_2(E_2^_) \geq S_1(E_1) + S_2(E_2)}$$

#### Entropy Increase

Define the **change in entropy** as:

$$\Delta S = [S_1(E_1^_) + S_2(E_2^_)] - [S_1(E_1) + S_2(E_2)]$$

Then:

$$\boxed{\Delta S \geq 0}$$

This is the **second law of thermodynamics**: entropy increases (or stays constant) in an isolated system.

#### Heat Flow Direction

When systems are first brought into contact, they're not at equilibrium, so: $$\frac{\partial S_1}{\partial E_1} \neq \frac{\partial S_2}{\partial E_2}$$

The entropy change is:

$$\Delta S = \left(\frac{\partial S_1}{\partial E_1}\bigg|_{\mathbf{x}_1} - \frac{\partial S_2}{\partial E_2}\bigg|_{\mathbf{x}_2}\right) \Delta E_1$$

where $\Delta E_1$ is the energy transferred to system 1.

Using $\partial S/\partial E = 1/T$:

$$\boxed{\Delta S = \left(\frac{1}{T_1} - \frac{1}{T_2}\right) \Delta E_1 \geq 0}$$

**Two cases:**

1. If $T_1 < T_2$: Then $1/T_1 > 1/T_2$, so we need $\Delta E_1 > 0$ (energy flows into system 1)
2. If $T_1 > T_2$: Then $1/T_1 < 1/T_2$, so we need $\Delta E_1 < 0$ (energy flows out of system 1)

**Conclusion:** Heat flows from hot to cold, consistent with **Clausius's statement** of the second law.

---

### Stability Conditions

#### Thermal Stability

Since $(E_1^_, E_2^_)$ is a **maximum** of $S_1(E_1) + S_2(E - E_1)$, the second derivative must be negative:

$$\frac{d^2}{dE_1^2}[S_1(E_1) + S_2(E - E_1)]\bigg|_{E_1^*} < 0$$

Computing:

$$\frac{\partial^2 S_1}{\partial E_1^2}\bigg|_{\mathbf{x}_1} + \frac{\partial^2 S_2}{\partial E_2^2}\bigg|_{\mathbf{x}_2} \cdot \left(\frac{dE_2}{dE_1}\right)^2 < 0$$

Since $dE_2/dE_1 = -1$:

$$\boxed{\frac{\partial^2 S_1}{\partial E_1^2}\bigg|_{\mathbf{x}_1} + \frac{\partial^2 S_2}{\partial E_2^2}\bigg|_{\mathbf{x}_2} < 0}$$

**Physical interpretation:**

Using $\partial S/\partial E = 1/T$:

$$\frac{\partial}{\partial E}\left(\frac{1}{T}\right) = -\frac{1}{T^2} \frac{\partial T}{\partial E} < 0$$

Therefore: $$\frac{\partial T}{\partial E} > 0$$

This means: **Adding energy increases temperature.**

Using the heat capacity at constant $\mathbf{x}$: $$C_{\mathbf{x}} = \frac{\partial E}{\partial T}\bigg|_{\mathbf{x}}$$

We get:

$$\boxed{C_{\mathbf{x}} > 0}$$

**Thermal stability:** Heat capacity must be positive.

#### Mechanical Stability

Similarly, the second-order changes in entropy (Eq. 4.8) must be non-positive for stability:

$$\Delta^{(2)} S = \frac{1}{2} \sum_{i,j} \frac{\partial^2 S}{\partial x_i \partial x_j}\bigg|_E \delta x_i \delta x_j \leq 0$$

This requires the matrix $\partial^2 S/\partial x_i \partial x_j$ to be **negative definite** (or equivalently, the matrix $-\partial^2 S/\partial x_i \partial x_j$ must be **positive definite**).

---

## Summary

### What We've Derived

From the single postulate of **equal a priori probabilities** in the microcanonical ensemble:

1. **Entropy:** $S = k_B \ln \Omega$
2. **Temperature:** $1/T = \partial S/\partial E$
3. **Generalized forces:** $J_i/T = -\partial S/\partial x_i$
4. **First law:** $dE = T , dS + \mathbf{J} \cdot d\mathbf{x}$
5. **Second law:** $\Delta S \geq 0$
6. **Zeroth law:** Systems in thermal equilibrium have equal temperatures
7. **Stability:** $C > 0$ and curvature conditions

### The Power of Statistical Mechanics

All of **phenomenological thermodynamics** emerges from:

- Counting accessible microstates
- Assuming equal probabilities
- Taking the thermodynamic limit ($N \to \infty$)

The **irreversibility** (second law) arises from the **exponential dominance** of high-entropy states in systems with many degrees of freedom.