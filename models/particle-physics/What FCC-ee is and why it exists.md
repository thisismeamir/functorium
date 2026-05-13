# What FCC-ee is and Why It Exists

## The Hierarchy of Questions in Particle Physics

The Standard Model is the most precisely tested theory in science. It also has at least 5 things badly wrong with it: it doesn't explain dark matter, dark energy, the matter-antimatter asymmetry, neutrino masses, or gravity. Something is missing.

There are two strategies to find it. Go high energy, meaning smash protons harder and hope new particles appear above some mass threshold. Or go high precision, measure known processes so accurately that tiny deviations from the SM prediction reveal the presence of new physics indirectly, even if you can't produce it directly.

The LHC does the first. FCC-ee does the second.

# Why Electron-Positron Instead of Proton-Proton?

Protons are composite. When two protons collide, it's actually a quark or gluon from each one that interacts, and you don't know which, or with what fraction of the proton's momentum. This is called the parton distribution function problem. The collision energy is smeared over s distribution, you cannot tune it.

Electrons and positrons are point particles. When they collide, you know exactly initial state: energy, momentum, quantum numbers. The full centre-of-mass energy goes into the hard process. No hadronic debris. No pile-up in any meaningful sense. The event is clean.

This means FCC-ee can sit precisely on a resonance peak and collect millions of decays of a specific particle with known quantum numbers. That's the operating principle.

# The Four Energy Stages and What They Measure

FCC-ee runs at four centre-of-mass energies, each chosen to sit on or near a specific threshold.

1. $\sqrt{ s } = 91.2\text{ GeV}$: $Z$ pole $\to 5 \times 10^{12} Z\text{ bosons}$.
2. $\sqrt{ s }=160\text{ GeV}$: $WW$ threshold $\to 10^{8} W$ pairs.
3. $\sqrt{ s }=240\text{ GeV}$: $ZH$ break $\to 10^{6}$ Higgs bosons.
4. $\sqrt{ s }=365\text{ GeV}$: $tt$ threshold $\to 10^{6}$ top pairs.

The $Z$-pole run alone produces more $Z$ bosons than all previous experiments combined by a factor of $\sim1000$. This is called the Tera-$Z$ programme. With 5 trillion $Z$ decays you can get measure the $Z$ mass to $100\text{ keV}$ precision, the weak mixing angle $\sin ^{2}\theta_{W}$ to $10^{-5}$, and search for deviations in every $Z$ coupling at the sub-permille level.

# Why Reconstruction Quality is the Limiting Factor

At this level of statistical percision, the bottleneck is no longer how many events you collect. It's how well you measure each one. Consider one example:

## Higgs Mass Measurement

The Higgs mass measurement. At $\sqrt{ s }=240\text{ GeV}$, FCC-ee producess $e^{+}e^{-}\to ZH$ where the $Z$ is used as a tag, you find the $Z$ by its decay products, and whatever recoils against it is the Higgs, regardless of how it decays. The Higgs mass is:
$$
m_{H^{2}} = s + m_{Z^{2}} - 2\sqrt{ s } \cdot E_{\text{recoil}}
$$
So $\sigma(m_{H})$ is directly determined by $\sigma_{E_{\text{recoil}}}$, which is detemined by how well you measure the $Z$ decay products. If $Z \to \mu^{+}\mu^{-}$, your muon momentum resolution sets the limit. If $Z\to qq$, your jet energy resolution sets the limit. The physics reach is locked inside the detector performance. 

Another example: separating $W\to jj$ from $Z \to jj$ using only the diject mass. The $W$ and $Z$ masses differ by only $11\text{ GeV}$. To do this separation cleanly you need a jet energy resolution of roughly $3-4 \% / \sqrt{ E }$. ALEPH at LEP achieved $\sim 60\%/\sqrt{ E}$. The entire FCC-ee detector design, the choice of highly granular silicon-tungsten ECAL, the particle flow approach is driven by this single number.