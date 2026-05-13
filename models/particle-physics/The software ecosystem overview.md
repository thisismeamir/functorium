# Key4Hep Stack

Key4Hep is the common software framework for future collider experiments, FCC, CLIC, ILC, CEPC all use it. It's not one package but a full stack:

```txt
Physics analysis       FCCAnalyses (RDataFrame based)
        ↑
Reconstruction         k4RecTracker, k4RecCalorimeter, k4Pandora
        ↑
Algorithms             ACTS (tracking), PandoraPFA (particle flow)
        ↑
Framework              Gaudi (algorithm scheduling and data flow)
        ↑
Data model             EDM4hep (physics objects), podio (I/O)
        ↑
Geometry               DD4hep (detector description)
        ↑
Simulation             ddsim / Geant4
```

Every layer has a specific job and a defined interface to the layers above and below it.

**Gaudi**: is the framework that runs everything. It was originally developed for LHCb and is now shared across experiments. A Gaudi application is a sequence of Algorithms. Each algorithm reads some collections from the event store, does something, and writes new collections back. The framework handles scheduling, threading, and I/O/ You write algorithms; Gaudi runs them.

**EDM4hep**: is the event data model, the agreed set of C++ classes that represents physics objects: tracks, clusters, PFOs, MC particles, vertices. If you write a reconstruction algorithm that produces tracks, you write them as EDM4hep Track objects. If someone else's algorithm downstream needs tracks, it reads EDM4hep Track objects. The model is the contract between algorithms.

**podio** is the I/O layer underneath EDM4hep. It handles serialization to ROOT files, lazy loading, and the relationship between objects (a Track containing references to Hits). You mostly don't interact with podio directly.

**DD4hep** is the detector description toolkit. It reads a compact XML file that describes the geometry — every layer, every module, every cell. It provides the tools to: place volumes in 3D space, define sensitive detector regions, encode/decode cell IDs, and build surface maps for tracking. Every time reconstruction needs to know "where is channel `0x3A4F2B` in 3D space?" — that answer comes from DD4hep.

**ACTS** (A Common Tracking Software) is the tracking library. It implements seed finding, the Combinatorial Kalman Filter, the Gaussian Sum Filter, vertex fitting, and material maps. It's geometry-agnostic — you give it a TrackingGeometry built from DD4hep, and it works. It's also thread-safe and increasingly GPU-accelerated.

**PandoraPFA** is the particle flow framework. It defines a plugin architecture where you write content algorithms — small C++ classes that do one thing (match tracks to clusters, find photons, split merged clusters) — and chain them together. The FCC-ee reconstruction uses MarlinPandora or k4Pandora as the Gaudi wrapper.

**Setting up the environment**

The entire stack is distributed as a single Docker image and also available on CERN's CVMFS. For now the practical starting point is:

```bash
# Using the key4hep Docker image
docker pull ghcr.io/key4hep/key4hep-stack/ubuntu22.04-release:latest
docker run -it ghcr.io/key4hep/key4hep-stack/ubuntu22.04-release:latest

# Or if you have CERN access
source /cvmfs/sw.hsf.org/key4hep/setup.sh
```

We won't do this yet — there's no point touching the software before you understand what it's doing. But keep this in the back of your mind as where we're headed.