# Introduction

The Linux ecosystem is widely recognized for its robust software distribution and package management capabilities. However, it is not without limitations and inconsistencies. Different distributions employ distinct package management approaches, and the requirements for environments and configurations vary significantly across programming languages, projects, and software applications.

Unipac was conceived to address the fragmentation inherent in heterogeneous distribution models, disparate package management systems, and environment setup challenges. The latter issue has emerged because each community has developed solutions tailored to their specific requirements, often in isolation.

For instance, Conda environments were designed specifically to facilitate Python development, while npm serves exclusively the Node.js ecosystem. Although these tools partially address environment management within their respective domains, interoperability issues arise when using them concurrently.

Additional critical challenges in package and environment management include:
- The absence of unified diagnostic capabilities
- Inadequate version conflict resolution mechanisms
- Limited flexibility for users to customize software usage without binding system path variables to specific versions

While containerization technologies such as Docker and Podman offer isolated, reproducible environments that mitigate some dependency conflicts, they introduce significant overhead and practical limitations. 

Containers consume substantial system resources through full runtime isolation, including duplicated libraries and dependencies across multiple container instances. Furthermore, their isolated nature creates barriers to seamless integration with host system tools and workflows, requiring explicit volume mounts and network configurations. 

For use cases requiring lightweight, native performance and direct filesystem integration—such as development workflows, system utilities, and resource-constrained environments—containers represent an impractical solution that adds unnecessary complexity and resource consumption without addressing the fundamental need for unified, native package and environment management.

In this document, we present Unipac as a comprehensive solution to address the aforementioned challenges in package and environment management within the Linux ecosystem

# Project Overview

Unipac is a universal package and environment management system for Linux that solves the fundamental fragmentation problem in software dependency management. It provides a unified interface to multiple package managers, supports multiple versions of the same package simultaneously, and offers sophisticated environment isolation without the overhead of containerization.

## The Problem
Linux software management suffers from several critical issues:
### 1. Package Manager Fragmentation
- **Distro-level**: Each Linux distribution has its own package manager (apt, pacman, dnf, zypper)
- **Purpose-level**: Different languages and tools have their own package ecosystems (pip, npm, cargo, gem, conda, spack)
- **Result**: No unified way to manage dependencies across these systems
### 2. Version Conflicts
- System package managers only allow one version of a library to be installed
- Multiple applications requiring different versions of the same library cannot coexist
- Developers resort to language-specific solutions (venv, nvm, rbenv) creating further fragmentation
### 3. Environment Management Chaos
- Every tool creates its own environment solution
- No standardized way to create reproducible, inheritable environments
- Environments cannot easily be composed or layered
### 4. Heavy-Handed Solutions
- Containers (Docker) solve some problems but are resource-intensive
- Full OS images for simple dependency isolation is overkill
- Slow startup times and storage overhead (flatpak)

## The Unipac Solution

### Overview

Unipac addresses these challenges through a fundamentally different approach. Rather than relying on isolated containers or distributing packages with redundant libraries, Unipac manages dependencies and configurations at the pre-environment stage. The solution targets four principal problem domains:

1. **Heterogeneous Package Manager Protocols**: Disparate package managers employ different mechanisms for fetching, updating, and searching packages, creating fragmentation across the ecosystem.
2. **Environment-Specific Dependencies and Version Conflicts**: Different software applications require distinct libraries and packages, often with incompatible version requirements that lead to dependency conflicts.
3. **Reproducibility in Testing and Development**: Ensuring consistent, reproducible environments across testing, development, and production stages remains challenging without standardized tooling.
4. **Diagnostic Capabilities and Configuration Management**: Current solutions lack robust diagnostic tools for identifying conflicts and managing complex or aggressive environment configurations.

### Plugin-Based Package Managers

Unipac employs a plugin architecture that treats package managers as modular, interchangeable components (referred to as `repositories`). Each plugin encapsulates metadata and operational logic specific to its corresponding package manager, enabling a unified syntax for package management commands and processes across heterogeneous systems.

The `unipac` CLI provides a consistent interface for retrieving packages with explicit version and repository specifications. For example:

```bash
unipac get pip::numpy:1.0    # Retrieve NumPy version 1.0 from pip
unipac get pip::numpy         # Retrieve latest version from pip (default)
unipac get numpy              # Retrieve from first available repository
```

Critically, the `get` command downloads and stores packages without modifying the active system environment—a departure from conventional package managers that typically overwrite existing installations. This design preserves multiple versions concurrently and prevents unintended replacements.

To update an installed package, users execute:

```bash
unipac update pip::numpy:1.0
```

This command upgrades the specified `numpy 1.0` installation from pip to the latest available version. Alternatively, explicit version transitions (upgrades or downgrades) can be performed using:

```bash
unipac change pip::numpy:1.0 to pip::numpy:2.0
```

This syntax grants precise control over version management, enabling workflows previously unattainable with traditional package managers. For instance, Unipac supports simultaneous multi-repository, multi-version installations:

```bash
unipac get pip::numpy:1.3 apt::python-numpy:2.1 pacman::fuse3
```

This capability is feasible because `apt`, `pacman`, and `pip` function as plugins rather than system-level package managers, allowing Unipac to coordinate downloads across multiple channels without altering the user's system state.

Repository plugins reside in `~/.unipac/repos/` and define the interface between Unipac and underlying package managers. Below is an example plugin configuration for `pacman`:

```kotlin
repository {
    // Configuration for pacman
    name = "Pacman Repository"
    version = "1.0.0"
    description = "A sample pacman repository"
    group = RepositoryType.DISTRO
    repositoryIdentifier = "pacman"
    mirrors(
        "https://mirror1.example.com/pacman",
        "https://mirror2.example.com/pacman"
    )
    onFirstInitialization {
        println("First Initialization Hook Executed")
    }
    afterFetch {
        print("After Fetch Hook Executed")
    }
    beforeFetch {
        print("Before Fetch Hook Executed")
    }
    onFetchPackage { query ->
        // Simulate fetching packages based on the query
        println("Fetching packages for query: $query")
        emptyList()
    }
    onSearch { query ->
        // Simulate searching packages based on the query
        println("Searching packages for query: $query")
        emptyList()
    }
    onGetPackage { uniquePackageIdentifier ->
        // Simulate getting a package by its unique identifier
        println("Getting package with ID: $uniquePackageIdentifier")
        null
    }
}
```

This declarative configuration defines repository metadata, mirror URLs, and lifecycle hooks (`onFirstInitialization`, `beforeFetch`, `afterFetch`) that execute at specific stages of package operations. The `onFetchPackage`, `onSearch`, and `onGetPackage` handlers implement the core functionality for package retrieval and querying, allowing users to extend Unipac's capabilities by authoring custom repository plugins. There's a full documentation being written on how to write a repository script from scratch.

The installed packages live in `~/.unipac/packs` with the following example to showcase how different packages co-exist there:

```txt
~/.unipac/
├── packs/              # Downloaded packages
│   ├── python/
│   │   └── apt-3.11/
│   │       ├── metadata.json
│   │       ├── files/
│   │       └── dependencies.json
│   └── numpy/
│       ├── pacman-1.24/
│       └── pacman-1.26/
...
```

With the general rule `<package-name>/<repo-identifier>-<version>`.

### Package Use

Unipac does not “install into the system.” It constructs _activation models_ for each downloaded package, defined by a lightweight, declarative file called `use.unipac` within that package’s directory. This model describes how the package should be exposed to an environment at runtime: which paths should be added, which libraries should be surfaced, what executables should be made available, and how this package interacts with others.

The guiding idea is simple: **packages become self-contained activation units**. You don't mutate the system; you compose environments.

When the user requests:

```bash
unipac use numpy:1.24
```
> note: here it doesn't matter for the user what package manager it is loaded from.

Unipac reads the corresponding `use.unipac` and transparently constructs a temporary environment overlay. This overlay is isolated, reversible, and composable with other overlays. You can stack multiple packages, even conflicting versions, because each package declares its own activation scope.

The `use` mechanism has no global side effects: it simply injects the declared paths, variables, and metadata into a sandboxed shell session or a declarative environment file generated by Unipac.

Each package directory contains an `use.unipac` file generated by its repository plugin. A minimal example:

```kotlin
package {
    export(
        PATH -> "./bin",
        LD_LIBRARY_PATH -> "./lib",
        PYTHONPATH -> "./python",
        INCLUDE_PATH -> "./include"
    )
    
    meta(
        language = "python",
        entry = "./bin/python",
        version = "3.11.4",
        sourceRepo = "apt"
    )

    requires(
        "zlib:1.2.13",
        "openssl:3.0"
    )
}
```

This defines the activation contract:

- `export(...)` lists environment variables to extend relative to the package directory.
    
- `meta(...)` declares interpreter-level or integration metadata Unipac can use for deeper reasoning (toolchains, compilers, runtimes).
    
- `requires(...)` gives the dependency graph used to construct multi-package runtime environments.

Internally, `unipac use` builds a deterministic activation graph, resolves the declared exports, evaluates dependencies, and spawns a session with the composed view. Nothing is written outside the session. Nothing contaminates the global environment.

Multiple packages can be composed explicitly:

```bash
unipac use numpy:1.24 python:apt-3.11 openssl:3.0
```

At the core of this system is the unambiguous, declarative activation file—`add.model`—which formally describes how Unipac transforms a static package directory into a usable runtime component.

## Universes

A _universe_ is Unipac’s answer to reproducible, composable, non-fragile environments. Instead of copying the broken conventions of virtualenvs, Conda environments, Nix profiles, or container layers, a universe is a first-class, declarative object: a Kotlin script that describes exactly how a shell session or process should look, which packages it should expose, how conflicts are resolved, and how activation and teardown behave.

A universe file is simply another Unipac DSL artifact. But unlike `add.model`, which describes one package, a universe describes an entire environment graph. Universes can inherit from one another, override decisions, bind multiple versions of a package to different consumers, and define activation logic. They can be stored under `~/.unipac/universes/` or distributed as standalone `.unipac` files.

### CLI-Driven Universe Creation

Users can create a new universe interactively:

```bash
unipac make <universe-name>
```

The CLI walks the user through a structured, deterministic process:

1. Name and initialize the universe.
    
2. Search for packages (installed or not-yet-installed) across all repositories.
    
3. Add packages and choose versions.
    
4. Resolve dependency chains, with explicit visibility into conflicts.
    
5. Define consumers (logical applications or workflows within the universe).
    
6. Configure hooks and environment variables.
    
7. Finalize and write the script under `~/.unipac/universes/<name>.unipac`.

A typical dialogue might look like this:

```bash
$ unipac make research-env
[1] Select packages for this universe.
Search term: python
 → python:3.11 (apt)
 → python:3.12 (apt)
Select version: 3.11

Search term: numpy
 → numpy:1.24 (pip)
 → numpy:1.26 (pip)
Add both? [y/N] y

Search term: jupyter
 → jupyter:4.0 (pip)
Select version: 4.0

[2] Resolve dependencies:
 - numpy:1.26 requires python>=3.10 → satisfied by python:3.11
 - jupyter requires python>=3.8 → satisfied
Continue? [Y/n] y

[3] Define consumers:
Create consumer? [Y/n] y
Consumer name: analysis
Select packages for 'analysis':
 - numpy:1.26
 - python:3.11
Add? [Y/n] y

Create another consumer? [Y/n] y
Consumer name: notebooks
Select packages:
 - numpy:1.24
 - python:3.11
 - jupyter:4.0
Add? [Y/n] y

[4] Add activation hooks?
Add env var? [Y/n] y
Key: PYTHONWARNINGS
Val: ignore

Add onActivate command? [Y/n] y
Command: echo 'Analysis universe activated'

Finalize universe? [Y/n] y

Universe 'research-env' created at:
~/.unipac/universes/research-env.unipac
```

The CLI produces a complete, deterministic Kotlin universe file reflecting the choices made. That script is now a reproducible specification for anyone using Unipac.

### Universe Script DSL

Below is the full script example, matching the earlier conceptual description but fully formalized and idiomatic for the Unipac Universe DSL:

```kotlin
universe {
    name = "data-science-project"
    
    // Inherit from existing universes
    inherits("base-python", "gpu-tools")
    
    // Package definitions
    packages {
        add("python", "3.11", from = "apt")
        add("numpy", "1.24", from = "pip")
        add("numpy", "1.26", from = "pip")
        add("tensorflow", "2.15", from = "pip")
        add("cuda", "12.0", from = "nvidia")
    }
    
    // Logical consumers of different package graphs
    consumers {
        app("python") {
            uses("numpy:1.24")
        }
        
        app("jupyter") {
            uses("numpy:1.24")
            uses("python:3.11")
        }
        
        app("tensorflow-train") {
            uses("numpy:1.26")
            uses("tensorflow:2.15")
            uses("cuda:12.0")
        }
    }
    
    // Activation and teardown logic
    onActivate {
        env("CUDA_HOME", "/unipac/packages/cuda/12.0")
        env("TF_FORCE_GPU_ALLOW_GROWTH", "true")
        run("echo 'Universe activated'")
    }
    
    onDeactivate {
        run("cleanup.sh")
    }
}
```

This file fully defines a reproducible, multi-version-capable, multi-consumer environment.  
Once created, the universe can be activated with:

```bash
unipac enter data-science-project
```

or embedded in scripts, shells, CI pipelines, and distributed workflows without contaminating the system or requiring heavyweight containerization.

#project #unipac #spec