# Lecture: Hydrodynamics from Kinetic Theory

Let me give you a proper lecture on these sections, with all the mathematical details.

---

## Introduction: What are we trying to do?

We want to describe how a gas evolves toward equilibrium using the **Boltzmann equation**. Instead of tracking every single molecule, we'll describe the gas using macroscopic fields:

- **Density**: $\rho(\mathbf{r}, t)$ or $n(\mathbf{r}, t)$
- **Velocity**: $\mathbf{u}(\mathbf{r}, t)$
- **Temperature**: $T(\mathbf{r}, t)$

The strategy is to solve the Boltzmann equation perturbatively, order by order.

---

## Section 3.8: Zeroth-Order Hydrodynamics

### The Zeroth-Order Distribution

At zeroth order, we assume the gas is **locally** in equilibrium. This means at each point in space, the velocity distribution looks like a Maxwell-Boltzmann distribution, but the parameters (density, temperature, bulk velocity) can vary from point to point:

$$f_1^0(\mathbf{p}, \mathbf{q}, t) = n(\mathbf{q}, t) \left(\frac{m}{2\pi k_B T(\mathbf{q}, t)}\right)^{3/2} \exp\left(-\frac{m\mathbf{c}^2}{2k_B T(\mathbf{q}, t)}\right)$$

where $\mathbf{c} = \mathbf{p}/m - \mathbf{u}(\mathbf{q}, t)$ is the **peculiar velocity** (velocity in the local rest frame).

This is called the "local equilibrium distribution" because at each point, it has the equilibrium form, just with space-and-time-dependent parameters.

### Why does this satisfy the collision term?

The collision integral on the right-hand side of the Boltzmann equation vanishes for any Maxwellian distribution:

$$C[f_1^0, f_1^0] = 0$$

This is because collisions conserve energy and momentum - a Maxwellian already maximizes entropy subject to these constraints, so collisions don't change it.

### The Hydrodynamic Equations

Since $f_1^0$ satisfies the collision term, the Boltzmann equation becomes:

$$\left(\partial_t + \frac{\mathbf{p}}{m} \cdot \nabla_{\mathbf{q}} + \mathbf{F} \cdot \nabla_{\mathbf{p}}\right) f_1^0 = 0$$

We can extract equations for $n$, $\mathbf{u}$, and $T$ by taking **moments** of this equation (multiplying by 1, $\mathbf{p}$, and $p^2$, then integrating over momentum).

For small deviations from uniform equilibrium, the linearized equations are:

$$\boxed{\begin{cases} \partial_t \rho = -n\nabla \cdot \mathbf{u} \ m\partial_t \mathbf{u} = -k_B T \nabla \rho - k_B \rho \nabla T \ \partial_t T = -\frac{2}{3}T \nabla \cdot \mathbf{u} \end{cases}} \quad \text{(Eq. 3.101)}$$

**Physical interpretation:**

1. First equation: continuity (mass conservation)
2. Second equation: Newton's law with pressure gradient force
3. Third equation: adiabatic heating/cooling from compression/expansion

### Finding Normal Modes

To find the natural vibration patterns, we Fourier transform in space and time:

$$\tilde{A}(\mathbf{k}, \omega) = \int d^3q , dt , e^{i(\mathbf{k} \cdot \mathbf{q} - \omega t)} A(\mathbf{q}, t)$$

This converts the PDEs into an eigenvalue problem:

$$\omega \begin{pmatrix} \tilde{\rho} \ \tilde{\mathbf{u}} \ \tilde{T} \end{pmatrix} = \begin{pmatrix} 0 & n\mathbf{k} & 0 \ \frac{k_B T}{mn}\mathbf{k} & 0 & \frac{k_B}{m}\mathbf{k} \ 0 & \frac{2}{3}T\mathbf{k} & 0 \end{pmatrix} \begin{pmatrix} \tilde{\rho} \ \tilde{\mathbf{u}} \ \tilde{T} \end{pmatrix}$$

### The Normal Modes

Let me solve this system explicitly. The eigenvalues $\omega$ give us the mode frequencies.

#### **(a) Transverse (Shear) Modes**

For velocity components perpendicular to $\mathbf{k}$:

$$\mathbf{k} \cdot \tilde{\mathbf{u}}_T = 0$$

From the matrix equation, we see that $\partial_t \tilde{\mathbf{u}}_T = 0$, so:

$$\boxed{\omega_T = 0}$$

**Physical meaning:** Shear flows (layers sliding past each other) persist forever with no damping! This is clearly unphysical - we know viscosity should damp these.

#### **(b) Isobaric (Constant Pressure) Mode**

There's an eigenvector with $\omega = 0$:

$$\mathbf{v}_e = \begin{pmatrix} n \ 0 \ -T \end{pmatrix}$$

This represents variations where $\delta(nT) = 0$, meaning pressure $P = nk_B T$ stays constant. Since there's no pressure gradient, the fluid doesn't accelerate.

$$\boxed{\omega_e = 0}$$

#### **(c) Longitudinal Sound Modes**

For velocity parallel to $\mathbf{k}$, we get coupled oscillations of $\rho$, $u_L$, and $T$:

$$\mathbf{v}_{\pm} = \begin{pmatrix} nk \ \pm\omega k \ \frac{2}{3}Tk \end{pmatrix}$$

where the eigenfrequency satisfies:

$$\omega^2 = \frac{5k_B T}{3m} k^2 = v^2 k^2$$

with sound speed:

$$\boxed{v = \sqrt{\frac{5k_B T}{3m}} = \sqrt{\frac{5}{3}\frac{k_B T}{m}}}$$

So we have:

$$\boxed{\omega_{\pm} = \pm v k}$$

**Physical meaning:** Sound waves propagate without damping! Also unphysical.

**Check on entropy:** In these modes, $\delta(\ln(nT^{-3/2})) = 0$, meaning they're **adiabatic** (no entropy change).

### The Problem with Zeroth Order

**None of the modes relax to equilibrium!**

- Shear flows never stop
- Sound never decays
- Entropy variations never smooth out

This is because we haven't included **dissipation** (viscosity and heat conduction). We need a better approximation.

---

## Section 3.9: First-Order Hydrodynamics

### The Strategy

We know $f_1^0$ satisfies the collision term but _not_ the full Boltzmann equation. The left-hand side operator is:

$$\mathcal{L}f \equiv \left(\partial_t + \frac{\mathbf{p}}{m} \cdot \nabla + \mathbf{F} \cdot \nabla_{\mathbf{p}}\right) f = D_t f + \mathbf{c} \cdot \nabla f + \frac{\mathbf{F}}{m} \cdot \nabla_{\mathbf{c}} f$$

where $D_t = \partial_t + \mathbf{u} \cdot \nabla$ is the convective derivative.

### Computing $\mathcal{L} \ln f_1^0$

This is a key calculation. Starting from:

$$\ln f_1^0 = \ln(nT^{-3/2}) - \frac{mc^2}{2k_B T} + \text{const}$$

After applying $\mathcal{L}$ and using the zeroth-order hydrodynamic equations to simplify, we get:

$$\boxed{\mathcal{L} \ln f_1^0 = \frac{m}{k_B T}\left[\left(\mathbf{c}\mathbf{c} - \frac{\mathbb{1}}{3}c^2\right):\nabla\mathbf{u}\right] + \left(\frac{mc^2}{2k_B T} - \frac{5}{2}\right)\frac{\mathbf{c} \cdot \nabla T}{T}}$$

**Physical interpretation:**

- First term: responds to **velocity gradients** (shear and compression)
- Second term: responds to **temperature gradients**

### The Single Collision Time Approximation

The linearized collision operator is complicated, so we approximate:

$$C_L[g] \approx \frac{g}{\tau_\times}$$

where $\tau_\times$ is the mean collision time.

From the linearized Boltzmann equation $\mathcal{L}f_1^0 = -f_1^0 C_L[g]$, we get:

$$g = -\tau_\times \frac{1}{f_1^0} \mathcal{L}f_1^0 \approx -\tau_\times \mathcal{L} \ln f_1^0$$

### The First-Order Distribution

Substituting our expression for $\mathcal{L} \ln f_1^0$:

$$\boxed{f_1^1(\mathbf{p}, \mathbf{q}, t) = f_1^0(\mathbf{p}, \mathbf{q}, t) \left[1 - \frac{\tau_\mu m}{k_B T}\left(\mathbf{c}\mathbf{c} - \frac{\mathbb{1}}{3}c^2\right):\nabla\mathbf{u} - \tau_K \left(\frac{mc^2}{2k_B T} - \frac{5}{2}\right)\frac{\mathbf{c} \cdot \nabla T}{T}\right]}$$

where $\tau_\mu$ and $\tau_K$ are both $\sim \tau_\times$ (equal in the simple approximation).

### Computing Transport Coefficients

Now we calculate the **stress tensor** and **heat flux** using this corrected distribution.

#### **Pressure Tensor (Stress Tensor)**

$$P_{\alpha\beta}^1 = nm\langle c_\alpha c_\beta \rangle_1$$

Using Wick's theorem for Gaussian averages and keeping first-order terms:

$$P_{\alpha\beta}^1 = nk_B T \delta_{\alpha\beta} - 2nk_B T \tau_\mu \left(\frac{\partial u_\alpha}{\partial x_\beta} + \frac{\partial u_\beta}{\partial x_\alpha} - \frac{2}{3}\delta_{\alpha\beta}\nabla \cdot \mathbf{u}\right)$$

The off-diagonal terms give us **viscous stress**:

$$\boxed{P_{\alpha\beta}^1 = P\delta_{\alpha\beta} - \eta\left(\frac{\partial u_\alpha}{\partial x_\beta} + \frac{\partial u_\beta}{\partial x_\alpha} - \frac{2}{3}\delta_{\alpha\beta}\nabla \cdot \mathbf{u}\right)}$$

where the **viscosity coefficient** is:

$$\boxed{\eta = nk_B T \tau_\mu}$$

#### **Heat Flux**

$$\mathbf{h}_1 = n\left\langle \mathbf{c} \frac{mc^2}{2}\right\rangle_1$$

Calculating with the first-order distribution:

$$\mathbf{h}_1 = -\frac{5}{2}\frac{nk_B^2 T \tau_K}{m}\nabla T$$

This is **Fourier's law of heat conduction**:

$$\boxed{\mathbf{h} = -\kappa \nabla T}$$

where the **thermal conductivity** is:

$$\boxed{\kappa = \frac{5nk_B^2 T \tau_K}{2m}}$$

### Physical Significance

We now have:

- **Viscosity** $\eta$: opposes shear flows
- **Thermal conductivity** $\kappa$: smooths temperature gradients

These are **dissipative** mechanisms that will cause relaxation to equilibrium.

### Modified Hydrodynamic Equations

The equations of motion now include these transport coefficients:

**Momentum equation:** $$m\partial_t \mathbf{u} = -\nabla P + \eta\left(\nabla^2\mathbf{u} + \frac{1}{3}\nabla(\nabla \cdot \mathbf{u})\right)$$

**Energy equation:** $$\frac{3}{2}nk_B\partial_t T = -\nabla \cdot \mathbf{h} = \kappa \nabla^2 T$$

### First-Order Normal Modes

The Fourier-transformed matrix equation becomes:

$$\omega \begin{pmatrix} \tilde{\rho} \ \tilde{\mathbf{u}} \ \tilde{T} \end{pmatrix} = \begin{pmatrix} 0 & n\mathbf{k} & 0 \ \frac{k_B T}{mn}\mathbf{k} & -i\frac{\eta}{mn}\left(k^2\mathbb{1} + \frac{\mathbf{k}\mathbf{k}}{3}\right) & \frac{k_B}{m}\mathbf{k} \ 0 & \frac{2}{3}T\mathbf{k} & -i\frac{2\kappa k^2}{3nk_B} \end{pmatrix} \begin{pmatrix} \tilde{\rho} \ \tilde{\mathbf{u}} \ \tilde{T} \end{pmatrix}$$

Notice the **imaginary terms** on the diagonal - these produce damping!

#### **Transverse Modes (Shear Waves)**

For $\mathbf{k} \cdot \tilde{\mathbf{u}}_T = 0$:

$$\boxed{\omega_T = -i\frac{\eta}{mn}k^2}$$

**Interpretation:**

- Imaginary frequency means **exponential decay**, not oscillation
- Decay rate $\gamma = (\eta/mn)k^2 \propto k^2$
- Characteristic time $\tau \sim \lambda^2/\nu$ where $\nu = \eta/mn$ is **kinematic viscosity**
- This is **diffusive** behavior (time $\propto$ length$^2$)

#### **Longitudinal Modes (Sound + Entropy)**

For $\mathbf{u} \parallel \mathbf{k}$, we have three coupled modes.

**Isobaric (entropy) mode:** $$\boxed{\omega_e = -i\frac{2\kappa k^2}{5nk_B}}$$

This is **thermal diffusion** of temperature variations.

**Sound modes:** $$\boxed{\omega_{\pm} = \pm vk - i\Gamma k^2}$$

where the **damping coefficient** is:

$$\Gamma = \frac{k^2}{2}\left(\frac{2\eta}{3mn} + \frac{2\kappa}{15nk_B}\right)$$

**Interpretation:**

- Sound waves still oscillate at frequency $\sim vk$
- But now they decay with rate $\propto k^2$
- The damping has two contributions: viscous and thermal

### Summary: What Did We Achieve?

**Zeroth order:**

- Local equilibrium assumption
- No dissipation
- Modes don't relax (unphysical)

**First order:**

- Small corrections to local equilibrium
- Introduces viscosity $\eta$ and thermal conductivity $\kappa$
- All modes now decay/diffuse
- System relaxes to global equilibrium ✓

**The key insight:** Deviations from local equilibrium, driven by gradients in velocity and temperature, create dissipative fluxes (viscous stress and heat flow) that restore equilibrium. This is the microscopic origin of irreversibility in gases!

---

Does this help clarify the structure and physics? Would you like me to elaborate on any particular calculation?