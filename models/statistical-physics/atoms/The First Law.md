---
sticker: lucide//atom
---
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
