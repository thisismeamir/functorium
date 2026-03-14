# Chapter 7 - Capacitors and Inductors
---
**Table of Content**
```toc
    style: number
    min_depth: 1
    max_depth: 6
```
---
## The Capacitor
### Ideal Capacitor
Previously, we referred to *independent and dependent sources as active elements*, and *the linear resistor as a passive element*,  We now define an active element as an element that is capable of furnishing an average power greater than zero to some external device, where the average is taken over an infinite time interval. Ideal sources are active elements, and the operational amplifier is also an active device. 
\
A passive element, however, is defined as an element that cannot supply an average power that is greater than zero over an infinite time interval. The resistor falls into this category; the energy it receives is usually transformed into heat, and it never supplies energy.
\
\
We now introduce a new passive circuit element, **the capacitor**. We define capacitance **C** by the voltage–current relationship:
$$
i = C\frac{dv}{dt}
$$
where $v$ and  $i$ satisfy the conventions for a passive element. We should bear in mind that **v** and **i** are functions of time; if needed, we can emphasize this fact by writing **v(t)** and **i(t)** instead.
![[Pasted image 20211121094538.png]]
we may determine the unit of capacitance as an ampere-second per volt, or coulomb per volt. We will now define the **farad (F)** as one coulomb per volt, and will use this as our unit of capacitance.

The ideal capacitor defined by Eq above is only a mathematical model of a real device.
![[Pasted image 20211121095515.png]]
A capacitor consists of two conducting surfaces on which charge may be stored, separated by a thin insulating layer that has a very large resistance. If we assume that this resistance is sufficiently large that it may be considered infinite, then equal and opposite charges placed on the capacitor “plates” can never recombine, at least by any path within the element. 

Let’s visualize some external device connected to this capacitor and causing a positive current to flow into one plate of the capacitor and out of the other plate. Equal currents are entering and leaving the two terminals, and this is no more than we expect for any circuit element. Now let us examine the interior of the capacitor. The positive current entering one plate represents positive charge moving toward that plate through its terminal lead; this charge cannot pass through the interior of the capacitor, and it therefore accumulates on the plate. As a matter of fact, the current and the
increasing charge are related by the familiar equation:
$$
i = \frac{dq}{dt}
$$
Now let us consider this plate as an overgrown node and apply Kirchhoff’s current law. It apparently does not hold;current is approaching the plate from the external circuit, but it is not flowing out of the plate into the “internal circuit.”
\
The unified electromagnetic theory that Maxwell subsequently developed hypothesizes a “displacement current” that is present wherever an electric field or a voltage is varying with time. The displacement current flowing internally between the capacitor plates is exactly equal to the conduction current flowing in the capacitor leads; Kirchhoff’s current law is therefore satisfied if we include both conduction and displacement currents. However, circuit analysis is not concerned with this internal displacement current, and since it is fortunately equal to the conduction current, we may consider Maxwell’s hypothesis as relating the  conduction current to the changing voltage across the capacitor.

Several important characteristics of our new mathematical model can be discovered from the defining equation,$i = C\frac{dv}{dt}$. 

***A constant voltage across a capacitor results in zero current passing through it; a capacitor is thus an “open circuit to dc.”***

This fact is pictorially represented by the capacitor symbol. It is also apparent that a sudden jump in the voltage requires an infinite current. Since this is physically impossible, we will therefore prohibit the voltage across a capacitor to change in zero time.

### Integral Voltage–Current Relationships
The capacitor voltage may be expressed in terms of the current by integrating $i = C\frac{dv}{dt}$. We first obtain:
$$
dv = \frac1C i(t)dt
$$
and then integrate:
$$
v(t) = \frac1C \int_{t_0}^t i(t')dt' + v(t_0)
$$
or written indefinitely:
$$
v(t) \frac1C\int i(t)dt + k
$$
Finally, in many situations we will find that $v(t_0)$, the voltage initially across the capacitor, cannot be discerned. In such cases it is mathematically convenient to set $t_0 = −\infty$ and $v(-\infty) =0$, so that:
$$
v(t) = \frac1C\int_{-\infty}^t i dt'
$$
Since the integral of the current over any time interval is the corresponding charge accumulated on the capacitor plate into which the current is flowing, we may also define capacitance as
$$
q(t) = Cv(t)
$$
where $q(t)$ and $v(t)$ represent instantaneous values of the charge on either plate and the voltage between the plates, respectively.

### Energy Storage
To determine the energy stored in the electric field of a capacitor, we begin with the power delivered to it:
$$
p = vi = cv\frac{dq}{dt}
$$
and simply integrate over the time interval:
$$
\int_{t_0}^t pdt' = C\int_{t_0}^t v \frac{dv}{dt'}dt' = C\int_{v(t_0)}^{v(t)}vdv = \frac12C\big(v^2(t)-v^2(t_0)\big)
$$
Thus:
$$
w_C(t) - w_C(t_0) = \frac12C\big(v^2(t)-v^2(t_0)\big)
$$
where the stored energy is $w_C$, measured in joules (J), and the voltage at $t_0$ is $v(t_0)$. If we select a zero-energy reference at $t_0$, implying that the capacitor voltage is also zero at that instant, then:
$$
w_C(t) = \frac12Cv^2
$$

### Important Characteristics of an Ideal Capacitor 
1. There is no current through a capacitor unless the voltage across it is changing with time. A capacitor is therefore an open circuit to dc.

2. A finite amount of energy can be stored in a capacitor even if the current through the capacitor is zero, such as when the voltage across it is constant.

3. It is impossible to change the voltage across a capacitor by a finite amount in zero time, as this requires an infinite current through the capacitor. (A capacitor resists an abrupt change in the voltage across it in a manner analogous to the way a spring resists an abrupt change in its displacement.)

4. An ideal capacitor never dissipates energy, but only stores it. Although this is true for the mathematical model, it is not true for a physical capacitor due to finite resistances associated with the dielectric as well as the packaging. Thus, a real capacitor will eventually discharge once disconnected from a power source.

## The Inductor
### Ideal Inductor Model
In the early 1800s Danish scientist Hans Christian Ørsted showed that a current-carrying conductor produced a magnetic field (i.e. compass needles were affected in the presence of a wire when current was flowing). Shortly thereafter, Ampère made some careful measurements which demonstrated that this magnetic field was linearly related to the current which produced it. The next step occurred some 20 years later when English experimentalist Michael Faraday and American inventor Joseph Henry discovered almost simultaneously3 that a changing magnetic field could induce a voltage in a neighboring circuit. They showed that this voltage was proportional to the time rate of change of the current producing the magnetic field. The constant of proportionality is what we now call the **inductance**, symbolized by L, and therefore
$$
v = L\frac{di}{dt}
$$
The circuit symbol for the inductor is shown in Fig. 7.10, and it should be noted that the passive sign convention is used, just as it was with the resistor and the capacitor. The unit in which inductance is measured is the Henry (H), and the defining equation shows that the Henry is just a shorter
expression for a volt-second per ampere.
![[Pasted image 20211121103714.png]]

The inductor whose inductance is defined by Eq above is a mathematical model; it is an ideal element which we may use to approximate the behavior of a real device. A physical inductor may be constructed by winding a length of wire into a coil. This serves effectively to increase the current that is causing the magnetic field and also to increase the “number” of neighboring circuits into which Faraday’s voltage may be induced. The result of this twofold effect is that the inductance of a coil is approximately proportional to the square of the number of complete turns made by the conductor out of which it is formed.

This equation shows that the voltage across an inductor is proportional to the time rate of change of the current through it. 
$$
v = L\frac{di}{dt}
$$
In particular, it shows that there is no voltage across an inductor carrying a constant current, regardless of the magnitude of this current. Accordingly, we may view an inductor as a **short circuit to dc.**
Another fact that can be obtained from Eq is that a sudden or discontinuous change in the current must be associated with an infinite voltage across the inductor. 
\
In other words, if we wish to produce an abrupt change in an inductor current, we must apply an infinite voltage. Although an infinite-voltage forcing function might be amusing theoretically, it can never be a part of the phenomena displayed by a real physical device. 
\
As we shall see shortly, an abrupt change in the inductor current also requires an abrupt change in the energy stored in the inductor, and this sudden change in energy requires infinite power at that instant; infinite power is again not a part of the real physical world. In order to avoid infinite voltage and infinite power, an inductor current must not be allowed to jump instantaneously from one value to another.
![[Pasted image 20211121113333.png]]

### Integral Voltage-Current Relationships
We have defined inductance by a simple differential equation, and we have been able to draw several conclusions about the characteristics of an inductor from this relationship.
$$
v = L\frac{di}{dt}
$$
The simple defining equation for inductance contains still more information, however. Rewritten in a slightly different form:
$$
di = \frac1L v(t)dt
$$

it invites integration. Let us first consider the limits to be placed on the two integrals. We desire the current $i$ at time $t$, and this pair of quantities therefore provides the upper limits on the integrals appearing on the left and right sides of the equation, respectively; the lower limits may also be kept general by merely assuming that the current is $i(t_0)$ at time $t_0$. Thus,

$$
\int_{i(t_0)}^{i(t)} di = \frac1L\int_{t_0}^t v(t')dt'
$$
which leads to:
$$
i(t)-i(t_0) = \frac1L\int_{t_0}^t v(t')dt'
$$
We may write the integral as an indefinite integral and include a constant of integration $k$:
$$
i(t) = \frac1L\int v(t)dt+k
$$
We also may assume that we are solving a realistic problem in which the selection of $t_0$ as $–∞$ ensures no current or energy in the inductor. Thus, if $i(t_0) = i (−∞) = 0$, then:
$$
i = \int_{-\infty}^tvdt'
$$
### Energy Storage
Let us now turn our attention to power and energy. The absorbed power is given by the current–voltage product:
$$
p=vi = Li\frac{di}{dt}
$$
The energy $w_L$ accepted by the inductor is stored in the magnetic field around the coil. The change in this energy is expressed by the integral of the power over the desired time interval:
$$
\begin{equation}
\begin{split}
\int_{t_0}^t pdt' =& L\int_{t_0}^ti\frac{di}{dt'}dt' = L\int_{t_0}^ti'dt'
\\
=&\frac12L\big(i^2(t)-i^2(t_0)\big)
\end{split}
\end{equation}
$$
Thus,
$$
w_L(t) - w_L(t_0)\frac12L\big(i^2(t)-i^2(t_0)\big)
$$
where we have again assumed that the current is $i(t0)$ at time $t_0$. In using the energy expression, it is customary to assume that a value of $t_0$ is selected at which the current is zero; it is also customary to assume that the energy is zero at this time. We then have simply:
$$
w_L(t)  = \frac12Li^2
$$

### Important Characteristics of an Ideal Inductor 
1. There is no voltage across an inductor unless the current through it is changing with time. An inductor is therefore a short circuit to dc.
2. A finite amount of energy can be stored in an inductor even if the voltage across the inductor is zero, such as when the current through it is constant.
3. It is impossible to change the current through an inductor by a finite amount in zero time, for this requires an infinite voltage across the inductor. (An inductor resists an abrupt change in the current through it in a manner analogous to the way a mass resists an abrupt change in its velocity.)
4. The inductor never dissipates energy, but only stores it. Although this is true for the mathematical model, it is not true for a physical inductor due to series resistances. An interesting exception is created when a superconducting wire is used to build the inductor.

## Inductance and Capacitance Combinations
We look first at Kirchhoff’s two laws, both of which are axiomatic. However, when we hypothesized these two laws, we did so with no restrictions as to the types of elements constituting the network. Both, therefore, remain valid.
### Inductors in Series
We first consider an ideal voltage source applied to the series combination of $N$ inductors, as shown in Fig. 7.18a. We desire a single equivalent inductor, with inductance $L_{eq}$, which may replace the series combination so that the source current $i(t)$ is unchanged. The equivalent circuit is sketched in Fig. 7.18b. Applying KVL to the original circuit,
![[Pasted image 20211121120136.png]]
$$
\begin{equation}
\begin{split}
v = &\sum v_i
\\
v = &\frac{di}{dt}\sum L_i
\end{split}
\end{equation}
$$
Since:
$$
v = L_{eq} \frac{di}{dt}
$$
Thus
$$
L_{eq}  \frac{di}{dt} =  \frac{di}{dt}\sum_i L_i
$$
Therefore:
$$
L_{eq} = \sum_i L_i
$$
### Inductors in Parallel
The combination of a number of parallel inductors is accomplished by writing the single nodal equation for the original circuit, shown in Fig. 7.19a,
![[Pasted image 20211121121427.png]]
$$
\begin{equation}
\begin{split}
i_s =& \sum i_n = \sum\frac1{L_n}\int_{t_0}^t vdt +i_n(t_0)

=& \sum \frac1{L_n}\int_{t_0}^t vdt  + \sum i_n(t_0)
$$
from another point of view:
$$
i_s = \frac 1{Leq}\int_{t_0}^t vdt  i_s(t_0)
$$
Snice Kirchhoff's current law demands that $i_s(t_0)$ be equal to the sum of the branch currents at $t_0$  the two  integral terms must be equal hence:
$$
\frac1{L_{eq}} = \sum\frac1{L_i}
$$
### Capacitors in Series
Capacitors tend to act the opposite of inductors we can derive just like above that for Capacitors in Series:
![[Pasted image 20211121123320.png]]
$$
\frac1{C_{eq}} = \sum \frac1{C_i}
$$
### Capacitors in Parallel
This can easily be done to so that we find:
$$
C_{eq} = \sum C_i
$$
![[Pasted image 20211121123448.png]]
## Linearity and its Consequences
Next let us turn to nodal and mesh analysis. Since we already know that we may safely apply Kirchhoff’s laws, we can apply them in writing a set of equations that are both sufficient and independent. They will be constant-coefficient linear “integrodifferential” equations, however, which are hard enough to pronounce, let alone solve. Consequently, we shall write them now to gain familiarity with the use of Kirchhoff’s laws in RLC circuits and discuss the solution of the simpler cases in subsequent chapters.