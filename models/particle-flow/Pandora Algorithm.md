![[../../attachments/Pasted image 20260428184604.png]]

# Algorithms

The reconstruction of events in a fine granularity detector, such as ILD, uses over 60 different Pandora algorithms. These algorithms are well-understood and have been documented. The basic reconstruction operations performed by the default set of Pandora algorithms is briefly summarized below:

- Calorimeter cells are clustered using a simple cone based clustering algorithm, working out-wards in the calorimeters from the front of the ECAL to the back of the HCAL. Clusters can be seeded by the projection of inner detector tracks to the front face of the ECAL.
- The clustering algorithm is configured so that it tends to split up the energy deposits from individual particles, rather than risk accidentally merging particles so early in the reconstruction. The resulting proto-clusters are then carefully merged together by a series of algorithms that implement well-motivated topological rules. The fine granularity and tracking capabilities of the calorimeter are exploited to merge clusters whilst making very few mistakes.
- 