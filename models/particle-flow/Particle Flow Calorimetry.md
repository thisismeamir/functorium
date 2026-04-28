# Particle Flow Calorimetry

Particle flow calorimetry requires the energy depositions from individual particles to be traced through the detector and cleanly separated from the depositions of other particles. This reconstruction of individual particles in the event requires both fine granularity calorimeters, or a lack of sophistication in the patter recognition algorithms, will likely lead to confusion in the particle reconstruction.

![[../../attachments/Pasted image 20260428161527.png]]

It is this confusion that is the limiting factor for the particle flow calorimetry:

- Failure to resolve neutral particles (photons or neutral hadrons) from nearby charged hadrons will result in loss of energy. The energy deposit of the neutral particle will be added to those of the charged particle, but the charged particle four-vector will be reconstructed using measurements from the inner detector tracker.
- Failure to associate all the calorimeter energy deposits from a charged particle with correct inner detector track will lead to double counting of energy. The unassociated calorimeter energy  deposits will be used to create a fake neutral particle, whilst the track will still be used to provide the four-vector for the true charged particle.

In order to fully exploit particle flow calorimetry, the confusion must be reduced to the lowest possible level. This places constraints on both the calorimeter hardware and the software pattern recognition algorithms.

## Hardware

In terms of the hardware, accurate inner detector tracking is vital, alongside calorimeters that can longitudinally separate electromagnetic and hadronic showers.

### ECAL

The ECAL must therefore have a large ratio of radiation length to nuclear interaction length. Its Moliere radius must also be small, in order to reduce the transverse spread of electromagnetic showers and aid the separation of photons from nearby charged hadrons. ***The transverse and longitudinal sampling in the ECAL must be sufficient to allow separate clustering and identification of electromagnetic showers by the particle flow algorithms.***

### HCAL

The HCAL must offer longitudinal and transverse segmentation, sufficient to allow separation of neutral hadrons from nearby charged particles. **The HCAL should also aim to fully contain hadronic showers, so a small nuclear interaction length is desirable.** It will be a rather large component of the detector, so its cost and structural properties are also of importance.

---

Fine granularity particle flow calorimetry lives or dies on the quality