# FCC Software Framework: Complete Build Guide and Configuration

## Executive Summary

This document provides a comprehensive guide to building and configuring the FCC (Future Circular Collider) software framework from source. It covers the complete build process for the software stack, including ROOT, Gaudi, and podio, along with critical troubleshooting for Boost 1.89.0 compatibility. The document details the Gaudi-based architecture, environment configuration for source-built installations, and initial operational procedures. This guide is specifically tailored for systems without CVMFS access, requiring manual dependency management and environment setup.

## 1. Framework Architecture

### 1.1 Gaudi Framework Foundation

The FCC software stack is built upon the Gaudi framework, designed to address fundamental challenges in high-energy physics computing:

- **Data Acquisition**: Efficient collection of detector-recorded data
- **Data Processing**: Optimized filtering and processing pipelines for recorded events
- **Task Management**: Coordination of complex workflows for collision data analysis
- **Event Organization**: Flexible structuring of bunch crossing data
- **Dynamic Configuration**: Software customization without recompilation requirements

### 1.2 Core Architectural Components

#### Event Loop

Individual bunch crossings (events) exhibit statistical independence, enabling sequential processing without simultaneous memory allocation. The Gaudi EventLoop processes events iteratively, optimizing memory utilization and computational efficiency.

#### Transient Event Store (TES)

The TES provides hierarchical organization of per-event data objects including Particles, Vertices, Tracks, and Hits. The structure resembles a filesystem with location paths such as `/Event/Rec/Track/Best` and `/Event/Phys/MyParticles`. The TES automatically clears at the conclusion of each event's processing cycle.

#### Algorithms

Algorithms are C++ classes integrated into the EventLoop that execute specific functions for each event. Common applications include trigger-based filtering and particle reconstruction. Each algorithm operates on data retrieved from and stored to the TES.

#### Tools

Tools implement shared functionality utilized across multiple algorithms, including vertex fitting, distance calculations, and primary vertex association. This modular approach promotes code reuse and maintains consistency across the analysis chain.

#### Options System

The Options system enables runtime configuration through Python scripts (option files). These files specify algorithm execution order, set algorithm and tool properties, and configure the EventLoop without requiring C++ recompilation. Multiple option files can be combined to create complex processing configurations.

## 2. Build Process and Dependencies

### 2.1 Build Timeline and Strategy

**Build Period**: November 19-25, 2025

The build follows a layered dependency approach, constructing foundational packages before higher-level frameworks. The sequence proceeds through ROOT, Gaudi, podio, and finally the Key4hep stack components.

### 2.2 ROOT Installation

ROOT serves as the foundational framework for data analysis and object serialization. The latest version from the GitHub repository provides necessary C++20 support.

```bash
# Clone and build ROOT
git clone https://github.com/root-project/root.git
cd root
mkdir build install
cd build

cmake -DCMAKE_INSTALL_PREFIX=../install \
      -DCMAKE_BUILD_TYPE=Release \
      -DCMAKE_CXX_STANDARD=20 \
      ..

make -j$(nproc)
make install

# Setup ROOT environment
source ../install/bin/thisroot.sh
```

**Requirements**: ROOT 6.28.04 or later (6.32+ for RNTuple support) with C++20 compilation enabled.

### 2.3 Gaudi Framework Build

Gaudi requires careful dependency management and a specific development environment. The process involves creating an isolated conda environment with precise package versions.

#### 2.3.1 Environment Preparation

```bash
# Create and activate conda environment
conda create -n fcc python=3.11
conda activate fcc

# Install essential build tools
conda install -c conda-forge cmake make pkg-config git

# CRITICAL: Install Boost 1.82 specifically
# Gaudi requires boost_python, which isn't properly configured in newer versions
# when using the disable flag method from older documentation
conda install -c conda-forge boost=1.82
```

#### 2.3.2 Additional Dependencies via Spack

Certain HEP-specific libraries are best managed through Spack rather than conda:

```bash
# Install and load additional dependencies
spack install aida heppdt clhep cppunit tbb vdt uuid fmt
spack load aida heppdt clhep cppunit tbb vdt uuid fmt
```

**Rationale**: These libraries are not required after the build completes, making Spack's temporary loading mechanism ideal. The installation script handles these dependencies reliably without polluting the permanent environment.

#### 2.3.3 Critical Boost 1.89.0 Compatibility Issue

**Problem Statement**: Gaudi fails to build with Boost 1.89.0 due to removal of the `boost_system` stub library. Although Boost.System has been header-only since version 1.69, the backward-compatibility stub was maintained until version 1.89.0, where it was completely removed.

**Technical Background**: The `boost_system` library provided a linkable stub for backward compatibility even though all functionality had migrated to headers. Gaudi's `cmake/GaudiDependencies.cmake` explicitly requests the `system` component, which no longer exists as a separate CMake target in Boost 1.89.0+.

**Error Manifestation**:

```
CMake Error at BoostConfig.cmake:141 (find_package):
  Could not find a package configuration file provided by "boost_system"
  (requested version 1.89.0)
```

**Solution**: Modify `cmake/GaudiDependencies.cmake` to remove the `system` component requirement and create a compatibility alias:

```cmake
# In cmake/GaudiDependencies.cmake

# Line 94: Remove 'system' from components list
find_package(Boost 1.70 REQUIRED COMPONENTS
  filesystem
  program_options
  regex
  thread
  # system  # REMOVED
)

# Lines 98-100: Remove system from mark_as_advanced loop
foreach(_component filesystem program_options regex thread)
  mark_as_advanced(Boost_${_component}_LIBRARY_DEBUG)
  mark_as_advanced(Boost_${_component}_LIBRARY_RELEASE)
endforeach()

# Add compatibility alias after find_package(Boost)
# Boost::system is header-only since 1.69 and removed in 1.89
# Create an alias to Boost::headers for compatibility
if(NOT TARGET Boost::system)
  add_library(Boost::system ALIAS Boost::headers)
endif()
```

**Compatibility Guarantee**: This solution maintains full backward compatibility with Boost 1.70+ (Gaudi's minimum version) while supporting 1.89.0+. The conditional alias ensures existing code referencing `Boost::system` continues to function correctly.

#### 2.3.4 Gaudi Build Execution

```bash
# Clone Gaudi repository
git clone <gaudi-repository-url>
cd Gaudi
mkdir build install
cd build

# Apply Boost 1.89.0 fix to cmake/GaudiDependencies.cmake if needed

# Configure build
cmake -DCMAKE_INSTALL_PREFIX=../install \
      -DCMAKE_BUILD_TYPE=Release \
      -DBUILD_SHARED_LIBS=YES \
      -DCURL_LIBRARY=/usr/lib/libcurl.so.4 \
      ..

# Build and install
make -j$(nproc)
make install
```

**Troubleshooting**: During configuration and build, CMake may report missing dependencies not covered in the standard installation. Document all such errors with their specific library names and versions for comprehensive troubleshooting records.

### 2.4 Podio Build

Podio provides the event data model (EDM) infrastructure for FCC. It requires Python 3.8+ with specific modules for code generation.

#### 2.4.1 Python Environment Requirements

**Critical Requirement**: Python 3.8 or later (tested with 3.13.7)

**Required Python Modules**:

- `yaml`: YAML parsing for data model definitions
- `jinja2`: Template engine for code generation
- `graphviz` (optional): Required for podio-vis visualization tool
- `tabulate` (optional): Required for podio-dump utility

```bash
# Verify Python version
python3 --version

# Install required Python packages
pip install -r requirements.txt

# On macOS, install libyaml for yaml module support
brew install libyaml

# Verify module availability
python3 -c "import yaml; import jinja2; print('All modules available')"
```

#### 2.4.2 Podio Build Process

```bash
# Clone podio repository
git clone <podio-repository-url>
cd podio
mkdir build install

# Setup environment
source ./init.sh

# Configure build
cd build
cmake -DCMAKE_INSTALL_PREFIX=../install ..

# Build and install
make -j$(nproc) install

# Run tests to verify installation
ctest --output-on-failure
```

**Test Suite**: The test suite performs unit tests and integration tests covering the complete I/O cycle. Example data files are created and validated during this process.

**Build Options**: To view available configuration options:

```bash
cd build
cmake -LH ..
```

### 2.5 Key4hep Stack Components

The Key4hep stack provides detector simulation, geometry description, and generator interfaces. Components include:

- **k4FWCore**: Core framework extensions for Key4hep
- **dd4hep**: Detector description toolkit
- **edm4hep**: Event data model for HEP
- **k4Gen**: Event generator interfaces
- **k4geo**: Detector geometry descriptions

Each component follows a similar CMake build pattern with dependencies on previously built packages.

## 3. Environment Configuration

### 3.1 Custom Setup Script

For source-built installations without CVMFS access, a comprehensive environment setup script manages all software components and their interdependencies.

### 3.2 Complete Setup Implementation

```bash
#!/bin/bash
# FCC Environment Setup Script
# Usage: source setup.sh

# Check if this script is being sourced (not executed)
if [ "${BASH_SOURCE[0]}" = "${0}" ]; then
    echo "Error: This script must be sourced, not executed directly."
    echo "Usage: source setup.sh"
    exit 1
fi

# ============================================================================
# FCC Software Stack Configuration
# ============================================================================

# Base directory for FCC software
FCC_BASE="/home/kid-a/hep/fcc-sw"

# Core packages
GAUDI_DIR="${FCC_BASE}/core/Gaudi/install"
export PATH="${GAUDI_DIR}/bin:${PATH}"
export LD_LIBRARY_PATH="${GAUDI_DIR}/lib:${LD_LIBRARY_PATH}"

PODIO_DIR="${FCC_BASE}/core/podio/install"
export PATH="${PODIO_DIR}/bin:${PATH}"
export LD_LIBRARY_PATH="${PODIO_DIR}/lib:${LD_LIBRARY_PATH}"

# Geant4
GEANT4_DIR="${FCC_BASE}/geant4/install"
export PATH="${GEANT4_DIR}/bin:${PATH}"
export LD_LIBRARY_PATH="${GEANT4_DIR}/lib:${LD_LIBRARY_PATH}"

# Delphes (non-standard structure)
DELPHES_DIR="${FCC_BASE}/delphes"
export PATH="${DELPHES_DIR}:${PATH}"
export LD_LIBRARY_PATH="${DELPHES_DIR}:${LD_LIBRARY_PATH}"

# Pythia8
PYTHIA8_DIR="${FCC_BASE}/pythia8"
export PATH="${PYTHIA8_DIR}/bin:${PATH}"
export LD_LIBRARY_PATH="${PYTHIA8_DIR}/lib:${LD_LIBRARY_PATH}"

# Key4hep stack
K4FWCORE_DIR="${FCC_BASE}/key4hep-stack/k4FWCore/install"
export PATH="${K4FWCORE_DIR}/bin:${PATH}"
export LD_LIBRARY_PATH="${K4FWCORE_DIR}/lib:${LD_LIBRARY_PATH}"

DD4HEP_DIR="${FCC_BASE}/key4hep-stack/dd4hep/install"
export PATH="${DD4HEP_DIR}/bin:${PATH}"
export LD_LIBRARY_PATH="${DD4HEP_DIR}/lib:${LD_LIBRARY_PATH}"

EDM4HEP_DIR="${FCC_BASE}/key4hep-stack/edm4hep/install"
export PATH="${EDM4HEP_DIR}/bin:${PATH}"
export LD_LIBRARY_PATH="${EDM4HEP_DIR}/lib:${LD_LIBRARY_PATH}"

K4GEN_DIR="${FCC_BASE}/key4hep-stack/k4Gen/install"
export PATH="${K4GEN_DIR}/bin:${PATH}"
export LD_LIBRARY_PATH="${K4GEN_DIR}/lib:${LD_LIBRARY_PATH}"

K4GEO_DIR="${FCC_BASE}/key4hep-stack/k4geo/install"
export PATH="${K4GEO_DIR}/bin:${PATH}"
export LD_LIBRARY_PATH="${K4GEO_DIR}/lib:${LD_LIBRARY_PATH}"

# Python paths
export PYTHONPATH="${GAUDI_DIR}/python:${PYTHONPATH}"
export PYTHONPATH="${PODIO_DIR}/python:${PYTHONPATH}"
export PYTHONPATH="${K4FWCORE_DIR}/python:${PYTHONPATH}"
export PYTHONPATH="${EDM4HEP_DIR}/python:${PYTHONPATH}"
export PYTHONPATH="${K4GEN_DIR}/python:${PYTHONPATH}"
export PYTHONPATH="${K4GEO_DIR}/python:${PYTHONPATH}"
export PYTHONPATH="${DD4HEP_DIR}/python:${PYTHONPATH}"

# CMake prefix path (helps CMake find packages)
export CMAKE_PREFIX_PATH="${GAUDI_DIR}:${CMAKE_PREFIX_PATH}"
export CMAKE_PREFIX_PATH="${PODIO_DIR}:${CMAKE_PREFIX_PATH}"
export CMAKE_PREFIX_PATH="${GEANT4_DIR}:${CMAKE_PREFIX_PATH}"
export CMAKE_PREFIX_PATH="${PYTHIA8_DIR}:${CMAKE_PREFIX_PATH}"
export CMAKE_PREFIX_PATH="${DD4HEP_DIR}:${CMAKE_PREFIX_PATH}"
export CMAKE_PREFIX_PATH="${EDM4HEP_DIR}:${CMAKE_PREFIX_PATH}"
export CMAKE_PREFIX_PATH="${K4FWCORE_DIR}:${CMAKE_PREFIX_PATH}"
export CMAKE_PREFIX_PATH="${K4GEN_DIR}:${CMAKE_PREFIX_PATH}"
export CMAKE_PREFIX_PATH="${K4GEO_DIR}:${CMAKE_PREFIX_PATH}"

# ============================================================================
echo "========================================"
echo "FCC Environment Configured"
echo "========================================"
echo "Core:"
echo "  - Gaudi: ${GAUDI_DIR}"
echo "  - podio: ${PODIO_DIR}"
echo ""
echo "Generators & Simulation:"
echo "  - Geant4: ${GEANT4_DIR}"
echo "  - Delphes: ${DELPHES_DIR}"
echo "  - Pythia8: ${PYTHIA8_DIR}"
echo ""
echo "Key4hep Stack:"
echo "  - k4FWCore: ${K4FWCORE_DIR}"
echo "  - dd4hep: ${DD4HEP_DIR}"
echo "  - edm4hep: ${EDM4HEP_DIR}"
echo "  - k4Gen: ${K4GEN_DIR}"
echo "  - k4geo: ${K4GEO_DIR}"
echo ""
echo "To restore original environment, open a new terminal"
echo "========================================"
```

### 3.3 Software Stack Components

The environment configuration manages three primary component categories:

**Core Framework**: Gaudi (event processing framework) and podio (data model library)

**Generators and Simulation**: Geant4 (detector simulation), Delphes (fast simulation), and Pythia8 (event generation)

**Key4hep Stack**: k4FWCore (framework core), dd4hep (detector description), edm4hep (event data model), k4Gen (generator interfaces), and k4geo (geometry descriptions)

## 4. Initial Operations and Validation

### 4.1 Environment Activation

The environment must be sourced (not executed) in each terminal session:

```bash
source ${FCC_SETUP}/setup.sh
```

Where `${FCC_SETUP}` represents the root directory of the FCC installation.

### 4.2 Minimal Configuration Test

To verify proper installation and configuration, create a minimal option file:

**option.py**:

```python
from Configurables import ApplicationMgr
```

Execute using the k4run command:

```bash
k4run option.py
```

### 4.3 Expected Output

A successful execution produces the following output sequence:

```
[k4run - INFO] k4run.main:
ApplicationMgr SUCCESS
=============================================================
Welcome to ApplicationMgr (GaudiCoreSvc v40r0)
  running on archlinux on Sun Nov 30 12:05:51 2025
=============================================================
ApplicationMgr       INFO Application Manager Configured successfully
ApplicationMgr       INFO Application Manager Initialized successfully
ApplicationMgr       INFO Application Manager Started successfully
EventSelector        INFO End of event input reached.
ApplicationMgr       INFO Application Manager Stopped successfully
ToolSvc              INFO Removing all tools created by ToolSvc
ApplicationMgr       INFO Application Manager Finalized successfully
ApplicationMgr       INFO Application Manager Terminated successfully
```

This output confirms successful framework initialization. Note that no data processing occurs as no algorithms or input data were specified.

### 4.4 Multiple Option Files

The k4run command accepts multiple option files, enabling modular configuration:

```bash
k4run option1.py option2.py
```

This approach facilitates separation of concerns, allowing distinct configuration aspects (detector geometry, reconstruction algorithms, analysis tools) to be maintained in separate files.

## 5. Troubleshooting Guide

### 5.1 Common Build Issues

**Missing Dependencies**: During CMake configuration, you may encounter errors regarding missing packages. Document each occurrence with:

- Exact error message
- Package name and requested version
- Resolution method (conda, spack, or manual installation)

**Library Path Issues**: If executables fail to find shared libraries at runtime:

```bash
# Verify library paths
echo $LD_LIBRARY_PATH

# Check if library exists
ldd $(which gaudi_exe)
```

**Python Module Conflicts**: When multiple Python installations exist:

```bash
# Verify which Python is being used
which python3
python3 -c "import sys; print(sys.path)"
```

### 5.2 Boost Compatibility Matrix

|Boost Version|Gaudi Status|Required Changes|
|---|---|---|
|1.70-1.81|Compatible|None|
|1.82-1.88|Compatible|None|
|1.89.0+|Requires patch|Apply GaudiDependencies.cmake fix|

### 5.3 Build Environment Verification

```bash
# Verify conda environment
conda info --envs
conda list

# Verify spack packages
spack find --loaded

# Verify CMake can find packages
cmake --find-package -DNAME=Boost -DCOMPILER_ID=GNU -DLANGUAGE=CXX -DMODE=EXIST
```

## 6. Next Steps

With the environment properly configured and validated, subsequent development activities include:

- Defining input data sources and event selection criteria
- Implementing custom algorithms for specific analysis requirements
- Configuring reconstruction and analysis tool chains
- Developing output data formats and storage solutions
- Optimizing processing performance for production-scale operations

## 7. Technical Notes

### 7.1 Environment Management

**Environment Restoration**: To restore the original shell environment, open a new terminal session rather than attempting to unset variables.

**Source vs. Execute**: The setup script must be sourced to modify the current shell's environment. Direct execution creates a subprocess that terminates without affecting the parent shell.

**Path Dependencies**: The order of PATH and LD_LIBRARY_PATH entries can affect which software versions are utilized when multiple installations exist on the system.

### 7.2 Development Best Practices

**Conda Environment Isolation**: Maintain separate conda environments for different project versions or experimental builds to avoid conflicts.

**Version Pinning**: Document exact versions of all critical dependencies to ensure reproducible builds.

**Incremental Builds**: When modifying Gaudi or related packages, use incremental builds (`make` without `clean`) to reduce compilation time during development.

**Test Suite Execution**: Always run test suites after building to catch configuration issues early. Failed tests often indicate missing dependencies or incorrect library paths.

## 8. References

### 8.1 External Documentation

- Gaudi Framework: Official documentation and developer guide
- podio: Event data model documentation
- Key4hep: Collaborative HEP software stack
- Boost Libraries: Version-specific release notes

### 8.2 Issue Tracking

**Boost 1.89.0 Compatibility**: Issue #4 and associated pull request in Gaudi repository

**Build Logs**: Maintained separately for each component build with timestamps and error resolution notes

## Appendix A: Build System Summary

|Component|Version|Python Req.|Critical Dependencies|Build Time*|
|---|---|---|---|---|
|ROOT|Latest|3.8+|C++20 compiler|~30 min|
|Gaudi|v40r0|3.11|Boost 1.82+, AIDA, CLHEP|~15 min|
|podio|Latest|3.8+|yaml, jinja2, ROOT|~5 min|
|Geant4|Latest|3.8+|ROOT|~45 min|
|dd4hep|Latest|3.8+|Geant4, ROOT|~20 min|

*Approximate times on 8-core system with parallel compilation