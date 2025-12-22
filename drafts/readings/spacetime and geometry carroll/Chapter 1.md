# Basics as we all know

Gravitation went through a great transition in the 20th century going from a field theory upon bodies into a geometry. 

We can begin by remembering out previous theory of gravity, that of Newton. There are two basic elements: an equation for the gravitational field as influenced by matter, and an equation for the response of matter to this field. This conventional Newtonian statement of these rules is in terms of forces between particles, the force between two objects of masses $M$ and $m$ separated by a vector $\vec r  = r\vec{e_{r}}$ is the famous inverse-square law:

$$
\mathbf{F} = \frac{G M m}{r^2}\mathbf{e}_{r}
$$
and this force acts on a particle of mass $m$ to give it an acceleration according to Newton's second law,
$$
\mathbf{F} = m\mathbf{a}
$$
Equivalently, we could use the language of the gravitational potential $\Phi$; the potential is related to the mass density $\rho$ by Poisson's equation,
$$
\nabla^2 \Phi = 4\pi G\rho
$$
and the acceleration is given by the gradient of the potential,
$$
\mathbf a = \nabla\Phi
$$
In terms of how Einstein viewed the problem, it is a bit different, we first have an equation for the geometry of spacetime influenced by the distribution of matter and energy:
$$
R_{\mu\nu} - \frac12 R g_{\mu\nu} = \kappa T_{\mu\nu}
$$
The response of matter to spacetime curvature is somewhat easier to grasp: Free particles move along paths of "shortest possible distance", or geodesics. In other words, particles try their best to move on straight lines, but in a curved spacetime there might not be any straight lines, so they do the next best thing. 
$$
\frac{d^2 x^\mu}{d\lambda^2} + \Gamma^{\mu}_{\rho\sigma}\frac{dx^\rho}{d\lambda}\frac{dx^\sigma}{d\lambda}  =0
$$
# Space And time, Separately and Together
“Special relativity is a theory of the structure of spacetime, the background on which particles and fields evolve. SR serves as a replacement for Newtonian mechanics, which also is a theory of the structure of spacetime.” (Carroll, 2014, p. 3)

“Spacetime is a four-dimensional set, with elements labeled by three dimensions of space and one of time.” (Carroll, 2014, p. 4)

“An individual point in spacetime is called an event. The path of a particle is a curve through spacetime, a parameterized one-dimensional set of events, called the worldline. Such a description applies equally to SR and Newtonian mechanics. In either case, it seems clear that "time" is treated somewhat differently than "space"; in particular, particles always travel forward in time, whereas they are free to move back and forth in space.” (Carroll, 2014, p. 4)

“The notion of simultaneity, when two events occur at the same time, is unambiguously defined.” (Carroll, 2014, p. 4)

“Trajectories of particles will move ever forward in time, but are otherwise unconstrained; in particular, there is no limit on the relative velocity of two such particles.” (Carroll, 2014, p. 4)

“Although we use two distinct numbers to label each point, the numbers are not the essence of the geometry, since we can rotate axes into each other while leaving distances unchanged.” (Carroll, 2014, p. 6)

“In Newtonian physics this is not the case with space and time~ there is no useful notion of rotating space and time into each other. Rather, the notion of "all of space at a single moment in time" has a meaning independent of coordinates.” (Carroll, 2014, p. 6)

# Lorentz Transformations

We can now consider coordinate transformations in spacetime at a somewhat more abstract level than before. One simple variety are the translations, which merely shift the coordinates:
$$
x^\mu = x^{\mu'} = \delta_\mu^{\mu'}(x^\mu + a^\mu)
$$
where $a^\mu$ is a set of four fixed numbers.
“Translations leave the differences 6.xμ unchanged, so it is not remarkable that the interval is unchanged. The other relevant transformations include spatial rotations and offsets by a constant velocity vector, or boosts~ these are linear transformations, described by multiplying xμ by a (spacetime-independent) matrix” (Carroll, 2014, p. 12)