# Solutions to Differential Forms and Maxwell Equations Problems

## Problem 1: Dimension of p-forms on n-dimensional Vector Space

**Topic:** The space of differential forms on an $n$-dimensional vector space has a well-defined dimension determined by binomial coefficients.

A $p$-form on an $n$-dimensional vector space is an alternating multilinear map that takes $p$ vectors and returns a scalar. The basis of the space of $p$-forms is given by wedge products of the dual basis $1$-forms: $dx^{i_1} \wedge dx^{i_2} \wedge \cdots \wedge dx^{i_p}$ where $i_1 < i_2 < \cdots < i_p$.

Since we must choose $p$ distinct indices from $n$ available indices, the number of such basis elements is the binomial coefficient:

$$\text{dim}(\Lambda^p) = \binom{n}{p} = \frac{n!}{p!(n-p)!}$$

Each choice of $p$ indices gives one linearly independent basis $p$-form. Any $p$-form can be expressed as a linear combination of these basis elements with constant coefficients. Therefore, the space of linearly independent $p$-forms on an $n$-dimensional vector space has dimension $\frac{n!}{p!(n-p)!}$.

---

## Problem 2: Nilpotency of the Exterior Derivative

**Topic:** The exterior derivative operator satisfies $d^2 = 0$, a fundamental property in differential geometry.

Consider a $p$-form $A$ with components $A_{\mu_1 \cdots \mu_p}$. The exterior derivative is defined as:

$$dA = (p+1)\partial_{[\mu_1} A_{\mu_2 \cdots \mu_{p+1}]} dx^{\mu_1} \wedge \cdots \wedge dx^{\mu_{p+1}}$$

To show $d(dA) = 0$, we compute the exterior derivative of a $(p+1)$-form:

$$(d(dA))_{\nu \mu_1 \cdots \mu_{p+1}} = (p+2)\partial_{[\nu} (dA)_{\mu_1 \cdots \mu_{p+1}]}$$

Substituting the expression for $(dA)$:

$$(d(dA))_{\nu \mu_1 \cdots \mu_{p+1}} = (p+2)(p+1)\partial_{[\nu} \partial_{\mu_1} A_{\mu_2 \cdots \mu_{p+1}]}$$

The double sum over antisymmetrized indices yields terms like $\partial_\nu \partial_{\mu_1} A_{\mu_2 \cdots \mu_{p+1}]}$. Since partial derivatives commute for smooth functions, $\partial_\nu \partial_{\mu_1} = \partial_{\mu_1} \partial_\nu$, each term appears twice with opposite signs in the antisymmetrization. Therefore:

$$d(dA) = 0$$

This is a fundamental property that ensures consistency of Maxwell equations and cohomology theory.

---

## Problem 3: Hodge Dual and Vector Calculus Identities in 3D

**Topic:** In three-dimensional Euclidean space, the Hodge dual operation translates between differential forms and vector calculus operations.

**Part a) Curl as Hodge dual of exterior derivative:**

Let $A$ be a 1-form (identified with a vector field in 3D). The exterior derivative $dA$ is a 2-form:

$$dA = \left(\frac{\partial A_j}{\partial x^i} - \frac{\partial A_i}{\partial x^j}\right) dx^i \wedge dx^j$$

The Hodge dual maps 2-forms to 1-forms in 3D. Applying $\ast$ to $dA$:

$$\ast(dA) = (\nabla \times A)_k dx^k$$

where the components of the curl are $(\nabla \times A)_k = \epsilon_{kij} \frac{\partial A_j}{\partial x^i}$. This follows from the definition of the Hodge dual, which converts the 2-form basis elements using the Levi-Civita symbol. Thus:

$$\ast dA = \nabla \times A$$

This shows that the curl operator is represented as the composition of exterior derivative and Hodge dual.

**Part b) Divergence as composition of operations:**

Let $A$ be a 1-form. The dual $\ast A$ is a 2-form in 3D. Taking the exterior derivative:

$$d(\ast A) = \text{a 3-form}$$

Applying the Hodge dual to this 3-form (which maps to 0-forms in 3D):

$$\ast(d(\ast A)) = \nabla \cdot A$$

Therefore:

$$\ast d \ast A = \nabla \cdot A$$

This identity shows that the divergence is obtained by the composition $\ast d \ast$ applied to a 1-form, which is the codifferential operator in differential geometry.

---

## Problem 4: Maxwell Equations in Differential Form Language

**Topic:** The four Maxwell equations can be elegantly expressed using differential forms and the exterior derivative, revealing the underlying geometric structure.

**Part a) Homogeneous Maxwell equations:**

The homogeneous Maxwell equations (in vacuum with no sources) are:

$$\nabla \cdot B = 0 \quad \text{and} \quad \nabla \times E + \frac{\partial B}{\partial t} = 0$$

The electromagnetic field is encoded in the 2-form $F$:

$$F = E_i dx^i \wedge dx^0 + \frac{1}{2}B_k \epsilon_{kij} dx^i \wedge dx^j$$

where $x^0 = ct$ is the time coordinate. Computing the exterior derivative of $F$:

$$dF = \partial_\mu F_{\nu\rho} dx^\mu \wedge dx^\nu \wedge dx^\rho$$

The condition $\nabla \cdot B = 0$ corresponds to the vanishing of certain components, while $\nabla \times E + \partial_t B = 0$ corresponds to others. The statement that these homogeneous equations hold is equivalent to:

$$dF = 0$$

This compact form automatically encodes both Gauss's law for magnetism and Faraday's law.

**Part b) Non-homogeneous Maxwell equations:**

The inhomogeneous Maxwell equations include sources:

$$\nabla \cdot E = \rho \quad \text{and} \quad \nabla \times B - \frac{\partial E}{\partial t} = J$$

The current 1-form is defined as $J = \rho dx^0 + J_i dx^i$. The Hodge dual of $F$ is another 2-form:

$$\ast F = -B_i dx^i \wedge dx^0 + \frac{1}{2}E_k \epsilon_{kij} dx^i \wedge dx^j$$

Taking the exterior derivative and applying the Hodge dual to obtain a 1-form:

$$\ast(d(\ast F)) = \text{(related to sources)}$$

The complete statement of the inhomogeneous Maxwell equations is:

$$d \ast F = \ast J$$

This equation encodes Gauss's law ($\nabla \cdot E = \rho$) and the Ampère-Maxwell law, demonstrating the geometric elegance of electromagnetic theory expressed through differential forms.