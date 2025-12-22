# Introduction

***Thermodynamics is a phenomenological description of properties of macroscopic systems in thermal equilibrium***

Analogical to how success was gained by classical mechanics, if one were to describe the behavior of systems such as a container of gas, one would proceed by:

1. **Idealizing the System**
	We would first idealize the system as much as possible. The concept of the mechanical work on the system is certainly familiar, yet there appear to be complications due to exchange of heat. The solution is first to examine closed systems, insulated by adiabatic walls that don't allow any exchange of heat with the surroundings. 
2. **State Coordinates**
	 As the state of a point particle is quantified by its coordinates (and momenta), properties of the macroscopic system can also be described by a number of *thermodynamic* coordinates or *state functions*. The most familiar coordinates are those that relate to mechanical work. Quantities such as pressure, volume, electric field, etc. There are also state functions that are not related to mechanical work (which we'll see later). 
	 The state functions are well defined only when the system is in equilibrium, that is, when its properties do not change appreciably with time over the intervals of interest.
 3. **Laws of Thermodynamics**
	 Lastly, the relationship between the state function is described by the laws of thermodynamics. As a phenomenological description, these laws are based on a number of empirical observations. A coherent logical and mathematical structure is then constructed on the basis of these observations, which leads to a variety of useful concepts, and to testable relationships among various quantities. The laws of thermodynamics can only be justified by a more fundamental (microscopic) theory of nature. For example, statistical mechanics attempts to obtain these laws starting from classical or quantum mechanical equations for the evolution of collections of particles.
# The Zeroth Law

The zeroth law of thermodynamics describes the transitive nature of thermal equilibrium.

***If two systems, $A$ and $B$, are separately in equilibrium with a third system $C$, then they are also in equilibrium with one another.***

This law looks very simple, but it has a great implication. It implies the existence of an important state function, the empirical temperature $\Theta$, such that systems in equilibrium are are the same temperature.

![[Pasted image 20251121191250.png]]

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

# The First Law

In dealing with simple mechanical systems, conservation of energy is an important principle. Observations indicate that a similar principle operates at the level of macroscopic bodies *provided that the system is properly insulated*, that is, when that only sources of energy are mechanical origin. We shall use the following formulation of these observations:

***The amount of work required to change the state of an otherwise adiabatically isolated system depends only on the initial and final states, and not on the means by which the work is performed, or on the intermediate stages through which the system passes***

![[Pasted image 20251121191234.png]]

This as we all know holds for a particle in a potential. Similarly, for the thermodynamic system we can construct another state function, the internal energy $E(X)$. Up to a constant, $E(X)$ can be obtained from the amount of work $\Delta W$ needed for an adiabatic transformation from an initial state to a final state:

$$
\Delta W = E(X_f)- E(X_i)
$$
Another observation is that if we drop the adiabatic constraint this equation doesn't hold anymore. The difference:

$$
\Delta Q  = \Delta E - \Delta W
$$
is defined as the *heat intake* of the system from its surroundings. Clearly, in such transformation $\Delta Q$ and $\Delta W$ are not separately functions of state in that they depend on the external factors such as the means of applying work, and not only on the final states. 

To emphasize this, for a differential transformation we write:

$$
\bar d Q = dE -\bar d W
$$
where $dE = \sum_i \partial_i EdX_i$ can be obtained by differentiation, while $\bar dQ$ and $\bar d W$ generally cannot. Also note that our convention is such that the signs of work and heat indicate the energy added to the system, and not vice versa. The first law of thermodynamics thus states that:

***To change the state of a system we need a fixed amount of energy, which can be in the form of mechanical work or heat.***

A **Quasi-Static*** transformation is one that is performed sufficiently slowly so that the system is always in equilibrium. Thus at any stage of the process, the thermodynamic coordinates of the system exist and can in principle be computed.


One can typically divide the state function into a set of generalized displacements, and their conjugate generalized forces, such that for an infinitesimal quasi-static transformation

$$
\bar d W  =\sum_i J_i dx_i
$$
| System            |          Force           |        Displacement |
| :---------------- | :----------------------: | ------------------: |
| Wire              |       tension $F$        |          length $L$ |
| Film              |   surface tension $S$    |            area $A$ |
| Fluid             |      pressure $-P$       |          volume $V$ |
| Magnet            |    magnetic field $H$    |   magnetization $M$ |
| Dielectric        |    electric field $E$    |    polarization $P$ |
| Chemical reaction | chemical potential $\mu$ | particle number $N$ |

The displacements are usually extensive quantities, that is, proportional to system size, while the forces are intensive and independent of size. The latter are indicators of equilibrium. As discussed in connection with the zeroth law, temperature plays a similar role when heat exchanges are involved. Is there a corresponding displacement, and if so what is it?

*the ideal gas*: we noted in connection with the zeroth law that the equation of state of the ideal gas takes a particularly simple form, $PV\propto T$. The internal energy of the ideal gas also takes a very simple form.

As observed by  *Joule's free expansion*: measurements indicate that if an ideal gas expands adiabatically (but not necessarily quasi-statically), from a volume $V_i$ to $V_f$, the initial and final temperatures are the same. As the transformation is adiabatic ($\Delta Q = 0$) and there is no external work done on the system ($\Delta W = 0$), the internal energy of the gas is unchanged.

Since the pressure and volume of the gas change in the process, but its temperature does not, we conclude that the internal energy depends only on temperature, that is, $E(V,T)=E(T)$. This property of the ideal gas is in fact a consequence of the form of its equation of state.

“Response functions are the usual method for characterizing the macroscopic behavior of a system. They are experimentally measured from the changes of thermodynamic coordinates with external probes. Some comm“

Heat capacities are obtained from the change in temperature upon addition of heat to the system.” ([Kardar, p. 8](zotero://select/library/items/M9RXQI74)) ([pdf](zotero://open-pdf/library/items/WDMIC9R3?page=20&annotation=QSBAFBWE))on response functions are as follows.” ([Kardar, p. 8](zotero://select/library/items/M9RXQI74)) ([pdf](zotero://open-pdf/library/items/WDMIC9R3?page=20&annotation=BHL8W7YH))

Since heat is not a function of state, the path by which it is applied should also be specified. For a gas we can calculate the heat capacities in constant volume and in constant pressure:

$$
\begin{align}
C_v &= \left.\frac{\bar d  Q}{dT}\right\vert_V \\ 
&= \left.\frac{dE - \bar dW}{dT}\right\vert_V \\
&= \left.\frac{\partial E}{\partial T}\right\vert_V
\end{align}
$$

Force constants measure the (infinitesimal) ratio of displacement to force and are generalizations of the spring constant.

Thermal responses probe the change in the thermodynamic coordinates with temperature.

# The Second Law

The practical impetus for development of the science of thermodynamics in the nineteenth century was the advent of heat engines. An idealize heat engine works by taking in a certain amount of heat $Q_H$, from a heat source, converting a portion of it to work $W$, and dumping the remaining heat $Q_C$ into a heat sink. The efficiency of the engine is calculated from:

$$
\eta = \frac{W}{Q_H} = \frac{Q_H - Q_C}{Q_H} \leq 1
$$
An idealize refrigerator is like an engine running backward, that is, using work $W$ to extract $Q_C$ from a cold system, and dumping heat $Q_H$ at a higher temperature. We can similarly define a figure of merit for the performance of a refrigerator as:

$$
\omega = \frac{Q_C}{W} = \frac{Q_C}{Q_H-Q_C}
$$

![[Pasted image 20251122113446.png]]

The first law rules out so-called "*perpetual motion machines of the first kind*", that is, engines that produce work without consuming any energy. However, the conservation of energy is not violated by and engine that produces work by converting water to ice. Such a "*perpetual motion machine of the second kind*" would certainly solve the world's energy problems, but is ruled out by the second law of thermodynamics. 

the observation that the natural direction for the flow of heat is from hotter to colder bodies is the essence of the second law of thermodynamics. There is a number of different formulations of the second law, two are the below statements:

- ***Kelvin's Statement:** No process is possible whose sole result is the complete conversion of heat into work*.
- **Clausius's Statement:** No process is possible whose sole result is the transfer of heat from a colder to hotter body*.

A perfect engine is ruled out by the first statement, a perfect refrigerator by the second. Since we shall use both statements, we first show that they are equivalent.


# Carnot Engines

*A Carnot Engine is any engine that is reversible, runs in a cycle, with all of its heat exchanges taking place at a source temperature $T_H$ and a sink temperature $T_C$*.

![[Pasted image 20251122114236.png]]

A reversible process is one that can be run backward in time by simply reversing its inputs and outputs. It is the thermodynamics equivalent of frictionless motion in mechanics. An engine that runs in cycle returns to its original internal state at the end of the process. 

***The distinguishing characteristic of the Carnot engine is that heat exchanges with the surroundings are carried out only at two temperatures.***

The zeroth law allows us to select two isotherms at temperatures $T_H$ and $T_C$ for these heat exchanges. **To complete the Carnot cycle we have to connect these isotherms by reversible adiabatic paths in the coordinate space.**

Since heat is not a function of state, we don't know how to construct such paths in general. Fortunately, we have sufficient information at this point to construct a Carnot engine using an ideal gas as its internal working substance. For the purpose of demonstration, let us compute the adiabatic curves for a monatomic ideal gas with an internal energy:

$$
E= \frac23 Nk_B T = \frac32 PV
$$

Along a quasi-static path:

$$
\bar d Q = dE - \bar dW= d(\frac32 PV) + PdV = \frac52 PdV + \frac32 VdP
$$
The adiabatic condition $\bar d Q = 0$, then implies a path:

$$
\frac{dP}{P} + \frac53 \frac{dV}{V} = 0 \Rightarrow PV^\gamma = \text{constant}
$$

with $\gamma = 5/3$.


![[Pasted image 20251122121713.png]]

The adiabatic curves are clearly distinct from the isotherms, and we can select two such curves to intersect out isotherms, thereby completing a Carnot cycle. The assumption of $E\propto T$ is not necessary. In fact, a similar construction is possible for any two-parameter system with $E(J, x)$ 

**Carnot's Theorem:** *No engine operating between two reservoirs (at temperatures $T_H$ and $T_C$) is more efficient than a Carnot engine operating between them.*

Since a Carnot engine is reversible, it can be run backward as a refrigerator. User the non-Carnot engine to run the Carnot engine backward. Let us denote the heat exchange of the non-Carnot and Carnot engines by $Q_H, Q_C$ and $Q_H', Q_C'$, respectively. The net effect of the two engines is to transfer heat equal to $Q_H-Q_H' = Q_C - Q_C'$ from $T_H$ to $T_C$.

According to Calusius's statement, the quantity of transferred heat cannot be negative, that is $Q_H\geq Q_H'$. Since the same quantity of work $W$ is involved (since we're looking for efficiency), in this process, we can conclude that:

$$
\frac{W}{Q_H} \leq \frac{W}{Q_H'} \Longrightarrow \eta_{\text{Carnot}} \geq\eta_{\text{non-Carnot}}.
$$
![[Pasted image 20251217081032.png]]

**Corollary** All reversible engines have the same universal efficiency $\eta(T_H, T_C)$, since each can be used to run any other one backward.

- *Thermodynamic Temperature Scale:* as shown earlier, it is at least theoretically possible to construct a Carnot engine using an ideal gas (or any other two-parameter system) as working substance. Independent of the material used, and design and construction, all such cyclic and reversible engines have the same maximum theoretical efficiency

Since this maximum efficiency is only dependent on the two temperatures, it can be used to construct a temperature scale. Such temperature scale has the attractive property of being independent of the properties of any material. To construct such a scale we first obtain a constraint on the form of $\eta(T_H, T_C)$. 

### Making the Constraints

Consider two Carnot engines running in series, on between temperatures $T_1$ and $T_2$ and the other between $T_2$ and $T_3$ where:

$$
T_1 > T_2 > T_3
$$

Using the universal efficiency, the three heat exchanges are related by:

$$
\begin{cases}
Q_2 = Q_1 - W_{12} = Q_1 [1 - \eta(T_1,T_2)] \\
Q_3 =Q_2 - W_{23} = Q_2 [1-\eta(T_2,T_3)] =  Q_1 [1 - \eta(T_1,T_2)] [1-\eta(T_2,T_3)]\\
Q_3 = Q_1 - W_{13} = Q_1[1-\eta(T_1,T_3)]
\end{cases}
$$

Comparison of the last expressions would give us:

$$
[1- \eta(T_1,T_3)] = [1-\eta(T_1,T_2)][1-\eta(T_2,T_3)]
$$
This property implies that $1-\eta(T_1, T_2)$ can be written as a ration of the form $f(T_2)/f(T_1)$, which by convention is set to $T_2/T_1$, that is,
$$
\begin{align}
1- \eta(T_1,T_2) &= \frac{Q_2}{Q_1} = \frac{T_2}{T_1}\\
\eta(T_H,T_C) &= 1- \frac{T_C}{T_H} = \frac{T_H - T_C}{T_H} 
\end{align}
$$

This equation defines a temperature up to a constant of proportionality, which is again set by choosing the triple point of water, ice, and steam, to $273.16\text K$. So far we have used the symbols $\Theta$ and $T$ interchangeably. In fact, by running a Carnot cycle for a perfect gas, it can be proved that the ideal gas and thermodynamic temperature scales are equivalent. 

All thermodynamics temperatures are positive, since the heat extracted from a temperature $T$ is proportional to it. If a negative temperature existed, an engine operating between it and a positive temperature would extract heat from both reservoirs and convert the sum total to work, in violation of Kelvin's statement of the second law.

# Entropy

Consider the **Clausius's theorem**:

> *For any cyclic transformation (reversible or not), $\oint \bar{d} Q / T \leq 0$, where $\bar d Q$ is the heat increment supplied to the system at temperature $T$.*

1. Subdivide the cycle into series of infinitesimal transformations in which the system receives energy in the form of heat $\bar dQ$ and work $\bar d W$. The system need not be in equilibrium at each interval. 

2. Direct all the heat exchanges of the system to one port of a Carnot engine, which has another reservoir at a fixed temperature $T_0$.

3. Since the sign of $\bar d Q$ is not specified, the Carnot engine must operate a series of infinitesimal cycles in either direction.

4. To deliver heat $\bar d Q$ to the system at some stage, the engine has to extract heat $\bar d Q_R$ from the fixed reservoir. If the heat is delivered to a part of the system that is locally at temperature $T$, then according to our $\eta$ equation we have:

$$
\bar d Q_R = T_0 \frac{\bar d Q}{T}
$$
5. After the cycle is completed, the system and the Carnot engine return to their original states. The net effect of the combined process is extracting heat $Q_R = \oint \bar Q_R$ from the reservoir and converting it to external work $W$. 
6. The work $W=Q_R$ is the sum of total of the work elements done by the Carnot engine, and the work performed by the system in the complete cycle.
7. By Kelvin's statement of the second law, $Q_R = W \leq0$, that is:
	$$
	T_0 \oint \frac{\bar d Q}{T} \leq0 \Longrightarrow \oint \frac{\bar d Q}{T} \leq 0,
	$$
	Since $T > 0$. 

### Consequences of Clausius's Theorem

1. *For a reversible cycle* $\oint Q_{\text{rev}} / T = 0$, since by running in the opposite direction $\bar d Q_{\text{rev}} \rightarrow -\bar d Q_{\text{rev}}$, and by the above theorem $\bar Q_{\text{rev}}/T$ is both non-negative, and non-positive, hence zero. This implies that **The integral of $\bar d Q_{\text{rev}} /T$ between any two points $A$ and $B$ is independent of path.**
2. Because the path doesn't matter, we can construct yet another function of state, the *entropy* $S$. Since the integral is independent of path, and only depends on the two end-points:
$$ S(B) - S(A) \equiv \int_A^B \frac{\bar d Q_{\text{rev}}}/T
$$
> For reversible processes, we can now compute the heat from $\bar d Q_{\text{rev}} = T dS$. This allows us to construct adiabatic curves for a general system from the condition of constant $S$.

3. For a reversible transformation, $\bar d Q = T dS$ and $\bar W = \sum_i J_i dx_i$, and the first law implies:

$$
dE = \bar dQ + \bar d W = TdS  + \sum_i J_i dx_i
$$

We can see that in this equation $S$ and $T$ appear as conjugate variables, with $S$ playing the role of displacement and $T$ playing the role of force.

This identification allows us to make the correspondence between mechanical and thermal exchanges more precise, although we should keep in mind that unlike its mechanical analog, temperature is always positive. 

> [!NOTE]
    > While we used reversible transformations to get to this equation; it is important to emphasize that it is a relation between functions of state. Therefore appliable to every thermodynamical system. **This is likely the most fundamental and useful identity in thermodynamics**.

4. ***The number of independent variables necessary to describe work on a system follows from this equation.*** If there are $n$ conjugate pairs of forces and displacements then $n+1$ independent coordinates are necessary to describe the system.
5. Consider an irreversible change from $A$ to $B$. Make a complete cycle by returning from $B$ to $A$ along a reversible path, then:
	$$ \int_A^B \frac{\bar dQ}{T} + \int_B^A \frac{\bar dQ_{\text{rev}}}{T} \leq 0\Longrightarrow \int_A^B \frac{\bar dQ}{T}\leq S(B) - S(A).$$
	In differential form, this implies that $dS \geq \bar dQ /T$ for any transformation. In particular, consider adiabatically isolating a number of subsystems, each initially separately in equilibrium. As they come to a state of joint equilibrium since the net $\bar d Q = 0$, we must have $\delta S \geq 0$. Thus an adiabatic system attains a maximum value of entropy in equilibrium since spontaneous internal changes can only increase $S$. The direction of increasing entropy thus points out the arrow of time, and the path to equilibrium.

# Approach to Equilibrium and Thermodynamic Potentials

“The time evolution of systems toward equilibrium is governed by the second law of thermodynamics.” (Kardar, p. 16)

“What about out-of-equilibrium systems that are not adiabatically isolated, and may also be subject to external mechanical work?” (Kardar, p. 16)

**Enthalpy** is the appropriate function when there is no heat exchange ($\bar d Q = 0$), and the system comes to mechanical equilibrium with *a constant external force*. The minimum equilibrium principle merely formulates the observation that stable mechanical equilibrium is obtained by minimizing the net potential energy of the system *plus the external agent*. 

For any set of displacements $x$, at constant (externally applied) generalized forces $J$, the work input to the system is $\bar d W \leq \mathbf J \cdot \delta \mathbf x$ (Equality is achieved for a quasi-static change with $\mathbf J = \mathbf J_i, but there is generally some loss of the external work to dissipation). Since $\bar d Q = 0$ using the first law, $\delta E\leq \mathbf J\cdot \delta \mathbf x$. and $\delta H \leq 0$ where $H = E - \mathbf J\cdot \mathbf x$ is the enthalpy. The variations of $H$ i  equilibrium are given by:
$$dH = dE - d(\mathbf J \cdot \mathbf x) = TdS - \mathbf x \cdot d\mathbf J $$
The coordinate $(S,\mathbf J)$ is the natural choice for describing the enthalpy, and it follows from this equation that:

$$
x_i = \left.-\frac{\partial H}{\partial \mathbf J_i}\right\vert_{S,J_{j\not = i}}
$$

Variations of the enthalpy with temperature are related to heat capacities at constant force, for example:

$$
C_P = \left.\frac{\bar d Q}{dT}\right\vert_P = \left.\frac{dH}{dT}\right\vert_P 
$$

> [!NOTE]
> Note, however, that a change of variables is necessary to express $H$ in terms of $T$, rather than the more natural variable $S$

**Helmholtz free energy** is useful for isothermal transformations in the absence of mecchanical work ($\bar d W = 0$ ). It is rather similar to enthalpy, with $T$ taking the place of $J$. From Clausius's theorem, the heat intake of a system at a constant temperature satisfies $\bar d Q \leq T\delta S$ . Hence $\delta E = \bar d Q + \bar d W  \leq T\delta S$, and: 

$$\delta F \leq 0  \ \ \ \ \text{where} \ \ \ \ F = E -TS$$
is the Helmholtz free energy. Since:

$$
dF = dE - d(TS) = TdS + \mathbf J\cdot d \mathbf x - SdT - TdS = -SdT +\mathbf J\cdot d\mathbf x
$$
The coordinate set $(T,\mathbf x)$ is most suitable for describing free energy.  The equilibrium forces and entropy can be obtained by:

$$

J_i = \left.\frac{\partial F}{\partial x_i}\right\vert_{T,x_{j\not=i}} \ \ \ , \ \ \ S = \left.-\frac{\partial F}{\partial T}\right\vert_{x}.
$$
The internal energy can also be calculated from $F$:
$$
E + F+TS = F-T \left.\frac{\partial F}{\partial T}\right\vert_{x} = -\left.T^2\frac{\partial (F/T)}{\partial T}\right\vert_{x}
$$

**Gibbs free energy** applies to isothermal transformations involving mechanical work at constant external force. The natural inequalities for work and heat input into the system are given by $\bar d W \leq \mathbf J\cdot \delta \mathbf x$ and $\bar d Q \leq T\delta S$. Hence $\delta E \leq T\delta S + \mathbf J \cdot \delta \mathbf x$, leading to

$$
\delta G \leq 0  \ \ \ \text{where} \ \ \ G = E-TS - \mathbf J\cdot \mathbf x
$$
is the Gibbs free energy. Variations of $G$ are given by:

$$
d G = dE - d(TS) - d(\mathbf J \cdot \mathbf x) = TdS + \mathbf J\cdot d\mathbf x - SdT -TdS - \mathbf x\cdot d\mathbf J - \mathbf J \cdot d \mathbf x 
$$
which gives out:

$$
dG = -SdT - \mathbf x \cdot d\mathbf J
$$
and most easily expressed in terms of $T$ and $\mathbf J$ 

Until now we've used the assumption that the number of particles does not change in our system, and in equilibrium between two phases, the number of particles in a given constituent may change. The change in the number of particles necessarily involves changes in the internal energy, which is expressed in terms of a chemical work $\bar d W = \mu \cdot d \mathbf N$. The vector $N$ is just a list of number of particles of each species, and $\mu$ is the associated chemical potentials that measure the work necessary to add additional particles to the system.

For chemical equilibrium in circumstances that involve no mechanical work, the appropriate state function is the grand potential given by:

$$
\mathcal {G} = E - TS - \mathbf \mu \cdot \mathbf N
$$

The grand potential is minimized in chemical equilibrium, and its variations in general satisfy:

$$
d\mathcal G = -SdT + \mathbf J \cdot d\mathbf x - \mathbf N \cdot d\mu 
$$

The following sections of chapter 1, I didn't write note for, I list topics and you do exactly what you're doing as before:

# Useful Mathematical Results:

-  Extensivity, resulting in Gibbs-Duhen relations
- Maxwell relations
- The Gibbs Phase Rule

# Stability Conditions

As noted earlier, the conditions derived in Section 1.7 are similar to the wellknown requirements for mechanical stability: a particle moving freely in an

external potential U x dissipates energy and settles to equilibrium at a minimum value of U . The vanishing of the force Ji = −dU/dx is not by itself sufficient to ensure stability, as we must check that it occurs at a minimum of the potential energy, such that d2U/dx2 > 0. In the presence of an external force J , we must minimize the “enthalpy” H = U − Jx, which amounts to tilting the potential. At the new equilibrium point xeq J , we must require d2H/dx2 = d2U/dx2 > 0. Thus only the convex portions of the potential U x are physically accessible. With more than one mechanical coordinate, the requirement that any change x results in an increase in energy (or enthalpy) can be written as  ∑  ij  2U  xi xj  xi xj > 0 (1.61)  We can express the above equation in more symmetric form, by noting that the corresponding change in forces is given by  Ji =  (U  xi  )  =∑  j  2U  xi xj  xj (1.62)  Thus Eq. (1.61) is equivalent to  ∑  i  Ji xi > 0 (1.63)  When dealing with a thermodynamic system, we should allow for thermal and chemical inputs to the internal energy of the system. Including the corresponding pairs of conjugate coordinates, the condition for mechanical stability should generalize to  T S+∑  i  Ji xi + ∑ N > 0 (1.64)  Before examining the consequences of the above condition, I shall provide a more standard derivation that is based on the uniformity of an extended thermodynamic body. Consider a homogeneous system at equilibrium, characterized

--- 
Some things I thought about during reading:
1. Temperature is force? intuition? well look at it as a part of potential energy that can interact with other systems.
2. Can we have a smooth map from thermodynamic systems to general systems with the fact that quasi static is a continously defined phenomena? Like I'm doing a process in a way that the macroscopic events can matter but not the microscopic events? Global matters and not Local? Assume all the degrees of freedom in a system quite literally, if they are in such a way that a basis $P$ can be approximately define the space (there are small angles between them) one can have thermodynamic, otherwise the approximation doesn't work.