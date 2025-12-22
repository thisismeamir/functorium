---
# try also 'default' to start simple
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://cover.sli.dev
# some information about your slides (markdown enabled)
title: Welcome to Slidev
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
# apply UnoCSS classes to the current slide
class: text-center
# https://sli.dev/features/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations.html#slide-transitions
transition: slide-left
# enable MDC Syntax: https://sli.dev/features/mdc
mdc: true
# duration of the presentation
duration: 35min
---

# GENIE

---

## Executive Summary

GENIE (Generates Events for Neutrino Interaction Experiments) is the industry-standard Monte Carlo event generator for neutrino physics, serving virtually all major neutrino experiments worldwide. While comprehensive in physics coverage and actively maintained, the codebase exhibits significant technical debt from its mid-2000s origins, presenting both challenges and opportunities for modernization.

---
layout: center
---

### Key Findings

---
layout: two-cols
---

**Strengths:**
- De facto standard with extensive physics validation
- Active development (8,000+ commits, recent activity through November 2025)
- Comprehensive feature set covering MeV to PeV energy ranges
- Modular architecture with pluggable physics models
- Support for both Standard Model and BSM physics

::right::

**Critical Challenges:**
- Legacy build system (Perl-based configure script, GNU Autotools)
- Heavy reliance on deprecated dependencies (PYTHIA6, LHAPDF5)
- Pre-C++11 codebase lacking modern language features
- No official Python bindings or multi-language support
- Tight coupling to ROOT framework
- Complex installation process with platform limitations

---
layout: center
---

**Modernization Priority:** High urgency due to deprecated dependencies and opportunity to improve usability while maintaining physics fidelity.

---
layout: center
---

## Project Overview

---
layout: center
---

### Mission and Scope

GENIE serves as a **comprehensive neutrino-event generation framework** designed to:
- Simulate neutrino and charged-lepton interactions across all energy regimes
- Support all neutrino flavors and nuclear targets
- Provide experiment-agnostic physics with global tuning to experimental data
- Enable systematic uncertainty quantification via reweighting

---
layout: center
---

### Adoption and Impact

- Used by all running neutrino beam experiments (with rare exceptions like T2K)
- Adopted by neutrino telescopes and LHC/FASER experiments
- Standard tool for oscillation experiments and neutrino scattering studies
- Approximately 50 open issues and 24 active pull requests indicate healthy community engagement

---
layout: center
---

### Repository Statistics

```
Total Commits:    ~8,000
Latest Update:    November 10, 2025
Open Issues:      ~50
Closed Issues:    ~40+
Open PRs:         24
Merged/Closed PRs: 346+
```

---
layout: center
---

## Current Architecture

---
layout: center
---

### Technology Foundation

---

**Core Implementation:**
```
Language:         C++ (pre-C++11 vintage, circa 2005)
Framework:        CERN ROOT (deeply integrated)
Design Pattern:   Object-oriented with factory/registry patterns
Configuration:    XML-based model specification
Build System:     Perl configure script + GNU Make
```

---

**Key Architectural Decisions:**

1. **ROOT Integration:**
   - Event records stored as ROOT objects (GHEP format)
   - I/O operations through ROOT file format
   - Random number generation via ROOT's TRandom3 (Mersenne Twister)
   - Mathematical operations using ROOT libraries

---

2. **Physics Model Organization:**
   - "Algorithm" abstraction for physics processes
   - XML-configured model parameters and tunings
   - Factory pattern for runtime instantiation
   - Registry pattern for model discovery and selection

---

3. **Event Generation Workflow:**
   ```
   Flux Input → Cross Section Calculation → Event Generation →
   Intranuclear Transport → Hadronization → Final State → ROOT Output
   ```

---
layout: center
---

### Software Design Patterns

---

**Modular Driver Architecture:**
- **Event Generation Drivers:** Coordinate full event production
- **Flux Drivers:** Handle neutrino beam specifications (enabled by default)
- **Geometry Drivers:** Manage detector geometry (enabled by default)
- **Thread Managers:** Organize parallel processing units
- **Module System:** Encapsulate physics calculations

---

**Pluggable Physics:**
- Algorithms registered at compile-time
- Runtime selection via XML configuration
- Supports alternative implementations for same process
- Enables physics model comparisons and tuning

---
layout: center
---

## Code Organization

---
layout: center
---

### Repository Structure

---
```
GENIE-Generator/
├── config/              # XML configuration files
│   ├── ModelConfiguration.xml
│   ├── Messenger.xml
│   └── [tuning configurations]
├── data/                # Static physics data
│   ├── logo/
│   ├── pdftables/
│   └── evgen/
├── src/                 # Source code (primary)
│   ├── Framework/       # Core framework classes
│   ├── Physics/         # Physics model implementations
│   │   ├── QuasiElastic/
│   │   ├── Resonance/
│   │   ├── DeepInelastic/
│   │
  ├── Coherent/
│   │   └── HadronTransport/
│   ├── Apps/            # Executable applications
│   │   ├── gEvGen       # Event generator
│   │   ├── gMakeSplines # Cross section tables
│   │   └── [utilities]
│   ├── Tools/           # Support utilities
│   └── make/            # Build configuration
│       └── Make.config  # Generated by configure
├── Makefile
├── configure            # Perl-based configuration script
├── README.md
└── VERSION
```

---
layout: center
---
### Source Code Layout

---

**Framework Components:**
- `Algorithm/` - Base classes for physics models
- `Conventions/` - Constants, units, PDG codes
- `EventGen/` - Event generation infrastructure
- `GHEP/` - Event record structure
- `Interaction/` - Kinematics and interaction descriptors
- `Messenger/` - Logging system
- `Numerical/` - Mathematical utilities
- `ParticleData/` - Particle properties database
- `Registry/` - Configuration registry

---

**Physics Modules:**
- `QuasiElastic/` - QE scattering (CCQE, NCQE)
- `Resonance/` - Baryon resonance production
- `DeepInelastic/` - DIS with structure functions
- `Coherent/` - Coherent pion production
- `MEC/` - Meson exchange currents
- `Diffractive/` - Diffractive processes
- `HadronTransport/` - Final state interactions (INTRANUKE)
- `NuclearModel/` - Nuclear ground state models

---

**Build Generated Files:**
- `src/make/Make.config` - Contains compiler flags, library paths, feature toggles
- Included by all Makefiles in source tree
- Generated by `configure` script based on command-line options

---
layout: center
---

## Feature Set

---
layout: center
---

### Physics Coverage

---
layout: center
---

#### Standard Model Interactions

---

**Charged Current (CC):**
- Quasi-elastic scattering (CCQE)
- Resonance production (CC-RES)
- Deep inelastic scattering (CCDIS)
- Coherent pion production (CC-COH)
- Meson exchange currents (CC-MEC)

---

**Neutral Current (NC):**
- Elastic scattering (NCEL)
- Resonance production (NC-RES)
- Deep inelastic scattering (NCDIS)
- Coherent pion production (NC-COH)

---

**Energy Regimes:**
- Low energy: ~MeV (supernova neutrinos)
- Medium energy: ~GeV (accelerator experiments)
- High energy: ~TeV to PeV (atmospheric, astrophysical)

---

**Target Support:**
- All nuclear targets (hydrogen through heavy nuclei)
- Nuclear models: Fermi gas, spectral functions, correlated pairs
- All neutrino flavors: νₑ, νμ, ντ and antiparticles

---
layout: center
---

#### Beyond Standard Model Physics

```bash
--enable-nucleon-decay      # Proton/neutron decay
--enable-nnbar-oscillation  # Neutron-antineutron oscillation
--enable-boosted-dark-matter # Boosted DM scattering
--enable-hnl                # Heavy neutral leptons
--enable-hnl-validation     # HNL testing framework
--enable-dark-neutrino      # Dark neutrino interactions
```

These exotic channels demonstrate GENIE's flexibility beyond standard neutrino physics.

---
layout: center
---

### Infrastructure Features

---
layout: center
---

#### Flux Handling
- **Built-in Drivers** (enabled by default via `--enable-flux-drivers`)
- Support for common flux formats:
  - Simple histograms
  - FLUKA output
  - BDSIM output
  - GNuMI beamline simulation
  - Atmospheric flux calculations
- Experiment-specific drivers available via flags:
  ```bash
  --enable-t2k    # T2K beam simulation
  --enable-fnal   # Fermilab beamlines (NOvA, MicroBooNE, etc.)
  --enable-atmo   # Atmospheric neutrino fluxes
  ```

---
layout: center
---

#### Geometry Integration
- **Built-in Geometry Drivers** (enabled by default via `--enable-geom-drivers`)
- Simple geometries: planes, spheres, cylinders
- GDML import (via ROOT's TGeo)
- Optional Geant4 integration (via `--enable-geant4`) for:
  - Complex detector geometries
  - Material tracking
  - Detailed nuclear transport

---
layout: center
---

#### Hadronization Systems

**PYTHIA6** (default, enabled via `--enable-pythia6=YES`):
- Legacy Fortran 77 implementation
- Mature but deprecated by CERN
- Requires separate installation

**PYTHIA8** (optional, via `--enable-pythia8`):
- Modern C++ implementation
- Better physics models
- Future default planned

**AGKY Model:**
- GENIE's custom hadronization for transition region
- Smoothly interpolates between resonance and DIS

---
layout: center
---

#### Intranuclear Transport

**INTRANUKE** (built-in):
- GENIE's default cascade model
- Handles final state interactions (FSI)
- Supports both hadron and nuclear re-interactions

**Optional Cascades:**
- **INCL++** (via `--enable-incl`): Liège cascade model
- **Geant4 BERT/FTFP** (via `--enable-geant4`): Industry-standard transport

---
layout: center
---

### Analysis and Reweighting

**Event Reweighting Tools:**
- Systematic uncertainty propagation
- Cross-section model variations
- Nuclear effect parameter scans
- Allows hypothesis testing without regenerating events

**Spline Generation:**
- Pre-computed cross-section tables for fast generation
- `gMakeSplines` application creates lookup tables
- Significantly speeds up event generation

**Analysis Utilities:**
- Cross-section calculators
- Event selection tools
- ROOT-based analysis macros

---
layout: center
---

### Configuration and Tuning

**XML-Based Configuration:**
- Model parameter specification
- Algorithm selection and chaining
- Physics tune management

**Multiple Tunings:**
- Different parameter sets validated against data
- Experiment-specific optimizations
- Global fits to world data

---
layout: center
---

## Technical Debt Analysis

---
layout: center
---

### Legacy Dependencies

---
layout: center
---

#### Critical Issues

---

**1. PYTHIA6 (Fortran 77)**
```
Status:       Default hadronization engine
Problem:      Deprecated by CERN, unmaintained since ~2010
Impact:       - Security vulnerabilities
              - No compiler optimizations (Fortran 77)
              - Difficult to build on modern systems
              - 32-bit compatibility issues
Migration:    PYTHIA8 available but not default
Timeline:     Should be deprecated within 1-2 years
```

---

**2. LHAPDF5**
```
Status:       Default PDF library
Problem:      Superseded by LHAPDF6 (released 2013+)
Impact:       - Missing recent PDF sets
              - Legacy C++ interface
              - Limited functionality
Migration:    LHAPDF6 support exists (--enable-lhapdf6)
Timeline:     Should switch default immediately
```

---

**3. g2c and g77 Support**
```
Status:       Optional legacy Fortran support
Problem:      g77 compiler obsolete since GCC 4.x
Impact:       - Unnecessary code complexity
              - 32-bit assumptions
Migration:    Modern gfortran standard (GCC 4.0+)
Timeline:     Can remove g2c support
```

---
layout: center
---

#### Moderate Issues

**ROOT Version Coupling:**
- Tight integration with specific ROOT versions
- TRandom3 dependency for RNG (could use std::mt19937)
- Event record structure locked to ROOT classes
- Makes independent testing difficult

**CERNLIB References:**
- `--disable-cernlib` flag still exists
- Indicates recent removal of ancient dependency
- Cleanup not complete

---
layout: center
---

### Build System Limitations

---

**Perl Configure Script:**
```perl
# Traditional autoconf-style but written in Perl
./configure --prefix=/path/to/install \
            --enable-lhapdf6 \
            --with-pythia8-inc=/path/to/pythia8/include \
            --with-pythia8-lib=/path/to/pythia8/lib \
            --enable-fnal \
            --enable-atmo
```

---

**Problems:**
1. **Not True Autotools:** Custom Perl script mimics autoconf
2. **Manual Path Specification:** Every dependency needs explicit paths
3. **No Dependency Discovery:** Cannot find libraries automatically
4. **Platform Limitations:**
   - Poor support for macOS (especially M1/M2)
   - Windows essentially unsupported
   - FreeBSD/other Unix variants require manual tweaking
5. **No Package Manager Integration:** Cannot be packaged for conan, spack, conda-forge

---
layout: center
---

#### Comparison with Modern Alternatives

**What CMake Would Provide:**
```cmake
# Modern approach
find_package(ROOT REQUIRED COMPONENTS MathMore)
find_package(LHAPDF REQUIRED)
find_package(Pythia8)  # Optional

add_library(GenieFramework SHARED ${FRAMEWORK_SOURCES})
target_link_libraries(GenieFramework ROOT::Core ROOT::MathMore)
target_compile_features(GenieFramework PUBLIC cxx_std_17)
```


**Benefits:**
- Automatic dependency detection
- Out-of-source builds (keep source clean)
- IDE integration (CLion, VS Code)
- Cross-platform (Windows, macOS, Linux)
- Package manager support (conan, vcpkg)
- Modern CMake presets for common configurations

---
layout: center
---

### Code Quality Issues

---

#### Language Standard

**Current State: Pre-C++11**
```cpp
// Typical GENIE code patterns (circa 2005)
GHepParticle * p = event->Particle(i);  // Raw pointer
for(int i=0; i<n; i++) { ... }          // Traditional loops
Registry * config = Registry::Instance(); // Singleton
NULL                                     // C-style null
#define MACRO_CONSTANT 1.0              // Preprocessor macros
```

**What Modern C++17/20 Would Enable:**
```cpp
// Modern equivalent
auto p = event->particle(i);  // auto type deduction
for (const auto& particle : event->particles()) { ... }  // Range-based
auto config = Registry::instance();  // Still singleton but cleaner
nullptr                              // Type-safe null
constexpr double CONSTANT = 1.0;    // Compile-time constant
```

---

**Missing Modern Features:**
- Smart pointers (`std::unique_ptr`, `std::shared_ptr`)
- Move semantics (avoid copies)
- Lambda functions (callbacks, algorithms)
- `std::optional` (avoid null pointers)
- `std::variant` (type-safe unions)
- Structured bindings
- `constexpr` functions
- Parallel algorithms (`std::execution::par`)

---
layout: center
---

### Installation Complexity

---

#### User Experience

**Common Failure Points:**
- Missing dependencies (often not obvious)
- Incorrect library paths
- ROOT version incompatibility
- PYTHIA6 not found (rare in standard repos)
- M1/M2 Mac architecture issues
- Conflicts between system and custom libraries

**User Complaints:**
- "How do I install GENIE on Apple Silicon?"
- "Configure fails to find ROOT"
- "Where do I get PYTHIA6?"
- "Compile errors with GCC 11+"

---

#### Contrast with Modern Package Management

**What Users Expect (2025):**
```bash
# Python example (DarkNews)
pip install darknews

# C++ via package manager
conan install genie/3.0.0

# Or system package
brew install genie  # (doesn't exist)
apt install genie   # (doesn't exist)
```

**Why GENIE Can't Do This:**
- Custom build system not compatible with packaging
- Dependency version requirements not declarative
- No binary distribution infrastructure
- Installation requires source compilation

---
layout: center
---

## Dependency Ecosystem

---
### Required Dependencies

#### ROOT Framework

#### GNU Scientific Library (GSL)

#### libxml2

#### log4cpp

---
layout: center
---

### Physics Dependencies

#### LHAPDF (Parton Distribution Functions)

**Migration Status:**
- LHAPDF5: Release ~2005, last update ~2013
- LHAPDF6: Released 2013, actively maintained
- GENIE should default to LHAPDF6

#### PYTHIA (Hadronization)

**Recommendation:** Switch to PYTHIA8 as default in next major release

---
layout: center
---

### Compiler and Build Tools

---

#### Required Compilers
```yaml
C++ Compiler: g++ 4.8+ or clang 3.4+
              (Newer versions may require fixes)
Fortran:      gfortran (for PYTHIA6 linking)
              NOT g77 (obsolete)
Configure:    --enable-gfortran (modern)
              --enable-g2c (legacy, avoid)
```

**Compatibility Notes:**
- GCC 11+ may produce warnings/errors in old code
- Clang on macOS may need special flags
- M1/M2 Macs require ARM-compatible ROOT and dependencies

---

#### Build System
```yaml
Make:         GNU Make required
Perl:         For configure script
Shell:        Bash for setup scripts
```

---
layout: center
---

### Installation Challenges

---

**Dependency Hell Example:**
```
User tries to build GENIE
├── ROOT 6.28 found → OK
├── ROOT lacks MathMore → ERROR: Install GSL and rebuild ROOT
│   ├── Install GSL → Rebuild ROOT → OK
├── LHAPDF not found → Install LHAPDF5
│   ├── LHAPDF5 not in repos → Download source → Build manually
├── PYTHIA6 not found → ERROR
│   ├── Download PYTHIA6 source (hard to find)
│   ├── Build with gfortran → Get library
├── Configure with all paths → Success
├── Make → Compile error with GCC 11 (C++17 incompatibility)
│   ├── Add -std=c++11 flag manually → Retry
├── Make install → Success
└── Runtime error: Cannot find libPythia6.so
    └── Add to LD_LIBRARY_PATH → Finally works
```

**Time Investment:** 2-8 hours for experienced users, days for newcomers

---

