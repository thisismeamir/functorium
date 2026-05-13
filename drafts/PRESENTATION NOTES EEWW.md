**Slide 1 — Channel & Setup**

We are working on the fully hadronic WW channel at FCC-ee. Both W bosons decay into quark pairs, giving us a clean 4-jet final state with no missing energy — which means the kinematics are fully constrained, and that is a big advantage for a mass measurement. It is also the highest branching ratio WW channel at around 46%, so we have plenty of statistics to work with. We are running over the IDEA detector simulation using Delphes, across seven center-of-mass energy points from 160 up to 365 GeV. The analysis has two stages that feed into each other — first we characterize the jet resolution, then we use that to do a kinematic fit for the W mass.

---

**Slide 2 — Angular Resolution**

The first stage is about understanding how well the detector reconstructs the jets. We cluster both the generator-level and reconstructed particles into exactly 4 jets using the ee-kt algorithm, then match them by deltaR. From the matched pairs we compute the residuals in theta, phi, the log-momentum x, and the energy scale alpha. These plots are preliminary — the angular residuals look reasonable, but we currently have a known issue in the alpha distribution that we are actively debugging, most likely in either the jet matching or the parton energy calculation. Once this is sorted, we fit each distribution with a Crystal Ball to extract the resolution parameters, which then go directly into the covariance matrix of the kinematic fit.

---

**Slide 3 — Kinematic Fit**

The second stage is the kinematic fit. We impose energy-momentum conservation — that is the 4C fit — and then add a fifth constraint requiring the two dijet masses to be equal, which is the 5C fit. This second constraint is what collapses the combinatorial ambiguity into a single W mass peak, as you can see in the bottom left plot. The minimisation runs over all three possible jet pairings and picks the one with the best chi-squared. The plots here use a placeholder covariance matrix, so the agreement with the reference is qualitative at this stage. The structure is correct and the fit is working — the main thing missing is the realistic covariance from Step 1.

---

**Slide 4 — Current Status**

To summarize where we are: Step 1 is running but has a known bug in the alpha residuals that we are fixing. Step 2 is complete and validated against a reference using a placeholder covariance. The two pieces are essentially ready to be connected — we are one debugging session away from having the full pipeline working end to end.

---

**Slide 5 — Next Steps**

The immediate priority is fixing the alpha bug in Step 1. Once that is done we connect the two stages and replace the placeholder covariance with the real one. After that the plan is to improve the treatment of the center-of-mass energy, which is currently hardcoded. Finally, once the pipeline is validated at threshold we extend the comparison across all seven energy points. That is the roadmap for the next few weeks.


