# Problem 1

For Newtonian gravity the potential is related to the mass density by Poisson's equation
$$
\nabla^2\Phi(\vec{x},t) = 4\pi G \rho(\vec x , t)
$$
Before Special relativity, Galilean transformation was used to relate the space and time coordinates of an event as observed in two different inertial reference.

- Show that the Poisson's equation is invariant under a Galilean transformation.
- Then show that Poisson's equation is not invariant under a Lorentz transformation.

### Answer
#### A:
Let's consider to coordinate systems $S$ and $S'$ with relative velocity $v$. Consider the Poisson's equation in $S$ coordinate as:

$$
\left(\frac{\partial^2}{\partial x^2} + \frac{\partial^2}{\partial y^2} + \frac{\partial^2}{\partial z^2}\right)\Phi  = \alpha \rho
$$

where $\alpha = 4\pi G$. Galilean transformation imposes the following rules of transformation from $S$ to $S'$:
$$
\begin{align}
x'&= x +  vt\\
y'&=y\\
z'&=z \\
t'&=t
\end{align}
$$
we therefore expand the Poisson's equation and write in terms of the $S'$ coordinates:

$$
\begin{align}
\partial_{x'}\left(\partial_{x'}\Phi \partial_xx' \right)\partial_xx' + \partial_{y'}\left(\partial_{y'}\Phi \partial_yy' \right)\partial_yy' +\partial_{z'}\left(\partial_{z'}\Phi \partial_zz' \right)\partial_zz' 
\end{align} = \dots
$$

now we know by the rules that:
$$
\partial_i i' = 1
$$
where $i=x,y,z$ and $i'=x',y',z'$

Therefore:
$$
\nabla^2 = \nabla'^2
$$
Now the Poisson's equation becomes:
$$
\boxed{
\nabla'^2 \Phi(\vec x',t') = 4\pi G\rho(\vec x' , t')
}
$$
$$
\text{QED.}
$$

#### B:
Following our previous example we know that the transformation rules imposed by Lorentz transformations are:
$$
\begin{align}
t'&= \frac{1}{\sqrt{1-v^2}}(t + x/v)\\
x'&= \frac{1}{\sqrt{1-v^2}} (x - vt)\\
y'&= y\\
z'&= z
\end{align}
$$

# Problem 2
There are hypothetical particles called tachyons which always move faster than light.

- Show that the four-velocity of tachyons is space-like
- Also prove that this property is invariant under a Lorentz boost? (Show that if a tachyon moves faster in one inertial frame, then it moves faster in all other inertial frames)
### Answer
#### A:
Assume $v^\mu$ to be the four-velocity of a tachyon and $c^\mu$ be the four-velocity of light, we have to show that:
$$
v^\mu v_\mu > c^\mu c_\mu
$$
By definition we know that the null vector is zero thus:

$$
v^\mu v_\mu > 0
$$

#### B:
Now any Lorentz transformation on this would have the form:
$$
v^{\nu'} = \Lambda^{\nu'}_{\ \ \mu} v^\mu 
$$
writing down:
$$
v^{\nu'}v_{\nu'} = \Lambda^{\nu '}_{\ \ \mu}\Lambda_{\nu'}^{ \ \ \lambda} v^{\mu} v_\lambda
$$

By definition:
$$
 \Lambda^{\nu '}_{\ \ \mu}\Lambda_{\nu'}^{ \ \ \lambda} = \delta_\mu^\lambda
$$
and thus:
$$
v^{\nu'}v_{\nu'} =  v^{\mu} v_\mu > 0
$$
Which shows that tachyons are tachyons in every coordinate system, and are moving faster than the speed of light.

> Another simple approach would be to note that $v^\mu v_\mu$ is an scalar and scalars are invariant under coordinate transformations. 

# Problem 3
- Show that if two events are time-like separated, there is a Lorentz frame in which they occur at the same point, i.e. at the same spatial coordinate values.
- Similarly, show that if two events are space-like separated, there is a Lorentz frame in which they are simultaneous

### Answer
#### A:
Let us imagine two events $a^\mu$ and $b^\mu$. The difference between these two can be shown by:
$$
\Delta^\mu = a^\mu - b^\mu 
$$
Now $\Delta^\mu$ is by definition above, a 4-vector. For $|\Delta^\mu|$ there are three scenarios again:

$$
\begin{cases}
|\Delta^\mu| > 0, &\text{Space-like}\\
|\Delta^\mu| < 0 , &\text{Time-like}\\
|\Delta^\mu| = 0 , &\text{null}
\end{cases}
$$
We can in principle choose two coordinates where $\Delta^\mu$ lies on the $x$-axis. Then:

$$
\Delta^\mu = (\Delta t , \Delta x , 0,0)
$$
Assume we're in the $S$ inertial frame, we want to find $S'$ such that:
$$
\Delta^{\mu'} = (\Delta t',0,0,0)
$$
We know the transformation rule between inertial frame are given by the Lorentz transformations therefore:

$$
\Delta^{\mu'}= \Lambda^{\mu'}_{\ \ \ \mu} \Delta^{\mu} 
$$
Expanding it means:
$$
\begin{cases}
\Delta t' = \gamma(\Delta t  - v \Delta x) \\ 
\Delta x' = \gamma (\Delta x - v \Delta t)
\end{cases}
$$
We want $\Delta x' = 0$
Achieving this is possible by finding $v$ of our transformation satisfying:
$$
\begin{align}
\gamma (\Delta x - v\Delta t) &= 0\\
v &= \frac{\Delta x}{\Delta t}
\end{align}
$$
If the events are time-like separated then $\Delta x / \Delta t < 1$. We've shown that there exists a transformation $S \rightarrow S' = S_v$ such that in that frame, the spacial components of the distance between these events would be zero. Interpreting this physically means:

> You moved to the rest frame of the worldline joining the two events.

The crucial condition to be added here is that we need the events be in such distance that $v \not > c$ otherwise the condition only applies when the inertial frame is moving faster than the speed of light.

#### B:
Following the reasoning of the previous section we consider that this time $\Delta x / \Delta t >1$. Considering the same equations hold:
$$
\begin{cases}
\Delta t' = \gamma(\Delta t  - v \Delta x) \\ 
\Delta x' = \gamma (\Delta x - v \Delta t)
\end{cases}
$$
Setting $\Delta t'=0$ would yield:
$$
\begin{align}
\gamma(\Delta t - v\Delta x) &= 0\\
v &= \frac{\Delta t}{\Delta x}
\end{align}
$$
and since $\Delta t / \Delta x < 1$ we're sure that $v < c$, therefore we've shown that there exists a transformation $S \rightarrow S' = S_v$ in which the distance in the final inertial frame have no temporal component. 

# Problem 4: P2 of Reference Book
Imagine that space (not spacetime) is actually a finite box, or in more sophisticated terms, a three-torus, of size $L$. By this we mean that there is a coordinate system $x^\mu = (t,x,y,z)$ such that every point with coordinates $(t,x,y,z)$ is identified with every point with coordinates $(t,x+L,y,z)$, $(t,x,y+L,z$), and $(t,x,y,z+L)$. Note that the time coordinate is the same. Now consider two observers; observer $A$ is at rest in this coordinate system (constant spatial coordinates), while observer $B$ moves in the $x$-direction with constant velocity $v$. $A$ and $B$ begins at the same events, and while $A$ remains still, $B$ moves once around the universe and comes back to intersect the world-line of $A$ without ever having to accelerate (since the universe is periodic). 

- What are the relative proper times experienced in this interval by $A$ and $B$? 
- Is this consistent with your understanding of Lorentz invariance?

### Answer:
Space is a $3$-torus of circumference $L$ in each spatial direction, so the identification is:
$$
(t,x,y,z)\sim (t,x+L,y,z)
$$
Time coordinate $t$ is the same at identified points.
Observer $A$ sits at fixed spatial coordinates (so $A$ is at rest in the coordinates that define the identifications). Observer $B$ moves at constant velocity $v$ in the $x$-direction and, because of the periodic identification, returns to intersect $A$'s world-line after one circuit without any acceleration.

We use units with $c=1$ and $0< |v| < 1$.

Along $B$'s path in the given coordinates, the spatial distance travelled in the $x$-direction (from starting event to reunion event) is exactly $\Delta x = L$. Since $B$ moves with velocity $v$ in these coordinates,

$$
v = \frac{\Delta x}{\Delta t} \Rightarrow \Delta t = \frac{\Delta x}{v}=\frac{L}{v}
$$

For observer $A$ (world-line: fixed $x,y,z$):
$$
d\tau_A^2 = -ds^2 = dt^2 \Rightarrow \Delta \tau_A = \Delta t = \frac{L}{v}
$$
For observer $B$ (constant velocity $v$):
The line element for a straight inertial world-line with coordinate velocity $v$ is 

$$
d\tau_B = dt\sqrt{1-v^2}=\frac{dt}{\gamma}.
$$
Integrating over the trip, 
$$
\Delta \tau_B = \Delta t \sqrt{1-v^2}=\frac{\Delta t}{\gamma}=\frac{L}{v\gamma},
$$
where $\gamma=1/\sqrt{1-v^2}$. Thus
$$
\boxed{\Delta \tau_A = \frac{L}{v},  \ \ \Delta\tau_B = \frac{L}{v\gamma}}
$$
So $B$ ages less: $\Delta\tau_B = \Delta\tau_A/\gamma$. Locally the metric is Minkowski and Lorentz invariance holds: time dilation formula and proper-time calculation used above are standard. The identification $x\sim x+L$ at the same coordinate time $t$ singles out the coordinate frame in which the identifications are purely spatial.

That frame is therefore preferred by the global structure of this spacetime.

If you boost to another inertial frame, the identification no longer connects purely spatial points but connects events separated in time as well. Under a boost with velocity $v$ the identification vector $(\Delta t, \Delta x) = (0,L)$ transforms to:
$$
\Delta t' = \gamma(0-vL) = -\gamma vL , \ \ \Delta x' = \gamma L,
$$
so the identification links events with a nonzero time difference in the primed frame. In other words, the periodic spatial identification breaks global Lorentz symmetry even though the local metric is Lorentzian.

Because of the global asymmetry, the two inertial, non-accelerating world-lines $A$ and $B$ are not equivalent global paths between the same pair of events.

Topologically, a torus is a closed surface defined as the product of two circles. The moving body ($B$) and the stationary one $A$ are not equal because they lie on different classes of paths (different homotopy classes). Proper time compares lengths of time-like curves

Therefore the result $\Delta\tau_B < \Delta\tau_A$ is fully consistent with special relativity applied locally; the asymmetry arises from the global topology which selects a preferred frame for the identifications.


# Problem 5: P3 of Reference Book


### Answer:
If $A,B,C$ are separated time-like. 

# Problem 6: P5 of Reference Book
Particle physicists are so used to setting $c=1$ that they measure mass in units of energy. In particular, they tend to use electron-volts ($1\text{eV} = 1.6 \times10^{-12}\text{erg} = 1.8\times10^{-33}\text{gr}$), or, more commonly $\text{keV}$, $\text{MeV}$ and $\text{GeV}$ ($10^3 \text{eV}, 10^6\text{eV}, 10^9\text{eV}$, respectively).

The muon has been measured to have a mass of $0.106\text{GeV}$ and a rest frame life-time of $2.19\times 10^{-6}$ seconds. Imagine that such a muon is moving in the circular storage ring of a particle accelerator, $1$ kilometer in diameter, such that the muon's total energy is $1 \text{TeV}$. How long would it appear to live from the experimenter's point of view? How many radians would it travel around the ring?

### Answer:
We first have to find out the speed of the muon with respect to the stationary (assumed) observer. Calculating:
$$
E^2 = m^2 + p^2
$$
But we already know the total energy and the rest mass. Therefore,
$$
(10^3 - 0.106) \text{GeV} = 
$$
# Problem 7: P6 of Reference Book
In Euclidean three-space, let $p$ be the point with coordinates $(x,y,z) = (1,0,-1)$. Consider the following curves that pass through $p$:

$$
\begin{align}
x^i(\lambda) &= (\lambda, (\lambda - 1)^2, -\lambda) \\ 
x^i (\mu) &= (\cos\mu,\sin\mu,\mu-1)\\
x^i(\sigma)&=(\sigma^2,\sigma^3+\sigma^2,\sigma)\\
\end{align}
$$
- Calculate the components of the tangent vectors to these curves at $p$ in the coordinate basis $\{\partial_x,\partial_y,\partial_z\}$ 
- Let $f=x^2 + y^2 - yz$. Calculate $\frac{df}{d\lambda},\frac{df}{d\mu},\frac{df}{d\sigma}$

# Problem 8: P7 of Reference Book
Imagine we have a tensor $X^{\mu\nu}$ and a vector $V^{\mu}$,with components:
$$
X^{\mu\nu} = \begin{pmatrix}2 & 0 &1&-1 \\ -1 & 0 & 3&2 \\ -1 & 1& 0&0 \\ -2 & 1 & 1 &-2\end{pmatrix}, \ \ V^\mu = (-1,2,0,-2)
$$
Find the components of:
- $X^\mu_{ \ \ \nu}$ 
- $X_{\mu}^{\ \ \nu}$
- $X^{(\mu\nu)}$
- $X_{[\mu\nu]}$
- $X^{\lambda}_{\ \ \lambda}$
- $V^{\mu}V_\mu$
- $V_\mu X^{\mu\nu}$
