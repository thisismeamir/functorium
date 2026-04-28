# Master's Thesis: SBI Pipeline for Cosmic String Microphysics in PTA Data
## Comprehensive Project Plan & Reading List

---

## 1. Project Overview and Merged Scope

### Core Research Statement

You are building a **Simulation-Based Inference (SBI) pipeline for constraining cosmic string
microphysics from NANOGrav Pulsar Timing Array data**, with an emphasis on the following
scientific questions:

1. Can TMNRE (Truncated Marginal Neural Ratio Estimation) constrain cosmic string
   parameters (Gμ, p, loop model) from the NANOGrav 15-year dataset more efficiently
   than MCMC?
2. Can the pipeline perform **implicit source separation** — recovering the cosmic string
   signal while treating the SMBHB background as a nuisance?
3. As a software side-product: the pipeline architecture (the "PTAforge" layer) provides a
   modular, GPU-accelerated forward simulator usable in future PTA-SBI research.

### Merging the Two Proposals

| Proposal 1 (SBI Pipeline) | Proposal 2 (PTAforge) | Merged Thesis |
|---|---|---|
| Physics focus: cosmic strings, PTA band | Software focus: modular simulator | Physics-first, with clean software architecture |
| TMNRE + swyft inference backend | JAX/PyTorch batch simulation | JAX-accelerated simulator as part of the pipeline |
| NANOGrav 15yr application | Validation against PTArcade | Apply to real data AND validate against MCMC |
| Includes source separation (Ch. 5) | N/A | Source separation is the distinguishing scientific result |

**The key reframe your professor endorsed**: PTAforge is not a separate deliverable — it is the
forward-simulation layer of the SBI pipeline. Its modularity makes the pipeline extensible, and
its design merits a software paragraph in the methods section, but it is not the headline.

### Physics vs. Software Balance (per your professor's note)

The physics questions that must drive the proposal narrative are:
- What do the cosmic string parameters (Gμ, reconnection probability p, loop distribution
  model) physically mean, and why does the PTA band probe them?
- Why is SMBHB contamination a fundamental problem, and why does implicit
  marginalization solve it in a way MCMC cannot?
- What is the significance of the NANOGrav 15yr signal in the cosmological interpretation
  context?

The software work (JAX simulator, modular architecture, GPU batching) must be framed as
enabling the physics — not as an end in itself.

---

## 2. Five-Phase Project Plan (15 months)

### Phase 1 — Foundation Studies (Months 1–3)

**Goal**: Build deep understanding of the three pillars: PTA physics, cosmic string theory, and
SBI methodology. No code beyond toy examples.

**Milestones**:
- Reproduce the NANOGrav 15yr detection statistics from the paper
- Implement a simple VOS solver from scratch in Python (no library)
- Run TMNRE on a toy two-moon posterior using swyft
- Write a 5-page literature review connecting the three areas

**Key deliverable**: Written summary of the theoretical framework you will use, including the
explicit form of Ω_gw(f; Gμ, p) you plan to implement.

---

### Phase 2 — Implementation and Simple Testing (Months 4–6)

**Goal**: Build the forward simulator (PTAforge core) and validate it. Run first SBI
experiments on mock data.

**Milestones**:
- Working VOS + BOS/LRS loop distribution code in JAX
- NANOGrav noise injection working against the free-spectrum posterior
- Compression network (1D CNN) trained and producing summary statistics
- First TMNRE posterior on mock data, compared to MCMC with PTArcade

**Key deliverable**: Internal validation report comparing simulator outputs to PTArcade on
the power-law SGWB case.

---

### Phase 3 — Official Research and Development (Months 7–9)

**Goal**: Apply the validated pipeline to the real NANOGrav 15yr dataset. Develop the source
separation experiment (Chapter 5 / work-group proposal).

**Milestones**:
- Posterior constraints on (Gμ, p, loop model) from NANOGrav 15yr
- Joint SGWB simulation (cosmic strings + SMBHB) implemented
- TMNRE implicit marginalization over SMBHB parameters running on cluster
- Bias quantification experiment: inject strings-only, fit with SMBHB-contaminated model

**Key deliverable**: First draft results section with posterior plots.

---

### Phase 4 — Testing, Re-evaluation and Analysis (Months 10–12)

**Goal**: Validate inference quality, run simulation-based calibration (SBC), compare to
literature, and draw conclusions.

**Milestones**:
- SBC coverage checks completed
- Fisher forecasts computed for the joint model
- Comparison against existing PTArcade/ENTERPRISE analyses finalized
- GPU performance benchmarking of the simulator (targeting 10^4 sims/min)

**Key deliverable**: Complete results and discussion section, with figures publication-ready.

---

### Phase 5 — Writing, Finalization and Publication (Months 13–15)

**Goal**: Write the thesis and prepare a journal paper (target: Journal of Cosmology and
Astroparticle Physics or Physical Review D).

**Milestones**:
- Full thesis draft submitted for supervisor feedback (month 13)
- Revised thesis (month 14)
- Open-source code released with documentation and CI/CD
- Preprint submitted to arXiv (month 15)
- Journal submission prepared

**Key deliverable**: Thesis + arXiv preprint + released codebase.

---

## 3. Reading List — Phase 1 (Foundation Studies)

### 3.1 Pillar A: Pulsar Timing Arrays and the Gravitational Wave Background

#### Primary Papers (must read)
1. **NANOGrav 15yr Detection Paper**  
   Agazie et al. (2023), *The NANOGrav 15-year Data Set: Evidence for a Gravitational-Wave
   Background*, ApJ Lett. 951, L8  
   arXiv: 2306.16213  
   *This is your experimental data. Read the full paper, not just the abstract.*

2. **NANOGrav 15yr New Physics Search**  
   Afzal et al. (2023), *The NANOGrav 15 yr Data Set: Search for Signals from New Physics*,
   ApJ Lett. 951, L11  
   arXiv: 2306.16219  
   *Directly constrains cosmic strings. Understand their methodology — you are improving it.*

3. **NANOGrav 15yr Free Spectrum**  
   Agazie et al. (2023), *The NANOGrav 15-year Data Set: Detector Characterization and
   Noise Budget*, ApJ Supp. 265, 49  
   arXiv: 2306.16217  
   *Your noise model comes from here. You will use their free-spectrum posterior directly.*

4. **Hellings-Downs Original Paper**  
   Hellings & Downs (1983), *Upper limits on the isotropic gravitational radiation background*,
   ApJ Lett. 265, L39  
   *The foundational physics of the inter-pulsar correlation. Short and essential.*

5. **PTA Review — Dawn of GW Astronomy**  
   Taylor et al. (2025), *The Dawn of Gravitational Wave Astronomy at Light-year Wavelengths*,
   arXiv: 2511.08966  
   *A comprehensive historical and technical review. Read after the NANOGrav paper.*

#### Textbooks and Lecture Notes
6. **NANOGrav Pulsar Timing School**  
   https://github.com/nanograv/pulsar_timing_school  
   *Worked Jupyter notebooks covering ENTERPRISE, Bayesian PTA analysis, and GWB searches.
   Work through these notebooks in Phase 1 — they are the fastest hands-on intro.*

7. **NANOGrav Official Tutorials**  
   https://nanograv.org/outreach/tutorials  
   *Official tutorials for the 12.5yr and 15yr datasets.*

8. **van Haasteren (2011)**, *Gravitational Wave detection & data analysis for Pulsar Timing Arrays*  
   Available via the pulsar_timing_school repo above  
   *The foundational Bayesian framework for PTA data analysis. Essential math background.*

---

### 3.2 Pillar B: Cosmic Strings and Their Gravitational Wave Spectrum

#### Primary Papers (must read)
9. **VOS Model — Core Paper**  
   Martins & Shellard (1996), *Quantitative String Evolution*, Phys. Rev. D 54, 2535  
   arXiv: hep-ph/9602271  
   *The foundational VOS ODE system you will implement.*

10. **VOS Model Calibration**  
    Martins & Shellard (2002), *String Evolution with Friction*, Phys. Rev. D 65, 043514  
    *Updated parameters from numerical calibration.*

11. **SGWB from Cosmic Strings via VOS**  
    Sousa & Avelino (2013), *Stochastic Gravitational Wave Background generated by Cosmic
    String Networks: VOS model versus Scale-Invariant Evolution*, Phys. Rev. D 88, 023516  
    arXiv: 1304.2445  
    *Directly connects the VOS model to Ω_gw(f). This is your physics target.*

12. **BOS Loop Distribution Model**  
    Blanco-Pillado, Olum & Shlaer (2011), *The number of cosmic string loops*, Phys. Rev. D 83,
    083514  
    arXiv: 1101.5173  
    *One of your three loop distribution models.*

13. **LRS Loop Distribution Model**  
    Lorenz, Ringeval & Sakellariadou (2010), *Cosmic string loop distribution on all length scales
    and at any redshift*, JCAP 10, 003  
    arXiv: 1006.0931  
    *Second loop model.*

14. **Cosmic Strings in PTA Band — Constraint Paper**  
    Ellis & Sherrill (2023), *First constraint on the second-order gravitational wave signal
    from cosmic strings*, Phys. Rev. D 109, 063510  
    arXiv: 2312.09882  
    *Recent: shows what cosmic string constraints from PTA data look like in practice.*

#### Reviews
15. **Cosmic String Review**  
    Copeland, Kibble & Steer (2009), *Collisions of strings with Y junctions*  
    OR  
    Vilenkin & Shellard, *Cosmic Strings and Other Topological Defects*, Cambridge University Press  
    *The textbook. Chapter 3 (string network dynamics) and Chapter 12 (GWs) are your priority.*

16. **GW Spectrum from Cosmic Strings — Springer Review**  
    Sousa (2023), *Probing the Nature of Cosmic Strings with Gravitational Waves*  
    in *Gravitational Waves: A New Window to the Universe*, Springer  
    https://link.springer.com/chapter/10.1007/978-3-031-42096-2_9  
    *Excellent pedagogical treatment of the full calculation pipeline.*

---

### 3.3 Pillar C: Simulation-Based Inference

#### Primary Papers (must read)
17. **TMNRE — Original Algorithm**  
    Miller et al. (2021), *Truncated Marginal Neural Ratio Estimation*, NeurIPS 2021  
    arXiv: 2107.01214  
    *This is the algorithm you are using. Read in full.*

18. **swyft — Software Paper**  
    Miller et al. (2022), *swyft: Truncated Marginal Neural Ratio Estimation in Python*, JOSS  
    https://www.theoj.org/joss-papers/joss.04205/10.21105.joss.04205.pdf  
    *The library you will use. Read alongside its GitHub README.*

19. **saqqara — Direct Predecessor**  
    Alvey, Bhardwaj, Domcke, Pieroni & Weniger (2023/2024),  
    *Simulation-based inference for stochastic gravitational wave background data analysis*,
    Phys. Rev. D 109, 083008  
    arXiv: 2309.07954  
    *This is the most important single paper for your project. It is your starting point —
    you are extending saqqara to the PTA band with cosmic string models.*

20. **SBI Review — Frontier Paper**  
    Cranmer, Brehmer & Louppe (2020), *The Frontier of Simulation-Based Inference*,
    PNAS 117, 30055  
    arXiv: 1911.01429  
    *The canonical review. Read this before the TMNRE paper.*

21. **Autoregressive NRE (scalable TMNRE)**  
    Anau Montel, Alvey & Weniger (2023), *Scalable inference with Autoregressive Neural Ratio
    Estimation*, arXiv: 2308.08597  
    *Used in saqqara for high-dimensional posterior exploration. You will likely use this too.*

#### Software to install in Phase 1
22. **swyft GitHub**: https://github.com/undark-lab/swyft  
23. **saqqara GitHub**: https://github.com/PEREGRINE-GW/saqqara  
24. **ENTERPRISE docs**: https://enterprise.readthedocs.io/en/latest/  
25. **PTArcade**: https://ptarcade.readthedocs.io/  

---

## 4. Reading List — Phase 2 (Implementation and Simple Testing)

### 4.1 Forward Simulator Implementation

26. **JAX Documentation**  
    https://jax.readthedocs.io  
    Focus: `jit`, `vmap`, `grad`, `lax.scan` for ODE integration.

27. **Diffrax (JAX-based ODE solver)**  
    Kidger (2021), *On Neural Differential Equations*, arXiv: 2202.02435  
    https://github.com/patrick-kidger/diffrax  
    *Use this for the VOS ODE system in JAX instead of implementing a solver from scratch.*

28. **SGWB Response Function in PTAs**  
    Anholm et al. (2009), *Optimal strategies for gravitational wave stochastic background
    searches in pulsar timing arrays*, Phys. Rev. D 79, 084030  
    arXiv: 0809.0701  
    *The PTA antenna response / Hellings-Downs integral derivation you need for the detector layer.*

29. **Cross-Power Spectral Density in PTAs**  
    Allen & Romano (1999), *Detecting a stochastic background of gravitational radiation*,
    Phys. Rev. D 59, 102001  
    arXiv: gr-qc/9710117  
    *The Ω_gw → timing residuals pipeline derivation.*

### 4.2 Neural Compression Network Design

30. **1D CNN for time series in astrophysics**  
    Dax et al. (2021), *Real-time gravitational wave science with neural posterior estimation*,
    Phys. Rev. Lett. 127, 241103  
    arXiv: 2106.12594  
    *Best practice for compression network design in GW contexts. Directly relevant architecture.*

31. **saqqara compression network**  
    See arXiv: 2309.07954, Section III.B  
    *How Alvey et al. designed their compression network for LISA — adapt for PTA.*

### 4.3 Validation Methods

32. **Simulation-Based Calibration**  
    Talts et al. (2020), *Validating Bayesian Inference Algorithms with Simulation-Based
    Calibration*, arXiv: 1804.06788  
    *The SBC method you will use to validate posterior coverage.*

33. **PTArcade Paper**  
    Mitridate et al. (2023), *PTArcade*, arXiv: 2306.16377  
    *The MCMC baseline you will benchmark against.*

---

## 5. Discussion: Scientific Potential and Strategic Advice

### What Makes This Project Stand Out

1. **The source separation result is genuinely novel in the PTA band.** The saqqara paper
   proved TMNRE+implicit marginalization works for LISA. Extending it to PTA with a
   physically motivated cosmological source (cosmic strings, not a generic power law) is a
   non-trivial and publishable contribution.

2. **The implicit SMBHB marginalization result has immediate impact.** If you can show
   that MCMC-based analyses are biased when they fix the SMBHB model, and that TMNRE
   corrects this, that is a direct critique of existing NANOGrav new-physics papers — and a
   compelling narrative for reviewers.

3. **Timing**: The PTA field is at peak activity after the 2023 detections. A paper applying
   modern ML inference to cosmic string constraints in the PTA band, submitted in 2026–2027,
   will land in a highly receptive community.

### Risks and Mitigations

| Risk | Mitigation |
|---|---|
| VOS + BOS computation too slow for SBI | Implement in JAX with `vmap`; use the lookup-table trick for the loop integral |
| TMNRE posteriors poorly calibrated | Run SBC in Phase 4; start simple (power-law SGWB) before cosmic strings |
| NANOGrav noise model too simplified | Use the published free-spectrum posterior samples directly (noise realization injection) |
| Source separation experiment is too ambitious for MSc | Frame as "proof-of-concept" with mock data; real data application is the stretch goal |

### On the work-group.pdf (Chapter 5 / Source Separation)

The work-group proposal (simultaneous source separation via TMNRE) is the most ambitious of
the three original proposals. It is best structured as:
- **Primary thesis result**: single-source cosmic string constraints (Phase 3)
- **Extension / publication result**: source separation with SMBHB marginalization

This means if you run out of time, you still have a complete thesis with the single-source
result. The source separation becomes the "exciting future direction" in the discussion, or
the result that gets the paper into a better journal.

For the team/work-group aspect: the source separation experiment naturally divides into
subproblems (cosmic string forward model, SMBHB forward model, joint noise injection,
inference network design) that could be distributed among 2–3 students if your group
expands.

### Physics-First Framing for the Proposal

Your professor's note about physics orientation means the proposal introduction should read
like this:

> "The detection of a stochastic gravitational wave background by NANOGrav and other PTAs
> opens a window on the early universe. Among the proposed cosmological interpretations, a
> network of cosmic strings — one-dimensional topological defects formed during symmetry-
> breaking phase transitions — produces a characteristic gravitational wave spectrum sensitive
> to the string tension Gμ and reconnection probability p. We propose to constrain these
> microphysical parameters using simulation-based inference, which overcomes the scalability
> limitations of existing MCMC approaches and enables, for the first time in the PTA band,
> robust marginalization over the contaminating SMBHB background."

Then the software (PTAforge/simulator) appears as: "To enable this analysis, we build a
GPU-accelerated forward simulator..." — it serves the physics narrative, not the other way
around.

---

## 6. Key Software Stack

| Layer | Tool | Notes |
|---|---|---|
| Forward simulation | JAX + Diffrax | VOS ODE, loop integrals, PTA response |
| Inference backend | swyft / saqqara | TMNRE implementation |
| MCMC baseline | ENTERPRISE + PTArcade | Validation only |
| Data | NANOGrav 15yr public release | Free-spectrum posterior for noise injection |
| Cluster | Group compute cluster | ~10^5 prior samples required |
| CI/CD | pytest + GitHub Actions | For the released software |

---

*Document prepared: April 2026*

---

# Tasks Inbox

- [ ] **Phase 1**: Preliminaries
	- [ ] **Proposal Development**: Write the official proposal with planning and explanation of the project in mind.
		- [ ] Just an abstract would suffice for now.
	- [ ] **Preliminaries**: Reading important review papers on the topic, running basic implementation of ENTERPRISE and PTArcade.