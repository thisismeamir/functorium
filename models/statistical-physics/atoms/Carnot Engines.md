---
sticker: lucide//atom
---
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
