# Proposal for M.Sc. Thesis (1)

## Title:

## A Simulation-Based Inference Pipeline for Constraining Cosmic String Microphysics from NANOGrav Pulsar Timing Array Data

### Abstract

The nanohertz gravitational wave background recently reported by NANOGrav and other pulsar timing array (PTA) collaborations stands as one of the most exciting signals in contemporary physics. Among the cosmological interpretations, a stochastic gravitational wave background (SGWB) produced by a network of cosmic strings — one-dimensional topological defects formed during symmetry-breaking phase transitions in the early universe — is a well-motivated and observationally relevant candidate. The microphysics of such a network, encoded in the string tension Gμ, the reconnection probability p, and the loop distribution model, leaves a characteristic imprint on the spectral energy density Ω_gw(f). Traditional Bayesian parameter estimation using ENTERPRISE/PTArcade relies on MCMC sampling with an explicit likelihood, which scales poorly as the model complexity grows and struggles to marginalize efficiently over nuisance parameters such as the competing supermassive black hole binary (SMBHB) background.

In this proposal, we develop a fully open-source, modular **Simulation-Based Inference (SBI)** pipeline targeting the PTA frequency band. The forward simulator encodes the Velocity-dependent One-Scale (VOS) network evolution equations in an expanding FLRW background, computes the resulting SGWB spectral density analytically (via the BOS and LRS loop distribution models), and injects the signal into mock NANOGrav-15yr noise. The inference backend employs Truncated Marginal Neural Ratio Estimation (TMNRE), implemented via the `swyft` library, to learn the marginal posteriors over the string microphysics parameters. This approach is explicitly complementary to the existing `saqqara` library (Alvey et al. 2024), which targets LISA and generic signal templates; our contribution is a dedicated PTA-band forward model and a cosmic-string-specific signal module that could ultimately be contributed upstream.

The cluster resources available to the group are utilized for the large-scale parallel simulation campaigns needed to train the neural estimator.

### Objectives

1. Implement a vectorized, physically complete forward simulator for the SGWB from cosmic string networks in the PTA frequency band, based on the VOS model and Nambu-Goto loop dynamics;
2. Develop a modular SBI pipeline (forward simulator + noise model + TMNRE inference) as a reusable open-source software package, designed to be architecturally compatible with `saqqara`;
3. Constrain cosmic string microphysics parameters (Gμ, p, loop distribution model) from mock and real NANOGrav 15yr data;
4. Benchmark the SBI pipeline against traditional MCMC-based ENTERPRISE/PTArcade results to validate and quantify the improvement in inference efficiency;
5. Explore the implicit marginalization capability of TMNRE over the SMBHB contamination as a nuisance source.

### Methods

1. The VOS model — a pair of coupled ODEs describing the correlation length L and RMS velocity v of the string network in an FLRW background — is solved numerically using a stiff ODE integrator. This constitutes the physically relativistic core of the forward model.
2. The SGWB spectral energy density Ω_gw(f; Gμ, p) is computed by integrating the loop number density (BOS, LRS, or Lorenz-Wands-Martins models) weighted by the GW emission power from cusps and kinks.
3. The resulting signal is injected into a noise model based on the NANOGrav 15yr free-spectrum posterior, using the `enterprise` + `enterprise_extensions` PTA likelihood framework as a reference.
4. A compression network (1D CNN or UNet architecture, following the saqqara design) is trained to map frequency-domain PTA data to a low-dimensional summary embedding. A neural ratio estimator is then trained using `swyft` to produce marginal posteriors on the parameter vector θ = {log Gμ, log p, loop model index}.
5. Simulation campaigns are distributed across the group's compute cluster for embarrassingly parallel prior sampling.
6. Posterior predictive checks and simulation-based calibration (SBC) are applied to validate inference quality.
7. Results are compared to the existing PTArcade/ENTERPRISE analyses of the same dataset (Afzal et al. 2023, and revised bounds papers) for quantitative benchmarking.

### References

[1] Afzal, Adeela, et al. (NANOGrav Collaboration). "The NANOGrav 15 yr data set: Search for signals from new physics." _The Astrophysical Journal Letters_ 951.1 (2023): L11.

[2] Alvey, James, et al. "Simulation-based inference for stochastic gravitational wave background data analysis." _Physical Review D_ 109, 083008 (2024). [saqqara: github.com/PEREGRINE-GW/saqqara]

[3] Mitridate, Andrea, et al. "PTArcade." arXiv:2306.16377 (2023). [PTArcade: github.com/andrea-mitridate/PTArcade]

[4] Cranmer, Kyle, Johann Brehmer, and Gilles Louppe. "The frontier of simulation-based inference." _PNAS_ 117.48 (2020): 30055–30062.

[5] Martins, C. J. A. P., and E. P. S. Shellard. "Fractal structure and the accuracy of the velocity-dependent one-scale model." _Physical Review D_ 65 (2002): 043514.

[6] Lorenz, Larissa, Christophe Ringeval, and Mairi Sakellariadou. "Cosmic string loop distribution on all scales." _Journal of Cosmology and Astroparticle Physics_ 2010.10 (2010): 003.

[7] Johnson, Aaron D., et al. (NANOGrav Collaboration). "The NANOGrav 15-year Gravitational-Wave Background Methods." arXiv:2306.16223 (2023).

[8] Miller, Benjamin K., et al. "Truncated Marginal Neural Ratio Estimation." _NeurIPS_ (2021). [swyft: github.com/undark-lab/swyft]

---

---

# Proposal for M.Sc. Thesis (2)

## Title:

## Beyond the Power Spectrum: Morphological Summary Statistics for Stochastic Gravitational Wave Background Inference in Pulsar Timing Arrays

### Abstract

Parameter estimation from pulsar timing array data is predominantly performed using the cross-power spectral density as the summary statistic fed into a likelihood or inference algorithm. While the power spectrum captures the mean spectral shape, it discards higher-order information encoded in the non-Gaussian features of the signal. In cosmological large-scale structure analysis, morphological measures — specifically Minkowski functionals, persistent homology, and weighted morphological statistics — have been shown to carry significant additional constraining power beyond the power spectrum, particularly in the non-Gaussian regime.

This proposal investigates the application of these topological and geometrical summary statistics to SGWB data analysis in the context of PTA experiments. The key observation is that the SGWB, as reconstructed from PTA cross-correlations across frequency bins and pulsar pairs, forms a two-dimensional map (pulsar pairs × frequency) whose morphological structure encodes information about the signal's spectral shape, angular distribution, and non-Gaussianity. We propose to implement a systematic comparison of standard (power spectrum) and morphological summary statistics as inputs to a Simulation-Based Inference framework, quantifying via Fisher forecasts and SBI posterior widths which combination of statistics yields the tightest constraints on cosmological source parameters.

The target sources include the cosmic string network and a simple power-law SGWB as a baseline. This work establishes a direct bridge between Prof. Movahed's morphological statistics toolkit and gravitational wave data analysis, and is designed to yield a methods paper regardless of the physical source chosen.

### Objectives

1. Implement Minkowski functionals and persistent homology as summary statistics operating on the frequency–pulsar-pair cross-correlation matrix of PTA residuals;
2. Quantify via Fisher information matrix analysis the information gain of morphological statistics relative to the power spectrum alone for cosmic string parameter estimation;
3. Build a full SBI pipeline that uses these combined statistics as the compressed data representation fed to a neural ratio estimator;
4. Identify the optimal combination of summary statistics as a function of signal-to-noise ratio and source model, producing a general result applicable to any SGWB source.

### Methods

1. Mock PTA datasets are generated by injecting SGWB signals (cosmic string + SMBHB) into NANOGrav-15yr-calibrated noise realizations, for a wide prior over source parameters.
2. For each realization, the frequency-domain cross-correlation matrix C(f, a, b) (pulsars a, b) is computed. This matrix is the primary data object.
3. Minkowski functionals (area, perimeter, Euler characteristic as a function of threshold) are computed on excursion sets of C(f). Persistent homology is computed using the Vietoris-Rips filtration of the frequency-pulsar graph.
4. A Fisher information matrix forecast is constructed semi-analytically using the Gram matrix of summary statistic derivatives with respect to the source parameters.
5. An SBI pipeline (TMNRE via `swyft`) is constructed using each summary statistic set in turn, and posterior volumes are compared as a direct measurement of information content.
6. The cluster is used for the simulation campaign (O(10^4–10^5) simulations) and for parallelized morphological statistic computation.

### References

[1] Alvey, James, et al. "Simulation-based inference for stochastic gravitational wave background data analysis." _Physical Review D_ 109, 083008 (2024).

[2] Jalali Kanafi, M. H., Saeed Ansarifard, and S. M. S. Movahed. "Imprint of massive neutrinos on Persistent Homology of large-scale structure." _Monthly Notices of the Royal Astronomical Society_ 535.1 (2024): 657–674.

[3] Abedi, Fatemeh, Mohammad Hossein Jalali Kanafi, and Seyed Mohammad Sadegh Movahed. "Impact of Redshift Space Distortion on Persistent Homology of cosmic matter density field." arXiv:2410.01751 (2024).

[4] Klatt, Michael Andreas, Max Hörmann, and Klaus Mecke. "Characterization of anisotropic Gaussian random fields by Minkowski tensors." _Journal of Statistical Mechanics_ 2022.4 (2022): 043301.

[5] Afzal, Adeela, et al. (NANOGrav Collaboration). "The NANOGrav 15 yr data set: Search for signals from new physics." _The Astrophysical Journal Letters_ 951.1 (2023): L11.

[6] Cranmer, Kyle, Johann Brehmer, and Gilles Louppe. "The frontier of simulation-based inference." _PNAS_ 117.48 (2020): 30055–30062.

[7] Renzini, Arianna I., et al. "Stochastic gravitational-wave backgrounds: Current detection efforts and future prospects." _Galaxies_ 10.1 (2022): 34.

---

---

# Proposal for M.Sc. Thesis (3)

## Title:

## PTAforge: A Modular, High-Performance Forward Simulation Framework for New-Physics SGWB Signals in Pulsar Timing Arrays

### Abstract

The growing maturity of pulsar timing array experiments — NANOGrav, EPTA, PPTA, CPTA, and the emerging IPTA — demands analysis software that is physically complete, computationally efficient, and extensible to novel signal models from beyond-standard-model physics. The existing tool PTArcade provides a user-friendly wrapper around ENTERPRISE for MCMC-based new-physics searches. However, no general-purpose forward simulation library exists that is purpose-built for generating large-scale simulation campaigns from diverse cosmological SGWB source models, which are the prerequisite for Simulation-Based Inference workflows.

This proposal develops **PTAforge**: an open-source, modular, high-performance Python/C++ simulation framework for PTA SGWB signals. PTAforge separates the physics layer (signal model: cosmic strings, phase transitions, primordial GWs, etc.), the detector layer (PTA noise, pulsar timing residuals, antenna response), and the data product layer (cross-power spectral density, Hellings-Downs correlations, time-domain residuals) into independently testable, composable modules. The framework is designed to serve as the simulation backend for SBI workflows (compatible with `saqqara` and `swyft`) and as a standalone signal injection tool for traditional ENTERPRISE/PTArcade analyses.

The contribution here is explicitly a software contribution: the physics is well-established, but the infrastructure to run it at scale, with reproducible outputs, modular signal composition, and GPU-accelerated batch generation, does not exist. This addresses a real gap in the PTA software ecosystem and is publishable as a methods/software paper independent of any specific physical result.

### Objectives

1. Design and implement the PTAforge architecture: signal module interface, detector module interface, and data product module, with clean separation of concerns and a plugin system for new signal models;
2. Implement a library of built-in signal models: power-law SGWB, cosmic string (VOS/BOS/LRS), first-order phase transition, and primordial inflation as baseline plugins;
3. Achieve GPU-accelerated batch simulation via JAX or PyTorch backends, targeting O(10^4) simulations per minute on a single GPU node, enabling practical SBI simulation campaigns;
4. Validate PTAforge outputs quantitatively against PTArcade/ENTERPRISE results on shared benchmarks using the NANOGrav 15yr dataset;
5. Release as a fully documented open-source package with continuous integration, contributing signal modules back to the saqqara ecosystem.

### Methods

1. The software architecture is designed following the modular pattern established by saqqara: a `SignalModel` abstract base class, a `NoiseModel` abstract base class, and a `Simulator` class that composes them and produces batched outputs.
2. All computationally intensive inner loops (loop number density integrals, power spectrum evaluations, PTA response functions) are implemented in JAX for JIT compilation and automatic batching via `vmap`.
3. A Python plugin registry allows user-defined signal models to be registered and used seamlessly within the SBI or MCMC workflow without modifying core library code.
4. Unit tests, integration tests, and numerical benchmarks are implemented via pytest and run in CI. Outputs for the power-law SGWB case are compared against PTArcade's known posteriors to validate correctness.
5. Documentation is built with Sphinx and includes worked examples for both SBI (swyft integration) and MCMC (PTArcade/ENTERPRISE integration) workflows.
6. The cluster is used for performance benchmarking of the GPU batch generation and for running the validation simulation campaigns.

### References

[1] Mitridate, Andrea, et al. "PTArcade." arXiv:2306.16377 (2023).

[2] Alvey, James, et al. "Simulation-based inference for stochastic gravitational wave background data analysis." _Physical Review D_ 109, 083008 (2024).

[3] Johnson, Aaron D., et al. "The NANOGrav 15-year Gravitational-Wave Background Methods." arXiv:2306.16223 (2023).

[4] Afzal, Adeela, et al. "The NANOGrav 15 yr data set: Search for signals from new physics." _ApJL_ 951.1 (2023): L11.

[5] Bradbury, James, et al. "JAX: Composable transformations of Python+NumPy programs." (2018). [github.com/google/jax]

[6] Ellis, Justin A., Michele Vallisneri, Stephen R. Taylor, and Paul T. Baker. "ENTERPRISE: Enhanced Numerical Toolbox Enabling a Robust PulsaR Inference SuitE." Zenodo (2020).

[7] Renzini, Arianna I., et al. "Stochastic gravitational-wave backgrounds: Current detection efforts and future prospects." _Galaxies_ 10.1 (2022): 34.

---

---

# Proposal for M.Sc. Thesis (4)

## Title:

## Simultaneous Source Separation and Parameter Estimation for Overlapping SGWB Signals in PTA Data via Simulation-Based Inference

### Abstract

The gravitational wave background detected by pulsar timing arrays is almost certainly a superposition of multiple sources: at minimum, an astrophysical background from supermassive black hole binaries (SMBHBs), and potentially one or more cosmological backgrounds from phase transitions, cosmic strings, or primordial inflation. Disentangling these overlapping signals is one of the central challenges in PTA data analysis. Traditional approaches either fix the astrophysical background and search for a cosmological excess, or perform joint MCMC sampling over the combined parameter space — the latter becoming computationally intractable as the number of source classes grows.

Simulation-Based Inference offers a principled solution: by simulating overlapping signal realizations from the joint prior over all source parameters and training a neural ratio estimator to learn the marginal posteriors, one can achieve implicit marginalization over the contaminating source without any explicit likelihood assumption. This proposal applies this strategy to the specific problem of cosmic string signal recovery in the presence of SMBHB contamination in NANOGrav data, extending the proof-of-concept demonstrated for LISA transients in Alvey et al. (2024) to the PTA band and to a physically motivated cosmological source.

This is the most directly scientifically impactful of the proposed theses, as it addresses a real open problem in PTA data analysis and produces constraints on Gμ that are robust to SMBHB model uncertainty.

### Objectives

1. Model the joint SGWB from cosmic strings and SMBHBs in the PTA frequency band, parametrizing both source classes;
2. Demonstrate that TMNRE with implicit marginalization can recover the marginal posterior on cosmic string parameters while treating SMBHB parameters as nuisance variables;
3. Apply the pipeline to mock NANOGrav 15yr data and compare constraints on Gμ with and without explicit SMBHB marginalization;
4. Quantify the bias introduced in cosmic string parameter estimates when the SMBHB background is incorrectly modeled or ignored;
5. Optionally apply to the real NANOGrav 15yr free-spectrum chains as a data compression/re-analysis step.

### Methods

1. The forward simulator generates joint SGWB realizations by drawing simultaneously from the cosmic string prior (log Gμ, loop model) and the SMBHB prior (amplitude A, spectral index γ) and summing the two spectral contributions before injecting into PTA noise.
2. The TMNRE algorithm in `swyft` is used with the SMBHB parameters treated as implicit nuisance dimensions — the neural ratio estimator learns the marginal likelihood ratio p(x|θ_CS)/p(x) where x is the data and θ_CS are only the cosmic string parameters.
3. This is validated against an explicit joint posterior (obtained by sampling over all parameters) to verify that the marginals agree, and the number of required simulations is compared.
4. A second experiment injects only a cosmic string signal but fits with a model that assumes SMBHB contamination, to quantify the bias from incorrect noise modeling — a practically important diagnostic.
5. Fisher forecasts are computed for the joint model to understand which parameter combinations are fundamentally degenerate.
6. The cluster enables the large simulation campaigns required (~10^5 samples from the joint prior).

### References

[1] Alvey, James, et al. "Simulation-based inference for stochastic gravitational wave background data analysis." _Physical Review D_ 109, 083008 (2024).

[2] Afzal, Adeela, et al. "The NANOGrav 15 yr data set: Search for signals from new physics." _ApJL_ 951.1 (2023): L11.

[3] Sesana, Alberto. "Insights into the astrophysics of supermassive black hole binaries from pulsar timing observations." _Classical and Quantum Gravity_ 30.22 (2013): 224014.

[4] Cranmer, Kyle, Johann Brehmer, and Gilles Louppe. "The frontier of simulation-based inference." _PNAS_ 117.48 (2020): 30055–30062.

[5] Ellis, John, Marek Lewicki, Chunshan Lin, and Ville Vaskonen. "Cosmic Superstrings Revisited in Light of NANOGrav 15-Year Data." arXiv:2306.17147 (2023).

[6] Hazboun, Jeffrey S., et al. (NANOGrav Collaboration). "The NANOGrav 11-year Data Set: Limits on Gravitational Wave Emission from Individual Supermassive Black Hole Binaries." _ApJ_ 890 (2020): 108.

[7] Miller, Benjamin K., et al. "Truncated Marginal Neural Ratio Estimation." _NeurIPS_ (2021).

---

---

# Proposal for M.Sc. Thesis (5)

## Title:

## Differentiable Gravitational Wave Cosmology: A JAX-Based Framework for Gradient-Informed Inference of SGWB Source Parameters

### Abstract

Modern machine learning toolchains built on differentiable programming — PyTorch, JAX — have transformed computational physics by enabling gradient-based optimization over physical simulators. In gravitational wave cosmology, the forward model mapping source parameters to the observed SGWB spectral density is a smooth, differentiable function of those parameters. Yet existing PTA analysis frameworks (ENTERPRISE, PTArcade) treat this model as a black box, using gradient-free samplers (MCMC) and discarding the information in the Jacobian of the forward model. Simulation-Based Inference methods, while powerful, also do not exploit the differentiability of the simulator.

This proposal develops a JAX-based differentiable forward simulator for SGWB signals in the PTA band, and investigates three inference strategies that exploit gradients: (1) gradient-based MCMC (NUTS/HMC) via NumPyro; (2) variational inference (VI) using normalizing flows with gradient-optimized parameters; and (3) Neural Posterior Estimation (NPE) with gradient-informed sequential simulation (active learning). The result is both a software contribution (a publicly available differentiable SGWB simulator) and a methodological comparison — identifying which inference strategy is most simulation-efficient for cosmic string parameter estimation under realistic PTA noise.

This proposal is the most technically ambitious and software-forward of the five. It is appropriate if the student's primary interest is in the architecture of inference systems and differentiable scientific computing, with the GW physics as the application domain.

### Objectives

1. Implement a fully differentiable SGWB forward model for cosmic strings and a power-law SGWB in JAX, supporting `jit`, `grad`, `vmap`, and `pmap` transformations;
2. Deploy gradient-based MCMC (HMC/NUTS via NumPyro) on the differentiable model and benchmark convergence against gradient-free MCMC (PTMCMCSampler);
3. Implement a normalizing flow posterior (using `nflows` or `flowjax`) trained via maximum likelihood on simulated (θ, x) pairs, and compare to TMNRE;
4. Implement a gradient-informed active learning loop for sequential simulation, reducing the number of simulator calls needed to achieve target posterior accuracy;
5. Release the differentiable simulator as a standalone JAX library compatible with the broader NumPyro/BlackJAX inference ecosystem.

### Methods

1. The VOS network evolution equations and the Ω_gw(f) integral are implemented in JAX as pure functions, verified to be differentiable through `jax.grad` by comparison with finite-difference derivatives.
2. Automatic differentiation through the ODE solver is achieved via the `diffrax` library (Kidger 2021), which provides differentiable Dormand-Prince and Kvaerno solvers in JAX.
3. For gradient-based MCMC, the PTA likelihood (Gaussian approximation to the free-spectrum posterior) is implemented in NumPyro and NUTS is run using BlackJAX, with wall-clock time and effective sample size compared to PTMCMCSampler.
4. For normalizing flows, a masked autoregressive flow is trained offline on (θ, summary(x)) pairs, then used as an amortized posterior. Posterior quality is assessed via simulation-based calibration.
5. The gradient-informed active learning loop selects new simulation points from regions of high posterior uncertainty (estimated via an ensemble of normalizing flows), reducing simulation budget by targeted prior refinement.
6. All experiments are run on the group's GPU cluster nodes; the JAX implementation enables transparent multi-GPU distribution via `pmap`.

### References

[1] Bradbury, James, et al. "JAX: Composable transformations of Python+NumPy programs." (2018). [github.com/google/jax]

[2] Kidger, Patrick. "On Neural Differential Equations." PhD Thesis, University of Oxford (2021). [diffrax: github.com/patrick-kidger/diffrax]

[3] Phan, Du, et al. "Composable Effects for Flexible and Accelerated Probabilistic Programming in NumPyro." arXiv:1912.11554 (2019).

[4] Cranmer, Kyle, Johann Brehmer, and Gilles Louppe. "The frontier of simulation-based inference." _PNAS_ 117.48 (2020): 30055–30062.

[5] Papamakarios, George, et al. "Normalizing flows for probabilistic modeling and inference." _JMLR_ 22 (2021): 1–64.

[6] Alvey, James, et al. "Simulation-based inference for stochastic gravitational wave background data analysis." _Physical Review D_ 109, 083008 (2024).

[7] Afzal, Adeela, et al. "The NANOGrav 15 yr data set: Search for signals from new physics." _ApJL_ 951.1 (2023): L11.

[8] Martins, C. J. A. P., and E. P. S. Shellard. "Fractal structure and the accuracy of the velocity-dependent one-scale model." _Physical Review D_ 65 (2002): 043514.

---

_Document prepared: February 2026_  
_For internal use: Computational Cosmology Group, Shahid Beheshti University_