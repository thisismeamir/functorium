# What Reconstruction Actually Is?

Reconstruction is statistical inference. You observe a set of electronic signals in a detector. You want to infer what particles produced them, their identities, momenta, charges, origin vertices. The detector is a probabilistic measurement device: each true particle configuration produces a distribution over observable signals, not a single point. Reconstruction inverts this.

Every algorithm in the pipeline is solving an inference problem under uncertainty. The Kalman filter is Bayesian filtering. Clustering is unsupervised classification. Particle flow is a matching and assignment problem. The quality of reconstruction is determined by how well each algorithm handles noise, ambiguity, and the propagation of uncertainty.

# Walking Through the Path

![[Pasted image 20260508010241.png]]

Start at the left: raw detector readout. Every detector channel that fired, a pixel, a calorimeter, a muon wire etc. reports a digital number: an ADC count, a timestamp, a charge. At this stage you have a list of `(channel_id, value)` pairs. Nothing is reconstructed. You don't even have positions yet. A `channel_id` is just an integer until you look it up in the detector geometry. 

Digitization is the first step. In real data this step doesn't exist, you already have raw signals. In simulation, Geant4 gives you truth-level energy deposits (`SimHits`), and digitization models the detector response, charge drift, noise, threshold, electronic shaping. The output mimics what real hardware would produce.

Then the pipeline splits into four parallel streams, one per subsystem:

1. **Pixel and Strip streams (Silicon Tracking Detectors)**: The goal is to go from raw channel hits to 3D position measurements (hits) that a track fitter can use. Pixels go through CCA to form clusters. Strips go through space point formation to combine two 1D measurements into one 3D point. Both feed into tracking.
2. **Tracking**: Takes 3D hits from pixels and strips and reconstructs trajectories, helices in the magnetic field. This is computationally the hardest step. the output is a list of tracks, each with a fitted momentum vector, impact parameters, and a covariance matrix encoding the uncertainty on everything.
3. **Calorimeter Stream**: Cells above noise threshold are grouped into topological clusters, then calibrated. The calibration step corrects for the sampling fraction, the $e / h$ ration problem, and dead material losses.
4. **Muon Stream**: Hits in the muon stations are grouped into segments (short straight line stubs within one station), then linked across stations into full muon tracks.

All four streams converge at Particle Flow. This is where the magic happens. PFA takes tracks, calibrated clusters, and muon trackers, and builds one reconstructed particle per real particle in the event. The output is what every physics analysis uses.

# The Philosophy of Uncertainty Propagation

Every step produces objects with associated uncertainties. A cluster has an energy and a $\sigma(E)$. A track has a momentum and a $5\times5$ covariance matrix. These uncertainties aren't optional metadata; they are primary input to the next step. The Kalman filter in tracking uses hit covariance matrices to weight measurements. PFA uses track momentum resolution and cluster energy resolution to decide which measurement to trust. If you get the uncertainties wrong at one step, every downstream step degrades.

This is why understanding the physics of each detector and each algorithm is not optional. You cannot tune a covariance matrix you don't understand.