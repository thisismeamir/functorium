![[../../attachments/Pasted image 20260428184604.png]]

# Algorithms

The reconstruction of events in a fine granularity detector, such as ILD, uses over 60 different Pandora algorithms. These algorithms are well-understood and have been documented. The basic reconstruction operations performed by the default set of Pandora algorithms is briefly summarized below:

- Calorimeter cells are clustered using a simple cone based clustering algorithm, working out-wards in the calorimeters from the front of the ECAL to the back of the HCAL. Clusters can be seeded by the projection of inner detector tracks to the front face of the ECAL.
- The clustering algorithm is configured so that it tends to split up the energy deposits from individual particles, rather than risk accidentally merging particles so early in the reconstruction. The resulting proto-clusters are then carefully merged together by a series of algorithms that implement well-motivated topological rules. The fine granularity and tracking capabilities of the calorimeter are exploited to merge clusters whilst making very few mistakes.
- The calorimeter clusters are carefully associated to the inner detector tracks, by comparing the properties of the clusters with the projected track states at the front face of the calorimeter. Linear and helix fits to the clusters and tracks are used to help make the correct associations.
- If the energy of a calorimeter does not agree with the associated track momentum, the cluster can be reconfigured by the statistical reclustering algorithms. The relevant calorimeter cells can be passed to a series of differently configured clustering algorithms to see if a configuration with better track-cluster compatibility can be found.
- Fragment-removal algorithms look for neutral clusters (no track-association) that are actually fragments of nearby charged clusters (with track-associations). The algorithm look for evidence of associations between nearby neutral and charged clusters and evaluate the changes in track-cluster compatibility that would occur if the clusters were merged.
- Particle flow objects (PFOs) are formed. If a particle contains tracks and associated clusters, the particle properties are extracted from the tracks. For neutral particles, the calorimeter information is used.
- Particle identification algorithms flag the reconstructed particles with PDG codes, identifying charged leptons. photon identification is considered throughout the algorithms, but can be finalized at this stage.

These algorithms have provided the particle flow reconstruction for the majority of studies performed for the ILD Detailed Baseline Design and the CLIC Conceptual Design Report.