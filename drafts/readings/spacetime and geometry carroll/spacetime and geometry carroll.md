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