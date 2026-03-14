---
sticker: lucide//newspaper
---
# **Bondi-Sachs Formalism in General Relativity**

## **Introduction**

The Bondi-Sachs formulation of general relativity is naturally adapted to null surfaces, making it ideal for studying gravitational waves and asymptotic properties at null infinity ($\mathcal{I}^+$). The Einstein field equations split into three categories in this formalism:

1. **Hypersurface Equations**: These determine $\beta$, $U$, and $W_c$ at each step.
    
2. **Evolution Equations**: These govern the evolution of the angular components of the metric ($J$).
    
3. **Constraint Equations**: These relate data between different slices and ensure the correct propagation of constraints.
    

## **World-Tube and the Evolution Problem**

A **world-tube** $\Gamma$ is a timelike or null 3-surface that serves as an **inner boundary** of the computational domain. It is crucial in characteristic evolution schemes because:

- It provides **boundary conditions** for the evolution.
    
- It can represent the **surface of a star**, the **apparent horizon of a black hole**, or any other physically meaningful boundary in the system.
    

The computational domain extends **from $\Gamma$ to null infinity ($\mathcal{I}^+$)**, where we extract radiation.

### **Coordinate Compactification**

To handle the infinite extent of the physical radial coordinate $r$, a transformation such as

is applied. This maps:

- $r = 0$ (the world-tube) to $x = 0$.
    
- $r = \infty$ (null infinity) to $x = 1$.
    

This **compactifies** the numerical domain to a finite range, ensuring that **null infinity is included in the computational grid**.

## **Derivation of Key Equations**

### **(i) Hypersurface Equations**

These determine the metric quantities $\beta$, $U$, and $W_c$ at each step.

1. **Equation for $\beta$ (Surface Warping Function):** where $\mathcal{F}$ is an expression involving derivatives of the metric.
    
2. **Equation for $U$ (Angular Shift Function):** This governs the angular shift vector.
    
3. **Equation for $W_c$ (Bondi-Sachs Radial Coordinate Correction):**
    

These equations are solved radially **outward** from the world-tube at fixed $u$.

### **(ii) Evolution Equation for $J$**

Once the hypersurface quantities are determined, the evolution equation for the shear variable $J$ is solved:

This equation is similar to a wave equation, showing how gravitational radiation propagates outward.

### **(iii) Constraint Equations**

The constraint equations involve $R_{0\alpha}$, ensuring consistency of the evolution. They are checked at every step to verify stability and correctness.

## **Computational Algorithm for Solving the Bondi-Sachs System**

### **Step 1: Initialization**

- Set up an initial data slice $u = 0$ with prescribed values for $J$.
    
- Choose initial boundary values on the world-tube $\Gamma$.
    

### **Step 2: Solve Hypersurface Equations Radially**

For each fixed $u$, solve **radially outward** in $r$:

1. Solve $\beta$ from $R_{11} = 0$.
    
2. Solve $U^A$ from $q^A R_{1A} = 0$.
    
3. Solve $W_c$ from $h^{AB} R_{AB} = 0$.
    

### **Step 3: Solve the Evolution Equation**

- Use the evolution equation $q^A q^B R_{AB} = 0$ to compute $J$ at the next time step $u + \Delta u$.

### **Step 4: Apply Constraint Checks**

- Verify that $R_{0\alpha} = 0$ is satisfied to ensure numerical consistency.

### **Step 5: Compactification Handling**

- Implement the radial compactification transformation $r \rightarrow x$.
    
- Ensure regularity conditions at $x = 1$ (null infinity).
### **Step 6: Iterate for the Next Time Step**

- Repeat from Step 2 for $u \to u + \Delta u$.


# Deriving Bond-Sachs Equations from Einstein Equations
I'll help derive the Bondi-Sachs equations step by step. This is a complex derivation that requires careful attention to coordinate choices and gauge conditions.

1) First, let's establish the Bondi-Sachs metric in its standard form:

$$ ds^2 = -\left(\frac{V}{r}e^{2\beta} - r^2h_{AB}U^AU^B\right)du^2 - 2e^{2\beta}dudr - 2r^2h_{AB}U^Bdudx^A + r^2h_{AB}dx^Adx^B $$

where:
- $u$ is the retarded time coordinate
- $r$ is the luminosity distance
- $x^A$ represents angular coordinates $(θ,φ)$
- $h_{AB}$ is the metric on the unit 2-sphere
- $β$, $V$, and $U^A$ are metric functions

2) The determinant condition for the angular metric:

$$ \det(h_{AB}) = \det(q_{AB}) $$

where $q_{AB}$ is the standard metric on the unit 2-sphere.

3) Now, let's write out the Einstein tensor components. The key components are:

$$ G_{uu} = -\frac{1}{r^2}(V - r) + ... $$
$$ G_{ur} = -\frac{2}{r^2}β_{,r} + ... $$
$$ G_{uA} = \frac{1}{r}(U^B_{|B} - 2β_{,A}) + ... $$

where $|$ denotes covariant differentiation with respect to $h_{AB}$.

4) The hypersurface equations come from:

$$ R_{rr} = 8π(T_{rr} - \frac{1}{2}g_{rr}T) $$
$$ R_{rA} = 8π(T_{rA} - \frac{1}{2}g_{rA}T) $$

5) The evolution equations arise from:

$$ R_{uA} = 8π(T_{uA} - \frac{1}{2}g_{uA}T) $$

6) The constraint equations are:

$$ R_{uu} = 8π(T_{uu} - \frac{1}{2}g_{uu}T) $$

7) After substituting the metric components and performing a lengthy calculation, we get the main Bondi-Sachs equations:

For β:
$$ β_{,r} = \frac{r}{16}h_{AC}h_{BD}(h_{AB,r}h_{CD,r}) + 4πrT_{rr} $$

For $U^A$:
$$ (r^4e^{-2β}h_{AB}U^B_{,r})_{,r} = 16πr^2T_{rA} + ... $$

For $V$:
$$ V_{,r} = e^{2β}(1 - M_{,r}) + ... $$

where M is the mass aspect.

8) The evolution equation for the angular metric:

$$ \partial_u h_{AB} = \frac{1}{2}r^{-2}e^{-2β}V(h_{AB,r}r - 2h_{AB}) - (D_AU_B + D_BU_A) $$

where $D_A$ is the covariant derivative on the unit 2-sphere.

9) For numerical implementation, it's useful to introduce the following variables:

$$ J = q_{AC}h_{CB}dx^Adx^B $$
$$ K = \sqrt{\det(h_{AB})/\det(q_{AB})} $$
$$ β = β $$
$$ W = V/r $$
$$ U^A = U^A $$

10) This gives us a hierarchical system:

a) Hypersurface equations:
$$ β_{,r} = F_β(J, K) $$
$$ (r^2Q)_{,r} = F_Q(J, K, β) $$
$$ U^A_{,r} = F_U(J, K, β, Q) $$
$$ W_{,r} = F_W(J, K, β, Q, U^A) $$

b) Evolution equations:
$$ \partial_u J = F_J(J, K, β, Q, U^A, W) $$
$$ \partial_u K = F_K(J, K, β, Q, U^A, W) $$

11) The final system can be written in first-order form:

$$ \partial_r \vec{v} = \vec{F}(\vec{v}, r) $$
$$ \partial_u \vec{w} = \vec{G}(\vec{v}, \vec{w}, r) $$

where $\vec{v}$ contains hypersurface variables and $\vec{w}$ contains evolution variables.

This system is suitable for numerical implementation using standard methods for hyperbolic PDEs, typically using finite difference schemes in the radial direction and spectral methods for angular derivatives.

Would you like me to elaborate on any particular aspect of this derivation or discuss specific numerical implementation strategies?