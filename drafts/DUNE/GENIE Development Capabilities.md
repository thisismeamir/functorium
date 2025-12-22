# GENIE Event Generator: Architecture and Modernization Opportunities

---
## Executive Summary

--- 

GENIE is the de facto standard neutrino interaction Monte Carlo generator, widely used by oscillation and neutrino scattering experiments worldwide. Built entirely in C++ on the CERN ROOT framework, GENIE employs object-oriented design patterns to provide experiment-agnostic physics modeling across a broad spectrum of processes. However, its codebase contains legacy components, relies on outdated toolchains, and faces challenges in installation and maintenance. This report examines GENIE's current architecture and proposes comprehensive modernization strategies.

---
## Current Architecture

---
### Core Technologies

---
**Languages and Frameworks**
- Written in traditional C++ (mid-2000s style)
- Built entirely on CERN ROOT framework
- Uses ROOT classes for event records (GHEP), I/O operations, and random number generation (TRandom3 Mersenne Twister)
- Physics modules configured via XML files
- Employs factory/registry patterns for algorithm instantiation

---
**Design Philosophy**

- Object-oriented abstractions separate physics from simulation mechanics
- Modular architecture with drivers, threads, and modules
- Flexible, experiment-agnostic design
- Supports multiple processes: quasi-elastic, resonant, deep inelastic scattering (DIS), final state interactions (FSI)

---
### Dependencies and Limitations

---
**External Libraries**

- PYTHIA6 (Fortran 77) for hadronization - a significant legacy dependency
- ROOT framework - deeply embedded throughout codebase
- CLHEP, LHAPDF, and various PDF libraries
- Heavy software stack supporting broad physics coverage

---
**Build System**
- GNU Autotools (`configure`/`make`) - traditional but inflexible
- Requires manual environment configuration
- Hard-coded paths and shell script sourcing (`$GENIE` environment variable)
- Challenging installation on modern platforms (limited M1/M2 Mac support)

**Operational Workflow**
- Reads neutrino flux and geometry inputs
- Generates events via ROOT-based event records
- Outputs primarily to ROOT file formats
- Command-line driven with XML configuration files
- Often integrated into experiment frameworks (art/LArSoft)

---
## Modernization Opportunities

---
### 1. C++ Language Upgrade

**Transition to Modern C++ (C++17/20)**

- Replace raw pointers with smart pointers for memory safety
- Utilize `auto`, range-based loops, and standard library algorithms
- Eliminate macros and old ROOT-style RTTI
- Implement constexpr, enum classes, and lambda callbacks
- Use standard containers instead of home-grown utilities
- Simplify bindings to other languages (PyBind11 compatibility)

**Benefits**

- Improved code safety and expressiveness
- Better maintainability
- Easier integration with modern tools
- Enhanced performance through standard library optimizations

---
### 2. Modular Library Architecture

**Reorganization Strategy**

- Separate core components into distinct libraries:
    - Event record management
    - Kinematics calculations
    - Nuclear models
    - Geometry and flux interfaces
- Enable selective reuse without full generator dependency

**Standardized Data Formats**

- Adopt HepMC3 as common event record format
- Improve interoperability with collider-style analysis tools
- Maintain C++ with Python/PPC compatibility

**Random Number Generation**

- Decouple from ROOT's TRandom3
- Use standard `<random>` or Boost.Random
- Reduce tight coupling to specific ROOT versions

---
### 3. Build System Modernization

**Migration to CMake**

- Replace Autotools with CMake or Meson
- Enable cross-platform support (including Windows)
- Simplify out-of-source builds
- Improve IDE integration
- Facilitate dependency detection

**Package Management**

- Create conan or spack packages
- Simplify installation in HPC and CI environments
- Enable automated dependency resolution

**Continuous Integration**

- Implement GitHub Actions or GitLab CI
- Automated testing across multiple platforms
- Code coverage reporting
- Static analysis (clang-tidy, address-sanitizer)
- Build status badges for transparency

---
### 4. Python and Multi-Language Interfaces

**Python Integration**

- Official Python bindings via PyBind11 or Boost.Python
- Expose core classes: event records, generator engine, algorithms
- Enable Python-based steering scripts
- Support Jupyter notebook workflows
- Integration with data science tools (NumPy, Pandas)

**Hybrid Model**

- Maintain C++ physics core for performance
- Provide high-level Python API (`import genie`)
- Allow pip-installable package option

**Additional Language Support**

- Julia bindings for scientific computing
- Java/Kotlin via JNI for specific use cases
- SWIG or C-interface wrappers for flexibility

---
### 5. Physics Stack Updates

**Legacy Replacement**

- Migrate from PYTHIA6 to PYTHIA8
- Update to LHAPDF8
- Remove Fortran dependencies

**Plugin Architecture**

- Leverage existing factory pattern for runtime plugins
- Enable custom C++ plugins via shared libraries
- Support alternative nuclear models (GiBUU integration)
- No main code modification required for extensions

---
### 6. Configuration and Output Formats

**Configuration Modernization**

- Support JSON and YAML alongside XML
- Implement Python-based configuration language
- Improve default logging
- User-friendly parameter files

**Output Format Diversity**

- HDF5 support for large-scale data
- CSV export for simple analysis
- Pandas-compatible outputs
- ROOT as optional format, not requirement
- Better integration with machine learning pipelines

---
### 7. Parallelism and Acceleration

**CPU Parallelization**

- Multi-threaded event generation
- C++11 threads or Intel TBB implementation
- Parallel final-state interaction calculations
- Leverage multicore architectures

**GPU Acceleration**

- Explore Vulkan-based Kompute library
- Offload compute-intensive kernels
- Many-body kinematics sampling on GPU
- Vectorized math libraries (Eigen, Vc)

**Performance Optimization**

- Vectorized operations where possible
- Modern numerical libraries
- Profiling-guided optimization

---
### 8. Software Quality and Community Practices

**Development Infrastructure**

- Modern CI/CD pipelines
- Multi-OS build testing
- Unit and integration tests
- Public issue tracking
- Code review processes

**Documentation and Transparency**

- API documentation generation
- Usage examples and tutorials
- Build/test status visibility
- Contribution guidelines
- Community engagement tools

---
## ROOT Integration Strategy

---
### Maintaining Compatibility

**Decoupling Approach**

- Treat ROOT as optional I/O backend
- Core physics outputs to abstract event format
- Optional ROOT writers for .root file generation
- Support both ROOT and alternative formats simultaneously

**Experiment Framework Support**

- Continue art/LArSoft integration
- Provide ROOT-formatted outputs on demand
- Enable ROOT histogram generation
- Converters to/from ROOT formats

**Testing Benefits**

- Simplified CI builds without ROOT dependency
- Faster development cycles
- Broader platform support
- Maintained backward compatibility

---
## Development Pathways

---
### Contributing to GENIE

**Incremental Approach**

- Add CMake build parallel to Autotools
- Develop PyBind11 wrappers for key classes
- Propose physics module migrations (e.g., Pythia8)
- Non-invasive initial contributions

**Challenges**

- Requires core team buy-in
- Major refactoring needs community consensus
- Gradual migration of XML to JSON
- Balance stability with modernization

**Recommended Strategy**

1. Modernize build system and interfaces first
2. Gradually update internal implementations
3. Maintain backward compatibility
4. Leverage existing community momentum

---
### Alternative Development (PartiKle Concept)

**New Framework Approach**

- Python/C++/Kotlin implementation
- Kompute for GPU acceleration
- DeduKt integration
- Fresh codebase with modern practices

**Advantages**

- Freedom to implement best practices from scratch
- No legacy code constraints
- Modern API design
- Language-specific optimizations

**Considerations**

- Must validate against GENIE's tuned models
- Interoperability with existing GENIE data
- Can utilize published cross-section data
- Needs compelling advantages to justify effort
- Community adoption challenges

**Interoperability Strategy**

- Read GENIE cross-section splines
- Optional ROOT output for compatibility
- Focus on ease of use, speed, and flexibility
- Maintain physics accuracy and validation

---
## Conclusions

GENIE's comprehensive physics coverage and widespread adoption have made it the standard neutrino event generator. However, its architecture reflects software practices from the mid-2000s. Modernization efforts should focus on:

1. **Immediate priorities**: Build system modernization (CMake), Python bindings, and improved documentation
2. **Medium-term goals**: C++ language upgrade, modular architecture, and standardized data formats
3. **Long-term vision**: GPU acceleration, plugin ecosystem, and comprehensive multi-language support

Whether through incremental improvements to GENIE or development of a modern alternative like PartiKle, the neutrino physics community will benefit from event generation software that combines proven physics models with contemporary software engineering practices. The key is maintaining the scientific rigor and validation that GENIE has achieved while embracing tools and techniques that improve accessibility, performance, and maintainability for the next generation of neutrino experiments.

---