---
aliases:
status:
  - ongoing
priority:
  - high
tags:
  - "#project"
  - ongoing
---
- [ ] **Phase 1**: Foundations
	- [ ] **Understand the Pandora Architecture**: Read the EPJC paper (Marshal et al. 2015) Map the key components: PandoraSDK, Pandora Monitoring, LCContent, DDMArlinPandora. Understand the Manager Pattern (CaloHit, Cluster, Track, PFO, Vertex Managers) and the role of the XML settings file. (due:: 2026-04-26) #theory #study #cern #ep-fcc
	- [ ] **Build the full Key4Hep + Pandora Stack on Lxplus**: Source the Key4hep nigthtly (`setup.sh`), clone CLDConfig, build Pandora SDK + Pandora Monitoring + LCContent locally. Verify with a ddsim + k4rum CLDReconstruction.py run on 10 gamma events. (due:: 2026-04-26) #setup #ep-fcc #cern 
	- [ ] **Dissect the PandoraSettings XML recipe**: Open CLDConfig's PandoraSettingDefault.xml. Trace the reconstruction order: muon cleaning -> photon clustering -> electron association -> hadronic reclustering. Identify one parameter per step you could tune and note its physical meaning. (due:: 2026-04-26) #experiment #setup #ep-fcc #cern 
	- [ ] **Run ExampleContent step through a toy algorithm**:  Clone PandoraPDF/ExampleContent. Build and run the tor reconstruction. In the debugger, follow one event from PandoraApi::ProcessEvent through algorithm execution and inspect the resulting PFO list. (due:: 2026-04-26) #experiment #code #ep-fcc 
- [ ] **Phase 2:** Simulation
	- [ ] **Simulate single-particle gun events for CLD/ALLEGRO/IDEA**: Use ddsim with the FCC-ee detector geometry to shoot 10 GeV electrons, photons,and pions. Run full reconstruction with DDMarlinPandora. Produce EDM4hep output files for each particle type and confirm PFO collections appear. #code #ep-fcc #cern 
	- [ ] **Write a first custom Pandoa algorithm in C++**: Inherit from pandora::Algorithm, override Run function. Loop over  the current cluster list, print cluster energies to stdout. Register the algorithm in XML. This confirms the full plugin pipeline works end-to-end and you have learned it.
	- [ ] **Tune one LCContent Algorithm Parameter and Measure Impact**: Pick an LCContent algorithm (e.g. Clustering)