# Particle Flow Calorimetry

Particle flow calorimetry requires the energy depositions from individual particles to be traced through the detector and cleanly separated from the depositions of other particles. This reconstruction of individual particles in the event requires both fine granularity calorimeters, or a lack of sophistication in the patter recognition algorithms, will likely lead to confusion in the particle reconstruction.

![[../../attachments/Pasted image 20260428161527.png]]

It is this confusion that is the limiting factor for the particle flow calorimetry:

- Failure to resolve neutral particles (photons or neutral hadrons) from nearby charged hadrons will result in loss of energy. The energy deposit of the neutral particle will be added to those of the charged particle, but the charged particle four-vector will be reconstructed using measurements from the inner detector tracker.
- Failure to associate all the calorimeter energy deposits from a charged particle with correct inner detector track will lead to double counting of energy. The unassociated calorimeter energy  deposits will be used to create a fake neutral particle, whilst the track will still be used to provide the four-vector for the true charged particle.