Reconstruction is the process starting from the raw detector data, to the actual physical events happening there. It has a long journey through different phases and algorithms. In this model we'd look at it from the basics to the advanced.

**CONTEXT PROMPT** (paste this at the start of every new session)
_I am a physics student, software developer and designer working toward becoming a core contributor to FCC-ee particle reconstruction and particle flow at CERN. I have a background in physics and software but we are building this from first principles — assuming nothing. We are working through a structured curriculum together that goes from foundational particle-matter interactions all the way to the full Key4hep/ACTS/PandoraPFA reconstruction stack. The learning style is: derive things, understand them deeply, then implement toy models in Jupyter notebooks (Python) that actually run and visualize the concepts. No black boxes. The goal is to own this stack completely — physics, algorithms, and software. We are currently on [TOPIC — fill this in]. The full curriculum outline is below. Continue from where we left off, going deep on the current topic with lecture notes, derivations, code, and references._


## FCC-ee Reconstruction & Particle Flow — Complete Curriculum

### Module 0 — The Big Picture

- 0.1 [[What FCC-ee is and why it exists]]
    - The physics case: Z-pole, WW, ZH, tt thresholds
    - Why reconstruction quality directly limits physics reach
    - How a 3% vs 60% jet energy resolution changes what you can measure
- 0.2 [[The reconstruction pipeline as a whole]]
    - Walking through the diagram end to end
    - What "reconstruction" means philosophically — inference under uncertainty
    - The subsystems: tracker, ECAL, HCAL, muon system and their roles
- 0.3 [[The software ecosystem overview]]
    - Key4hep, Gaudi, EDM4hep, podio, DD4hep, ACTS, PandoraPFA — what each one is and why it exists
    - How a real FCC-ee event flows through the software chain
    - Setting up your environment: key4hep stack via CVMFS or Docker
### Module 1 — Particle Interactions with Matter

_This is the physical foundation of every reconstruction algorithm_

- 1.1 [[Charged particles in matter — energy loss]]
    - The ionisation mechanism: what actually happens at the atomic level
    - Deriving the Bethe-Bloch equation from first principles
    - The Bethe-Bloch curve: minimum ionising particles (MIPs), the Bragg peak
    - Restricted energy loss, δ-rays, Landau distribution of energy deposits
    - **Notebook**: plot Bethe-Bloch for π, K, p, e in Silicon and LAr. Implement the full formula.
- 1.2 [[Multiple Coulomb scattering]]
    - Why charged particles don't travel in straight lines
    - Deriving the Highland formula for scattering angle distribution
    - The radiation length X₀ and its physical meaning
    - How scattering limits track momentum resolution at low pT
    - **Notebook**: simulate a track through N material layers with scattering. Watch it walk.
- 1.3 [[Electrons and photons — radiation and pair production]]
    - Bremsstrahlung: why electrons are special, critical energy Ec
    - The radiation length X₀ revisited — now for EM cascades
    - Photon interactions: photoelectric, Compton, pair production — which dominates when
    - **Notebook**: plot the dominance regions as a function of photon energy and Z
- 1.4 [[Electromagnetic showers]]
    - The Heitler model — deriving shower maximum tmax and total track length
    - Longitudinal shower profile: the gamma distribution parameterisation
    - Lateral shower profile: Molière radius, 95% containment
    - Shower-to-shower fluctuations and their impact on energy resolution
    - **Notebook**: implement the Heitler model. Simulate toy EM showers. Plot longitudinal profiles.
- 1.5 [[Hadronic showers]]
    - Why hadronic showers are harder: nuclear interactions, invisible energy
    - The e/h ratio problem and its consequences for calorimetry
    - Hadronic interaction length λI vs radiation length X₀
    - Compensation techniques: hardware vs software
    - **Notebook**: compare EM vs hadronic shower profiles side by side
- 1.6 [[Energy loss of muons]]
    - Why muons are "minimum ionising" through most of the detector
    - Radiative losses at high energy
    - Why muons reach the muon system while pions don't
### Module 2 — Detector Physics

_How detectors convert particle interactions into electronic signals_

- 2.1 [[Silicon detectors — fundamentals]]
    - The p-n junction, depletion zone, reverse bias
    - Electron-hole pair creation: why 3.6 eV per pair in Si
    - Charge collection: drift velocity, carrier lifetime, trapping
    - **Notebook**: model charge collection efficiency vs bias voltage
- 2.2 [[Pixel detectors]]
    - From strip to pixel: 2D position measurement
    - Charge sharing and the η parameter
    - Lorentz drift in a magnetic field
    - Noise sources: thermal, shot, 1/f — the equivalent noise charge (ENC)
    - **Notebook**: simulate charge deposition and sharing across pixels. Implement η-correction.
- 2.3 [[Strip detectors and space points]]
    - Single-sided vs double-sided strips
    - The stereo angle geometry: deriving the 3D space point from two 1D measurements
    - Ghost hits and how to reject them
    - **Notebook**: implement stereo strip space point formation and ghost rejection
- 2.4 [[Calorimeters — sampling vs homogeneous]]
    - The sampling fraction and sampling fluctuations
    - ECAL designs: crystal (CMS), SiW (CLD), LAr (ATLAS)
    - HCAL designs: scintillator-steel, RPC-steel (DHCAL)
    - Signal formation: scintillation light, ionisation charge, silicon diode
    - **Notebook**: model energy resolution σ/E = a/√E ⊕ b ⊕ c/E — fit the three terms
- 2.5 [[Muon detectors]]
    - Drift tubes: isochrone, space-drift-time relation, left-right ambiguity
    - RPCs: fast timing, streamer vs avalanche mode
    - Why the muon system is outside the calorimeters
    - **Notebook**: simulate drift tube hit timing and reconstruct position
- 2.6 [[The FCC-ee detector concepts]]
    - [[CLD]]: the ILD-heritage concept
    - [[IDEA]]: dual-readout calorimetry, ultra-light tracker
    - Key performance numbers: IP resolution, jet energy resolution, particle ID
### Module 3 — Mathematical Foundations of Reconstruction

_The tools every algorithm in the pipeline uses_

- 3.1 [[Linear algebra review with a physics lens]]
    - Covariance matrices: what they mean physically for a track measurement
    - Rotation matrices, Jacobians, error propagation
    - Eigenvalue decomposition: principal components of a cluster shape
    - **Notebook**: propagate a track state through a rotation. Watch errors grow.
- 3.2 [[Probability and statistical inference]]
    - Likelihood, Bayesian inference, χ² as a special case
    - The Gaussian approximation and when it breaks
    - Hypothesis testing: is this a real track or a fake?
    - **Notebook**: build a simple maximum-likelihood fitter for a 1D measurement series
- 3.3 [[Least squares fitting and track fitting]]
    - Ordinary least squares on a straight line track
    - Weighted least squares: why hit errors matter
    - The normal equations and their solution
    - **Notebook**: fit a straight track through 5 layers with different hit resolutions
- 3.4 [[The Kalman filter — full derivation]]
    - The state-space model: what is the "state" of a track
    - Predict step: propagating the state and its covariance through space
    - Update step: incorporating a new measurement — deriving the Kalman gain
    - The information filter dual formulation
    - Smoothing: the Rauch-Tung-Striebel backward pass
    - **Notebook**: implement a full Kalman filter track fitter from scratch in Python. Single particle, 10 layers, magnetic field.
- 3.5 [[Material effects in the Kalman filter]]
    - Multiple scattering as process noise Q
    - Energy loss as a deterministic state update
    - Bethe-Bloch in the propagator
    - **Notebook**: add material effects to your Kalman filter. Watch momentum resolution degrade.
- 3.6 [[The Gaussian Sum Filter]]
    - Why Bremsstrahlung breaks the Kalman filter (non-Gaussian)
    - Representing the state as a mixture of Gaussians
    - The GSF update and mixture reduction
    - **Notebook**: compare KF vs GSF on a simulated electron track with random Brem photons
- 3.7 [[Graph algorithms for reconstruction]]
    - Why reconstruction is fundamentally a graph problem
    - Connected components, minimum spanning trees
    - Density-based clustering: DBSCAN and its calorimeter variant CLUE
    - **Notebook**: implement DBSCAN and CLUE on toy 2D calorimeter data. Compare.
### Module 4 — Tracking

_Turning silicon hits into particle trajectories_

- 4.1 [[Track parameterisation]]
    - The helix in a uniform B-field: full derivation from Lorentz force
    - Perigee representation: (d₀, z₀, φ, θ, q/p)
    - Curvilinear coordinates used in ACTS
    - Converting between representations
    - **Notebook**: implement helix propagation. Generate hits from a known track. Recover parameters.
- 4.2 [[Seed finding]]
    - The combinatorial problem: N hits, find M tracks
    - Doublet and triplet seeding
    - The ACTS SeedFinder algorithm
    - **Notebook**: implement triplet seeding on a toy detector. Measure seed efficiency vs fake rate.
- 4.3 [[Connected Component Analysis]]
    - BFS/DFS on a pixel grid
    - Cluster shape variables: size, charge-weighted CoG, η parameter
    - Merged cluster detection and splitting
    - **Notebook**: full CCA implementation. Simulate two overlapping tracks. Split their clusters.
- 4.4 [[The Combinatorial Kalman Filter]]
    - Extending the KF to track finding: branching and pruning
    - The measurement selector: χ² outlier rejection
    - Track candidate scoring and selection
    - **Notebook**: implement a toy CKF. Multiple tracks, shared hits. Measure efficiency and fake rate.
- 4.5 [[Track quality and performance]]
    - Efficiency, fake rate, clone rate — definitions and measurement
    - Impact parameter resolution: the Glückstein formula
    - Momentum resolution: sagitta method
    - **Notebook**: full performance evaluation of your toy tracker. Plot σ(pT)/pT vs pT.
- 4.6 [[Vertex finding]]
    - Primary vertex finding: beam spot constraint
    - Secondary vertex finding: why it matters for b-tagging
    - The Billoir vertex fitter
    - **Notebook**: implement a simple vertex fitter. Reconstruct a toy B-meson decay.
### Module 5 — Calorimeter Reconstruction

_Turning cell energies into particle showers_

- 5.1 [[Topological clustering]]
    - The signal-to-noise significance ξ
    - Seed, neighbour, border thresholds
    - The 4-1-0 algorithm used at LHC
    - **Notebook**: implement topo-clustering on a 2D toy calorimeter. Tune thresholds.
- 5.2 [[The CLUE algorithm]]
    - Density-based clustering: ρ and δ for each cell
    - Why it scales O(N) and runs on GPU
    - Comparing CLUE to topo-clustering: when each wins
    - **Notebook**: implement CLUE in Python. Benchmark against your topo-clustering implementation.
- 5.3 [[Shower splitting and merging]]
    - Local maxima finding in a cluster
    - Gaussian shower profile for splitting weights
    - The π⁰→γγ case: two photons in one cluster
    - **Notebook**: simulate overlapping EM showers. Implement splitting. Measure position resolution.
- 5.4 [[Calorimeter calibration]]
    - EM scale calibration using π⁰→γγ
    - Hadronic calibration: local hadron calibration weights
    - Software compensation with a BDT/NN
    - **Notebook**: train a simple NN software compensator on toy hadronic showers
- 5.5 [[High-granularity calorimetry]]
    - Why FCC-ee uses SiW ECAL with ~100M cells
    - Shower shape variables: FisherZ, shower width, Zernike moments
    - ML-based particle ID in the calorimeter
    - **Notebook**: compute shower shape variables. Train a classifier: photon vs π⁰ vs hadron.
### Module 6 — Particle Flow

_The core of FCC-ee reconstruction_

- 6.1 [[The particle flow concept]]
    - Deriving the confusion term: when does PFA win and lose
    - The detector design requirements imposed by PFA
    - Historical context: from ALEPH energy flow to modern PFA
    - **Notebook**: derive and plot jet energy resolution as a function of confusion term. Show the PFA advantage.
- 6.2 [[Track-cluster matching]]
    - Extrapolating tracks to calorimeter surface
    - Distance metrics: ΔR, Δφ, ΔE/p
    - The χ² matching and its failure modes
    - **Notebook**: implement track-cluster matching on toy events. Measure matching efficiency vs purity.
- 6.3 [[Cluster subtraction]]
    - Expected energy deposit of a charged track in ECAL/HCAL
    - Subtracting the charged contribution from clusters
    - Handling the case where subtraction goes negative
    - **Notebook**: implement a complete toy PFA. Measure jet energy resolution before and after.
- 6.4 [[PandoraPFA architecture]]
    - The algorithm chain: how Pandora is organised
    - Writing your own Pandora algorithm in C++
    - The ArborPFA variant and its tree-based approach
    - Key configuration parameters and how to tune them
- 6.5 [[ML-based particle flow]]
    - MLPF: treating PFA as a graph neural network problem
    - GRAPE and related approaches
    - How GNNs handle the combinatorial assignment problem
    - **Notebook**: implement a simple GNN PFA using PyTorch Geometric on toy events
- 6.6 [[Performance evaluation]]
    - Jet energy resolution measurement methodology
    - W/Z mass separation as the benchmark
    - PFA efficiency and confusion rates by particle species
    - **Notebook**: full PFA performance suite. Reproduce the key FCC-ee CDR performance plots.
### Module 7 — The Key4hep Software Stack

_Writing real reconstruction code_

- 7.1 [[The Gaudi framework]]
    - Algorithms, Tools, Services, Data handles
    - The functional algorithm pattern: Transformer, Producer, Consumer
    - Event data flow: TES, whiteboard model
    - **Exercise**: write your first Gaudi algorithm that reads hits and prints them
- 7.2 [[EDM4hep and podio]]
    - The EDM4hep data model: every collection type
    - podio: how the I/O layer works, ROOT backend
    - Writing and reading collections
    - **Exercise**: write a podio reader that loops over events and computes hit multiplicity per layer
- 7.3 [[DD4hep — detector description]]
    - Compact XML geometry description
    - DDSegmentation: encoding/decoding cellIDs
    - Surface maps for tracking
    - **Exercise**: load the CLD geometry, decode a cellID to (layer, module, cell), print its 3D position
- 7.4 [[ACTS in depth]]
    - TrackingGeometry from DD4hep
    - The Propagator: RKN stepper + navigator
    - CKF: configuration, measurement selector, track container
    - **Exercise**: run ACTS CKF on CLD simulation output. Plot tracking efficiency vs pT and η.
- 7.5 [[Writing a digitisation algorithm]]
    - The full Gaudi Transformer pattern
    - Implementing planar silicon digitisation: smearing, threshold, noise
    - Validating against DDPlanarDigi
    - **Exercise**: write your own digitiser. Compare cluster properties to the reference implementation.
- 7.6 [[Writing a clustering algorithm]]
    - Implementing your CLUE notebook as a proper Gaudi algorithm
    - Interfacing with EDM4hep Cluster collections
    - Performance validation on single-particle samples
    - **Exercise**: deploy your CLUE implementation in the k4RecCalorimeter chain
- 7.7 [[The full simulation-to-analysis chain]]
    - ddsim → digitisation → reconstruction → PFOs → FCCAnalyses
    - Steering files, options files, batch submission
    - **Exercise**: run the complete chain on e+e-→ZH→bbνν. Reconstruct the Higgs mass.
### Module 8 — Advanced Topics and Research Frontier

_Where you start contributing_

- 8.1 [[4D tracking — timing in reconstruction]]
    - Why timing matters at FCC-ee: beam-induced background rejection
    - Time-of-flight particle ID
    - Incorporating timing into the Kalman filter
- 8.2 [[Flavour tagging]]
    - B and charm tagging: the physics of displaced vertices
    - LCFI+ and ParticleNet-based taggers
    - Jet flavour tagging performance at FCC-ee
- 8.3 [[Dual-readout calorimetry (IDEA concept)]]
    - Scintillation vs Cherenkov signal separation
    - Hardware compensation: recovering the invisible energy
    - Reconstruction challenges specific to dual-readout
- 8.4 [[ML in reconstruction — the frontier]]
    - Track finding with GNNs: Exa.TrkX, ACORN
    - End-to-end reconstruction with transformers
    - Where ML genuinely helps vs where classical algorithms still win
- 8.5 [[Contributing to Key4hep]]
    - The open-source workflow: GitHub, PRs, CI
    - Where the actual gaps are in FCC-ee reconstruction software
    - How to identify a problem worth solving and pitch it

- [[List of Reconstruction References]]