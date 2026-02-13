# Introduction

The precision measurement of the $W$ boson mass in $e^+e^-\rightarrow WW$ events relies critically on accurate reconstruction of jet kinematics. In the kinematic fitting procedure described in the main $W$ mass analysis, the measurement uncertainties are encoded in a $16\times16$ covariance matrix that propagates detector resolution effects into the fitted mass distributions. The present angular resolution study provides the *empirical foundation* for constructing this covariance matrix by quantifying the detector performance in reconstructing jet angular and momentum parameters across multiple center-of-mass energies.

This analysis implements a comprehensive jet-level resolution study using Monte Carlo $WW$ samples at seven center-of-mass energies ranging from $\sqrt{ s } = 160\text{ GeV}$ (near production threshold) to $365 \text{ GeV}$ (well above threshold). 

For each event, reconstructed jets are matched to generator-level jets using a $\Delta R$ criterion, and the differences in kinematic parameters—specifically the polar angle $\theta$, azimuthal angle $\phi$, logarithmic momentum $x=\ln p$, and energy scale factor $\alpha$—are calculated. These resolution measurements directly correspond to the parametrization employed in the kinematic fit (Equations 7.20–7.23 of the reference[^1]), where each jet is described by the four-component vector $(\alpha, \theta,\phi,x)$. 

By extracting the widths and correlations of the $\Delta \theta,\Delta \phi,\Delta x$ and $\Delta \alpha$ distributions, this study enables the construction of a realistic, energy-dependent covariance matrix to replace the simplified placeholder currently used in the $W$ mass reconstruction.

The analysis proceeds through several stages: 

1. Jet clustering using the `ee_kt` algorithm in exclusive 4-jet mode, geometric matching between reconstructed and generator jets.
2. Calculation of resolution parameters for matched jet pairs,
3. Statistical filtering to remove poorly reconstructed outliers.

The outputs consist of per-jet resolution distributions that can be directly fitted to extract the diagonal and off-diagonal elements of the covariance matrix, accounting for both measurement uncertainties and potential correlations between jet parameters.

This document provides an analysis of the code and the results. For sake of completeness, we'd explain every line of the code. After that we'd take a look at the results obtained, and focus on the problems arising in them.

# Code Analysis

## Configuration

The analysis starts with some standard configurations, and initialization. 
```python
import ROOT, os
from glob import glob

ROOT.gROOT.SetBatch(True)

# ================================================
# CONFIGURATION: Multiple Energy Folders
# ================================================

# fraction of events to be taken into analysis
fractions = 1e-6
# Number of chunks per process.
chunks = 1  
# Base input directory
inputDir = "/eos/experiment/fcc/ee/generation/DelphesEvents/winter2023/IDEA/"
# Number of threads to use
nCPUS = 10
# Produces ROOT TTrees
doTree = True
# Output directory (will be created by fccanalysis)
outputDir = "path/to/output/directory"
# Process dictionary
procDict = "FCCee_procDict_winter2023_IDEA.json"
# Header files for analysis
includePaths = [
	"headers/jetMatching.h", # Jet Matching Function
	"headers/getDeltaTheta.h", 
	"headers/getDeltaPhi.h", 
	"headers/getDeltaEta.h",
	"headers/getDeltaMass.h",
	"headers/getXGen.h",
	"headers/getXReco.h",
	"headers/getElement.h",
	"headers/jetPartonMatching.h",
	"headers/getDeltaAlphaParton.h",
	"headers/filterValues.h",
	"headers/selectQuarks.h"
]
# Define energy configurations
energy_configs = {
    "p8_ee_WW_ecm160": {
        "fraction": fractions,
        "output_suffix": "ecm160",
        "label": "√s = 160 GeV"
    },
    # ... 7 energy points in total.
}

# Filtering criteria for delta values
filter_config = {
    "delta_theta": {"min": -0.02, "max": 0.02},
    "delta_phi": {"min": -0.02, "max": 0.02},
    "delta_eta": {"min": -0.1, "max": 0.1},
    "delta_x": {"min": -0.6, "max": 0.6},
    "delta_alpha": {"min": -0.25, "max": 0.25}
}

# ================================================
# Build processList for FCCAnalyses
# ================================================
processList = {}
for process_name, config in energy_configs.items():
    # Get all files for this process
    file_pattern = os.path.join(inputDir, process_name, "events_*.root")
    all_files = glob(file_pattern)

    if all_files:
        # Add to processList with the output suffix
        processList[f"{process_name}"] = {
            "fraction": config['fraction'],
            "chunks": chunks,
            "output": f"angular_resolution_{config['output_suffix']}"
        }
        print(f"Added process: {process_name} ({config['label']}) - {len(all_files)} files found")
    else:
        print(f"WARNING: No files found for {process_name}")
```
As this section is only a configuration before starting our analysis everything is self-explanatory. In summary:

1. We've declared some variables to enhance reproducibility and testing.
2. We wrote functionality that would create our event list, and load our desired events into the system.
3. We wrote functionality that help us filter our final outputs in the desired range.

## Analysis Pipeline

### Lepton Removal

We start by creating a pure hadronic final state for jet clustering. The reason is that $WW\rightarrow 4\text{ quarks}$ is fully hadronic; leptons indicate different decay modes. 

```python
# ---------------------------  
# Remove identified leptons  
# ---------------------------  
df = df.Alias("Electron0", "Electron#0.index")  
df = df.Alias("Muon0", "Muon#0.index")  
df = df.Alias("Photon0", "Photon#0.index")  
df = df.Define("ele_all", "FCCAnalyses::ReconstructedParticle::get(Electron0, ReconstructedParticles)")  
df = df.Define("mu_all", "FCCAnalyses::ReconstructedParticle::get(Muon0, ReconstructedParticles)")  
df = df.Define("pho_all", "FCCAnalyses::ReconstructedParticle::get(Photon0, ReconstructedParticles)")  
df = df.Define("RP_noPho", "FCCAnalyses::ReconstructedParticle::remove(ReconstructedParticles, pho_all)")  
df = df.Define("RP_noEle", "FCCAnalyses::ReconstructedParticle::remove(RP_noPho, ele_all)")  
df = df.Define("reco_clean", "FCCAnalyses::ReconstructedParticle::remove(RP_noEle, mu_all)")
```

### Parton Selection

Select quarks (PDG ID 1-6) with status 2 or 3 (partons after PS, before hadronization), in this lines we've used `selectQuarks` function, which is explained later.
```python 
df = df.Define("partons_all", "selectQuarks(Particle)")  
df = df.Define("n_partons", "partons_all.size()")  
```
Get the 4 partons from $WW\to 4 \text{ quarks}$:

```python
df = df.Filter("n_partons == 4", "Require only 4 partons")
```
Calculate parton kinematics using `FCCAnalyses::MCParticle` functions:
```python
# Calculate parton kinematics using FCCAnalyses::MCParticle functions  
df = df.Define("parton_energies", "FCCAnalyses::MCParticle::get_e(partons_all)")  
df = df.Define("parton_eta", "FCCAnalyses::MCParticle::get_eta(partons_all)")  
df = df.Define("parton_phi", "FCCAnalyses::MCParticle::get_phi(partons_all)")  
df = df.Define("parton_y", "FCCAnalyses::MCParticle::get_y(partons_all)")
```
#### `selectQuark` Function

```cpp
#include <cmath>  
#include <set>  
  
ROOT::VecOps::RVec<edm4hep::MCParticleData> selectQuarks(  
    const ROOT::VecOps::RVec<edm4hep::MCParticleData>& particles  
) {  
    ROOT::VecOps::RVec<edm4hep::MCParticleData> result;  
  
    // Set of quark PDG IDs (up, down, strange, charm, bottom, top)  
    std::set<int> quark_pdgs = {1, 2, 3, 4, 5, 6, -1, -2, -3, -4, -5, -6};  
  
    for (const auto& p : particles) {  
        // Select quarks with status 23 (outgoing from hard process)          
        if (quark_pdgs.count(p.PDG) > 0 && p.generatorStatus == 23) {  
            result.push_back(p);  
		}    
	}  
    return result;  
}
```
##### Purpose

This function filters Monte Carlo truth particles to extract the four quarks originating from the W boson decays in $e^+e^- \to WW \to 4q$ events. It selects quarks at the parton level—after the hard scattering process but before hadronization—which are necessary for measuring jet reconstruction performance against truth-level kinematics.

##### Algorithm Description

The function implements a two-stage selection criterion based on particle type and generator status:
##### Quark Identification (PDG Code Filter)

The algorithm first defines a set containing the PDG identification codes for all six quark flavors and their antiparticles:

- Up ($u$): $\pm 1$
- Down ($d$): $\pm 2$
- Strange ($s$): $\pm 3$
- Charm ($c$): $\pm 4$
- Bottom ($b$): $\pm 5$
- Top ($t$): $\pm 6$

This set enables efficient lookup to identify whether a given particle is a quark or antiquark.

##### Generator Status Selection

The Monte Carlo event record contains particles at various stages of the event generation process. This function selects quarks with specific generator status codes that identify partons at the appropriate stage:

- **Status 23**: Particles outgoing from the hard process (in Pythia 8 conventions, this indicates particles directly from the matrix element calculation before parton showering)

This dual-status selection ensures the function captures the correct parton-level quarks regardless of minor variations in how different Monte Carlo generators assign status codes. These are the "true" quarks before they fragment into hadrons, making them the appropriate reference objects for measuring jet angular resolution.

##### Selection Logic

For each particle in the input collection, the algorithm:

1. Checks if $|\text{PDG}| \in {1,2,3,4,5,6}$ using set membership (`quark_pdgs.count(p.PDG) > 0`)
2. Verifies the generator status is $23$: $\text{status} = 23$
3. If both conditions are satisfied, adds the particle to the output collection

Mathematically, a particle $p$ is selected if: 

$$\text{selected}(p) = \begin{cases} \text{true} & \text{if } |\text{PDG}_p| \in {1,2,3,4,5,6} \land \text{status}_p = 23 \\ \text{false} & \text{otherwise} \end{cases}$$
##### Expected Output

For a typical $WW \to 4q$ event, this function returns exactly four quarks: two from $W^+ \to q_1\bar{q}_2$ and two from $W^- \to q_3\bar{q}_4$. These parton-level quarks serve as the truth reference for matching to reconstructed jets and measuring detector resolution effects. In the context of the angular resolution analysis, the energies and angular coordinates of these selected quarks are subsequently compared to the kinematics of jets reconstructed from detector-level particles.

### Generator-Level Jet Clustering

```python
df = df.Define("MC_final", "FCCAnalyses::MCParticle::sel_genStatus(1)(Particle)")
df = df.Define("Particle_px", "FCCAnalyses::MCParticle::get_px(MC_final)")
df = df.Define("Particle_py", "FCCAnalyses::MCParticle::get_py(MC_final)")
df = df.Define("Particle_pz", "FCCAnalyses::MCParticle::get_pz(MC_final)")
df = df.Define("Particle_e", "FCCAnalyses::MCParticle::get_e(MC_final)")

df = df.Define("pseudo_jets_gen",
               "FCCAnalyses::JetClusteringUtils::set_pseudoJets(Particle_px, Particle_py, Particle_pz, Particle_e)")
df = df.Define(f"jets_gen_obj4",
               "JetClustering::clustering_ee_kt(2, 4, 0, 0)(pseudo_jets_gen)")
df = df.Define(f"jets_gen4",
               "FCCAnalyses::JetClusteringUtils::get_pseudoJets(jets_gen_obj4)")
```


### Reconstructed Jet Clustering

```python
df = df.Define("Reco_px", "FCCAnalyses::ReconstructedParticle::get_px(reco_clean)")
df = df.Define("Reco_py", "FCCAnalyses::ReconstructedParticle::get_py(reco_clean)")
df = df.Define("Reco_pz", "FCCAnalyses::ReconstructedParticle::get_pz(reco_clean)")
df = df.Define("Reco_e", "FCCAnalyses::ReconstructedParticle::get_e(reco_clean)")

df = df.Define("pseudo_jets_reco",
               "FCCAnalyses::JetClusteringUtils::set_pseudoJets(Reco_px, Reco_py, Reco_pz, Reco_e)")
df = df.Define(f"jets_reco_obj4",
               f"JetClustering::clustering_ee_kt(2,4, 0, 0)(pseudo_jets_reco)")
df = df.Define(f"jets_reco4",
               f"FCCAnalyses::JetClusteringUtils::get_pseudoJets(jets_reco_obj4)")

df = df.Define("n_jets_gen", "jets_gen4.size()")
df = df.Define("n_jets_reco", "jets_reco4.size()")
df = df.Filter("n_jets_gen == 4 && n_jets_reco == 4")
```

---
[^1]: M. Béguin, ‘Calorimetry and W mass measurement for future experiments’, PhD Thesis, IRFU, Saclay, CERN, 2019.
