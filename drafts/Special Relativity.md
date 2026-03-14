---
sticker: lucide//newspaper
---
# Overview
Special relativity, introduced by Albert Einstein in 1905, revolutionized our understanding of space and time by showing that they are not absolute but relative to the observer's state of motion. This theory resolved contradictions between Newtonian mechanics and Maxwell's equations of electromagnetism, demonstrating that the speed of light is constant for all observers, regardless of their motion.

However, special relativity applied primarily to non-accelerating, inertial reference frames, leaving gravity unexplained. A decade later, Einstein extended these principles to develop general relativity, a groundbreaking theory that redefined gravity as the curvature of spacetime caused by mass and energy. This shift transformed our view of the universe, laying the foundation for modern cosmology and our understanding of black holes, gravitational waves, and the dynamics of the cosmos.
# Basics
In 1905, Einstein's paper extended the principle of Galilean Relativity to encompass all physical laws, not just mechanics. By doing so, it immediately resolved the previous inconsistency between this principle and Maxwell's equations.

**The Principle of Special Relativity** is essentially an extension of Galilean Relativity to all areas of physics. After all, it would be odd for certain physical laws to remain the same across different inertial reference frames while others do not. This principle directly addresses the conflict with electromagnetism by asserting the following:

***The speed of light is invariant in all inertial reference frames.*** Since electromagnetism dictates that electromagnetic waves propagate at a speed of $c = 3 \times 10^8 \frac{m}{s}$, and since the laws of physics must hold true in all inertial reference frames (IRFs), the speed of light, $c$, must therefore remain constant in all IRFs.

# Kinematics in SR
From this one principle the nature of spacetime would look so different than what has been thought up until that point. The additional principle is one that is taken for granted in classical physics but now it must be narrowed and stipulated precisely.

- **Principle of Invariant Event**: This principle states that what occurs in one frame is the same in *any* other frame. But in SR this would be restricted. What changes here is that only observations that happen in one place and one time (events) can be considered the same, otherwise the principle is not allowed to be used.
- **Principle of Reciprocal Velocity**
Here's an explanation of the listed topics, with the required mathematical details using markdown format for both inline and block math expressions:

## Time Dilation
Time dilation occurs when time is observed to pass at different rates in different reference frames, particularly when one is moving relative to the other. According to special relativity, time for an observer in motion relative to a stationary observer will appear to pass more slowly.

If an object is moving with velocity $v$ relative to a stationary observer, the time interval $\Delta t'$ in the moving frame is related to the time interval $\Delta t$ in the stationary frame by the following formula:

$$
\Delta t' = \frac{\Delta t}{\sqrt{1 - \frac{v^2}{c^2}}}
$$

Where:
- $v$ is the relative velocity between the observer and the moving object,
- $c$ is the speed of light.

The factor $\gamma = \frac{1}{\sqrt{1 - \frac{v^2}{c^2}}}$ is called the Lorentz factor, which increases as $v$ approaches $c$, leading to significant time dilation effects at high speeds.

## Length Contraction
Length contraction is the phenomenon by which an object moving relative to an observer appears shorter along the direction of motion compared to its length when at rest.

If the proper length (the length of the object in its rest frame) is $L_0$, and the object moves with velocity $v$ relative to an observer, the observed length $L$ is given by:

$$
L = L_0 \sqrt{1 - \frac{v^2}{c^2}}
$$

Where:
- $L_0$ is the length of the object in its own rest frame,
- $L$ is the contracted length observed in the moving frame,
- $v$ is the relative velocity, and
- $c$ is the speed of light.

This effect only becomes significant as $v$ approaches $c$, meaning length contraction is not noticeable at everyday speeds but becomes prominent at relativistic velocities.

## Lack of Universal Simultaneity
In classical (Newtonian) physics, it is assumed that events occurring at the same time for one observer are simultaneous for all observers, regardless of their motion. However, in special relativity, simultaneity is relative: events that appear simultaneous in one inertial frame may not appear simultaneous in another.

The relativity of simultaneity can be demonstrated by the Lorentz transformations, which show how time and space coordinates change between reference frames. Consider two events occurring at the same time $t_A = t_B$ in one frame. In another frame moving with velocity $v$ relative to the first, the time of these events will generally differ:

$$
t'_A \neq t'_B
$$

This shows that simultaneity is not absolute; it depends on the observer’s reference frame. This breaks with our intuitive sense of time and highlights the deep connection between space and time in relativity.

## Addition of Velocity
In classical mechanics, velocities simply add together. However, in special relativity, the addition of velocities must account for the fact that no object can move faster than the speed of light. The relativistic formula for adding velocities $u$ and $v$, where one object is moving at velocity $u$ relative to another object moving at velocity $v$, is given by:

$$
u' = \frac{u + v}{1 + \frac{uv}{c^2}}
$$

Where:
- $u$ is the velocity of the object in one frame,
- $v$ is the velocity of the frame relative to a stationary observer,
- $u'$ is the resultant velocity in the stationary frame, and
- $c$ is the speed of light.

This formula ensures that even if both \( u \) and \( v \) are close to \( c \), their sum \( u' \) will always be less than or equal to \( c \).

## Speed of Light is the Ultimate Speed Limit
One of the fundamental postulates of special relativity is that the speed of light, $c$, is the maximum speed at which information or matter can travel. No object with mass can reach or exceed the speed of light because it would require infinite energy to do so.

This can be seen by examining the relativistic expression for the energy of an object moving with velocity $v$:

$$
E = \frac{mc^2}{\sqrt{1 - \frac{v^2}{c^2}}}
$$

As $v$ approaches $c$, the denominator approaches zero, causing the energy required to accelerate the object to approach infinity. This means that no massive object can be accelerated to or beyond the speed of light, making $c$ the ultimate speed limit in the universe. Only massless particles, such as photons, can travel at the speed of light.

###### Jump to Next [[Knowledge Center/Sidenotes/DraftedTheories/General Relativity]]