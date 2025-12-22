# Unipac — Unified Multi-Distro Package Environment Manager

## Executive Summary

Unipac is a next-generation Linux package environment manager that enables users to run multiple distributions' packages simultaneously on a single host without containers, virtual machines, or system-wide conflicts. It solves the fundamental problem of version conflicts, library incompatibilities, and distribution lock-in through a combination of FUSE-based filesystem virtualization, git-versioned environment state, and intelligent multi-distro dependency resolution.

**Key Innovation:** Unipac treats different distributions' packages as composable layers that can be mixed declaratively, with transparent filesystem redirection ensuring even hardcoded paths work correctly.

### Target Audiences

1. **Daily Linux Users:** Install any package from any distro without distro-hopping or sacrificing system stability
2. **Developers:** Test and build software against multiple distro configurations simultaneously
3. **Power Users:** Manage multiple versions of the same software (Python 3.9, 3.10, 3.12) with instant switching and zero conflicts
4. **Build Engineers:** Reproducible, shareable build environments that work across all distros

### Core Requirements

- **Zero Mounting Complexity:** No manual overlayfs or namespace management
- **Multi-Distro Support:** Mix Arch, Ubuntu, Fedora packages in single environment
- **Minimal Performance Overhead:** <5% runtime cost, <50ms activation time
- **Complete Transparency:** Works with hardcoded binaries without patching
- **Git-Based Versioning:** Full rollback, branching, and history for environments
- **Declarative & Shareable:** Environments defined in YAML, distributed via Git

---

## Architecture Overview

### High-Level Components

```
┌─────────────────────────────────────────────────────────┐
│                    User Applications                     │
│         (Python, GCC, Chromium, custom builds)          │
└──────────────────────┬──────────────────────────────────┘
                       │ Standard POSIX filesystem calls
                       ↓
┌─────────────────────────────────────────────────────────┐
│              FUSE Virtual Filesystem Layer               │
│                     (unipacfs)                           │
│  • Path interception & redirection                       │
│  • Multi-layer resolution (priority-based)               │
│  • Dynamic library path rewriting                        │
│  • Aggressive caching for performance                    │
└──────────────────────┬──────────────────────────────────┘
                       │
        ┌──────────────┼──────────────┐
        ↓              ↓              ↓
┌──────────────┐ ┌──────────────┐ ┌──────────────┐
│  Arch Repo   │ │ Ubuntu Repo  │ │ Fedora Repo  │
│   (Git)      │ │   (Git)      │ │   (Git)      │
│              │ │              │ │              │
│ usr/bin/     │ │ usr/bin/     │ │ usr/bin/     │
│ usr/lib/     │ │ usr/lib/     │ │ usr/lib/     │
└──────────────┘ └──────────────┘ └──────────────┘
        ↑              ↑              ↑
        │              │              │
        └──────────────┴──────────────┘
                       │
┌─────────────────────────────────────────────────────────┐
│           Unipac Core Engine (Kotlin + C++)             │
│                                                          │
│  • PackageIR: Distro-agnostic package representation     │
│  • Multi-distro dependency resolver                      │
│  • ABI compatibility validator                           │
│  • Native package manager orchestration                  │
│  • Git version control integration                       │
│  • Environment lifecycle management                      │
└──────────────────────┬──────────────────────────────────┘
                       │ gRPC / CLI
                       ↓
┌─────────────────────────────────────────────────────────┐
│                 User Interface Layer                     │
│  • CLI (primary interface)                               │
│  • GUI (Compose Multiplatform - optional)                │
│  • Desktop integration (app wrappers)                    │
└─────────────────────────────────────────────────────────┘
```

### Component Responsibilities

#### 1. FUSE Virtual Filesystem (unipacfs)

**Technology:** C++20, libfuse3

**Purpose:** Provides transparent filesystem redirection so applications see a unified view of files from multiple distro repositories.

**Key Features:**

- Intercepts filesystem syscalls (`open`, `openat`, `stat`, `readlink`)
- Consults resolution map to redirect paths to correct repository
- Maintains in-memory cache for hot paths (LRU eviction)
- Supports both explicit overrides and priority-based layer resolution
- Zero-copy passthrough for files not in any managed layer

**Performance Targets:**

- Cold lookup: <1ms
- Cached lookup: <50μs
- Overall runtime overhead: <5%

#### 2. Unipac Core Engine

**Technology:** Kotlin (JVM) for orchestration, C++ for performance-critical operations

**Responsibilities:**

**A. Package Manager Abstraction Layer**

- Plugin system for native package managers (pacman, apt, dnf, zypper)
- Each plugin translates native metadata → PackageIR
- Invokes native PMs with custom root directories (`pacman -r`, `apt -o Dir=`)
- Never allows PMs to write to global system paths

**B. PackageIR (Intermediate Representation)**

- Canonical, distro-agnostic package metadata format
- Includes: dependencies, conflicts, ABI requirements, file lists
- Enables cross-distro dependency resolution

**C. Multi-Distro Dependency Resolver**

- Builds unified dependency graph from multiple distros
- Detects conflicts (file path collisions, ABI incompatibilities)
- Produces installation plan with conflict warnings

**D. ABI Compatibility Validator**

- Checks glibc, libstdc++, and other critical library versions
- Warns when mixing packages with incompatible ABIs
- Maintains compatibility matrix (which distro versions can coexist)

**E. Git Integration Layer**

- Each environment is a Git repository
- Package operations = Git commits
- Enables rollback, branching, diffing, remotes

**F. Environment Lifecycle Manager**

- Create, activate, deactivate, destroy environments
- Mount/unmount FUSE filesystems
- Generate environment activation scripts

#### 3. Repository Storage

**Structure:**

```
~/.unipac/
  repos/
    arch/
      base/                    # Base Arch environment
        .git/                  # Git repo
        .unipac/
          manifest.json        # Installed packages
          config.yaml          # Environment definition
          resolution-map.json  # FUSE lookup table
        usr/
          bin/
          lib/
          share/
      
      my-project/              # Derived environment
        .git/
        .unipac/
        usr/                   # Symlinks to base + new packages
    
    ubuntu/
      py312/
        .git/
        .unipac/
        usr/
  
  mounts/                      # FUSE mountpoints
    my-project/
      usr/                     # Virtual filesystem
  
  store/                       # Content-addressable package storage
    <sha256-hash>/             # Deduplicated package files
  
  cache/
    packageir/                 # Cached PackageIR blobs
    metadata/                  # Native PM metadata cache
```

#### 4. User Interface

**CLI (Primary):**

- Simple, intuitive commands modeled after git/npm
- Rich output with progress bars, colored diffs
- Shell completion support

**GUI (Future):**

- Compose Multiplatform (cross-platform desktop)
- Visual environment explorer
- Dependency graph visualization
- Interactive conflict resolution

---

## Core Data Structures

### PackageIR Schema

The neutral canonical representation that all package managers produce.

```json
{
  "spec_version": "1.0",
  "name": "python3.12",
  "version": "3.12.1-1ubuntu1",
  "distro": {
    "id": "ubuntu",
    "release": "24.04",
    "codename": "noble"
  },
  
  "provides": [
    {"name": "python3", "version": "3.12"},
    {"name": "python", "version": "3.12"}
  ],
  
  "requires": [
    {
      "name": "libc6",
      "version_constraint": ">=2.35",
      "abi": {
        "soname": "libc.so.6",
        "symbol_versions": ["GLIBC_2.35", "GLIBC_2.36"]
      }
    },
    {
      "name": "libssl3",
      "version_constraint": ">=3.0.0"
    }
  ],
  
  "conflicts": [
    {
      "name": "python3.11",
      "reason": "Binary path collision: /usr/bin/python3"
    }
  ],
  
  "files": [
    {
      "path": "/usr/bin/python3.12",
      "type": "executable",
      "size": 14328,
      "permissions": "0755"
    },
    {
      "path": "/usr/lib/python3.12/",
      "type": "directory"
    },
    {
      "path": "/usr/lib/x86_64-linux-gnu/libpython3.12.so.1.0",
      "type": "shared_library",
      "soname": "libpython3.12.so.1.0",
      "size": 4819232
    }
  ],
  
  "abi_info": {
    "glibc_required": "2.35",
    "arch": "x86_64",
    "compiler": "gcc-12.2.0",
    "cxxabi": "1.3.14",
    "kernel_min": "5.15"
  },
  
  "metadata": {
    "homepage": "https://www.python.org",
    "license": "PSF",
    "description": "Interactive high-level object-oriented language",
    "install_size": 145829888
  }
}
```

### Environment Definition (unipac.yaml)

User-facing declarative format for defining environments.

```yaml
unipac_version: "1.0"

environment:
  id: my-mixed-dev
  description: "Mixed distro development environment for Project X"
  
  # Multi-distro layers (evaluated in priority order)
  layers:
    - id: arch-base
      distro: arch
      priority: 1
      packages:
        - gcc=13.2.1
        - make
        - cmake>=3.25
        - git
    
    - id: ubuntu-python
      distro: ubuntu
      release: "24.04"
      priority: 2
      packages:
        - python3.12
        - python3.12-dev
        - python3-pip
        - python3-venv
    
    - id: fedora-libs
      distro: fedora
      release: "39"
      priority: 3
      packages:
        - special-fedora-lib
  
  # Explicit path overrides (when auto-resolution isn't enough)
  overrides:
    /usr/bin/python: ubuntu-python:/usr/bin/python3.12
    /usr/bin/python3: ubuntu-python:/usr/bin/python3.12
    /usr/lib/libspecial.so: fedora-libs:/usr/lib64/libspecial.so
  
  # Environment variables set on activation
  environment_vars:
    CC: /usr/bin/gcc
    CXX: /usr/bin/g++
    PYTHON: /usr/bin/python3.12
    PROJECT_ROOT: "${PWD}"
  
  # Post-installation hooks
  post_install:
    - pip install --user numpy scipy matplotlib
    - pip install -e .
  
  # ABI validation policy
  abi_policy: warn  # Options: strict, warn, ignore
  
  # Resolution strategy when multiple layers provide same file
  resolution_strategy: last-wins  # Options: last-wins, first-wins, explicit-only
```

### FUSE Resolution Map

Internal data structure used by unipacfs for fast lookups.

```json
{
  "environment_id": "my-mixed-dev",
  "version": 1,
  "updated_at": "2025-11-26T15:30:00Z",
  
  "layers": [
    {
      "id": "arch-base",
      "priority": 1,
      "distro": "arch",
      "prefix": "/home/user/.unipac/repos/arch/base",
      "enabled": true
    },
    {
      "id": "ubuntu-python",
      "priority": 2,
      "distro": "ubuntu",
      "prefix": "/home/user/.unipac/repos/ubuntu/py312",
      "enabled": true
    }
  ],
  
  "explicit_overrides": {
    "/usr/bin/python": "/home/user/.unipac/repos/ubuntu/py312/usr/bin/python3.12",
    "/usr/bin/python3": "/home/user/.unipac/repos/ubuntu/py312/usr/bin/python3.12"
  },
  
  "path_cache": {
    "/usr/bin/gcc": {
      "real_path": "/home/user/.unipac/repos/arch/base/usr/bin/gcc",
      "layer_id": "arch-base",
      "cached_at": "2025-11-26T15:32:14Z",
      "hit_count": 1247
    }
  },
  
  "resolution_strategy": "last-wins"
}
```

---

## Key Technical Designs

### 1. FUSE Filesystem Implementation

#### Path Resolution Algorithm

```cpp
// unipacfs core lookup function
struct LookupResult {
    std::string real_path;
    std::string layer_id;
    bool found;
};

class UnipacFS {
private:
    ResolutionMap resolution_map_;
    LRUCache<std::string, LookupResult> path_cache_;
    
public:
    LookupResult lookup(const std::string& requested_path) {
        // 1. Check cache first
        if (auto cached = path_cache_.get(requested_path)) {
            return *cached;
        }
        
        // 2. Check explicit overrides
        if (resolution_map_.explicit_overrides.contains(requested_path)) {
            auto real_path = resolution_map_.explicit_overrides[requested_path];
            if (fs::exists(real_path)) {
                auto result = LookupResult{real_path, "override", true};
                path_cache_.put(requested_path, result);
                return result;
            }
        }
        
        // 3. Walk layers in priority order (highest first)
        auto layers = resolution_map_.layers;
        std::sort(layers.begin(), layers.end(), 
                  [](const Layer& a, const Layer& b) {
                      return a.priority > b.priority;
                  });
        
        for (const auto& layer : layers) {
            if (!layer.enabled) continue;
            
            std::string candidate = layer.prefix + requested_path;
            if (fs::exists(candidate)) {
                auto result = LookupResult{candidate, layer.id, true};
                path_cache_.put(requested_path, result);
                return result;
            }
        }
        
        // 4. Not found in any layer
        return LookupResult{"", "", false};
    }
};
```

#### FUSE Operations

```cpp
// Key FUSE callbacks
static int unipac_getattr(const char* path, struct stat* stbuf,
                          struct fuse_file_info* fi) {
    auto result = fs_instance->lookup(path);
    
    if (!result.found) {
        return -ENOENT;
    }
    
    // Stat the real file
    if (stat(result.real_path.c_str(), stbuf) == -1) {
        return -errno;
    }
    
    return 0;
}

static int unipac_open(const char* path, struct fuse_file_info* fi) {
    auto result = fs_instance->lookup(path);
    
    if (!result.found) {
        return -ENOENT;
    }
    
    // Open the real file
    int fd = open(result.real_path.c_str(), fi->flags);
    if (fd == -1) {
        return -errno;
    }
    
    fi->fh = fd;
    return 0;
}

static int unipac_read(const char* path, char* buf, size_t size,
                       off_t offset, struct fuse_file_info* fi) {
    // Direct read from fd (no additional lookup needed)
    int res = pread(fi->fh, buf, size, offset);
    if (res == -1) {
        return -errno;
    }
    
    return res;
}
```

#### Performance Optimizations

**1. Multi-level Caching:**

```cpp
class CacheHierarchy {
    // L1: Hot path cache (lock-free, thread-local)
    thread_local static std::array<CacheEntry, 64> hot_cache_;
    
    // L2: LRU cache (shared, mutex-protected)
    LRUCache<std::string, LookupResult> main_cache_;
    
    // L3: Negative cache (paths that don't exist)
    BloomFilter negative_cache_;
};
```

**2. Kernel FUSE Features:**

```cpp
struct fuse_conn_info_opts opts = FUSE_CONN_INFO_OPTS_INIT;
opts.max_readahead = 128 * 1024;  // 128KB readahead
opts.max_write = 128 * 1024;
opts.async_read = 1;
opts.writeback_cache = 1;  // Kernel-side write caching

fuse_session_new(&args, &unipac_ops, sizeof(unipac_ops), &opts);
```

**3. Inotify-based Cache Invalidation:**

```cpp
class CacheInvalidator {
    void watch_repository(const std::string& repo_path) {
        int fd = inotify_init1(IN_NONBLOCK);
        inotify_add_watch(fd, repo_path.c_str(), 
                         IN_MODIFY | IN_CREATE | IN_DELETE);
        
        // Background thread processes events
        std::thread([this, fd]() {
            while (running_) {
                auto events = read_inotify_events(fd);
                for (const auto& event : events) {
                    invalidate_cache_for_path(event.path);
                }
            }
        }).detach();
    }
};
```

### 2. Multi-Distro Dependency Resolution

#### PackageIR Graph Building

```kotlin
class DependencyResolver {
    private val packageIndex = mutableMapOf<String, PackageIR>()
    private val conflicts = mutableListOf<Conflict>()
    
    fun resolve(layers: List<EnvironmentLayer>): ResolutionResult {
        // Phase 1: Collect all PackageIR from all layers
        for (layer in layers.sortedBy { it.priority }) {
            val pm = PackageManagerFactory.create(layer.distro)
            
            for (pkgSpec in layer.packages) {
                val pkgIR = pm.fetchPackageIR(pkgSpec)
                processPackage(pkgIR, layer)
            }
        }
        
        // Phase 2: Resolve dependencies recursively
        val resolved = mutableSetOf<PackageIR>()
        val queue = ArrayDeque(packageIndex.values)
        
        while (queue.isNotEmpty()) {
            val pkg = queue.removeFirst()
            if (pkg in resolved) continue
            
            for (dep in pkg.requires) {
                val depPkg = findSatisfyingPackage(dep)
                if (depPkg == null) {
                    conflicts.add(MissingDependency(pkg, dep))
                } else {
                    queue.add(depPkg)
                }
            }
            
            resolved.add(pkg)
        }
        
        // Phase 3: Detect conflicts
        detectFileCollisions(resolved)
        detectABIConflicts(resolved)
        
        return ResolutionResult(
            packages = resolved.toList(),
            conflicts = conflicts,
            satisfiable = conflicts.none { it.severity == Severity.ERROR }
        )
    }
    
    private fun processPackage(pkg: PackageIR, layer: EnvironmentLayer) {
        // Check for conflicts with existing packages
        for ((name, existing) in packageIndex) {
            if (pkg.conflictsWith(existing)) {
                val conflict = PackageConflict(pkg, existing)
                
                // Resolution: higher priority layer wins
                if (layer.priority > existing.layer.priority) {
                    packageIndex[name] = pkg
                    conflicts.add(conflict.copy(
                        resolution = "Replaced by higher priority layer"
                    ))
                } else {
                    conflicts.add(conflict.copy(
                        resolution = "Ignored (lower priority)"
                    ))
                }
            }
        }
        
        packageIndex[pkg.name] = pkg
    }
}
```

#### ABI Compatibility Checking

```kotlin
class ABIValidator {
    private val compatibilityMatrix = loadCompatibilityMatrix()
    
    fun validate(packages: List<PackageIR>): List<ABIConflict> {
        val conflicts = mutableListOf<ABIConflict>()
        
        // Group packages by required glibc version
        val glibcGroups = packages.groupBy { it.abiInfo.glibcRequired }
        
        if (glibcGroups.size > 1) {
            // Multiple glibc versions present
            val versions = glibcGroups.keys.sorted()
            val minVersion = versions.first()
            val maxVersion = versions.last()
            
            // Check if versions are forward-compatible
            if (!isForwardCompatible("glibc", minVersion, maxVersion)) {
                conflicts.add(ABIConflict(
                    component = "glibc",
                    requiredVersions = versions,
                    severity = Severity.ERROR,
                    message = "Incompatible glibc versions: " +
                             "packages require both $minVersion and $maxVersion"
                ))
            } else {
                conflicts.add(ABIConflict(
                    component = "glibc",
                    requiredVersions = versions,
                    severity = Severity.WARNING,
                    message = "Mixed glibc versions ($minVersion, $maxVersion). " +
                             "Should work (forward compatible) but test thoroughly."
                ))
            }
        }
        
        // Similar checks for libstdc++, libgcc, etc.
        validateCxxABI(packages, conflicts)
        validateCompilerABI(packages, conflicts)
        
        return conflicts
    }
    
    private fun isForwardCompatible(
        component: String,
        older: String,
        newer: String
    ): Boolean {
        return compatibilityMatrix[component]?.let { rules ->
            when (rules.direction) {
                CompatibilityDirection.FORWARD -> true  // glibc is forward-compat
                CompatibilityDirection.BACKWARD -> false
                CompatibilityDirection.EXACT -> older == newer
            }
        } ?: false
    }
}
```

### 3. Git Integration for Version Control

#### Repository Initialization

```kotlin
class GitBackedRepository(
    val path: Path,
    val distro: Distro
) {
    private val git = Git.open(path.toFile())
    
    companion object {
        fun create(path: Path, distro: Distro): GitBackedRepository {
            Files.createDirectories(path)
            
            // Initialize Git repo
            val git = Git.init()
                .setDirectory(path.toFile())
                .call()
            
            // Create .unipac metadata directory
            val metaDir = path.resolve(".unipac")
            Files.createDirectories(metaDir)
            
            // Initial manifest
            val manifest = Manifest(
                version = 1,
                distro = distro,
                packages = emptyList(),
                createdAt = Instant.now()
            )
            Files.writeString(
                metaDir.resolve("manifest.json"),
                Json.encodeToString(manifest)
            )
            
            // Initial commit
            git.add().addFilepattern(".").call()
            git.commit()
                .setMessage("Initial Unipac environment for ${distro.id}")
                .call()
            
            return GitBackedRepository(path, distro)
        }
    }
    
    fun installPackage(pkg: PackageSpec): InstallResult {
        // 1. Use native PM to install to this repo
        val pm = PackageManagerFactory.create(distro)
        val installResult = pm.installToPrefix(pkg, path)
        
        if (!installResult.success) {
            return InstallResult.failure(installResult.error)
        }
        
        // 2. Update manifest
        val manifest = loadManifest()
        val updatedManifest = manifest.copy(
            packages = manifest.packages + pkg,
            updatedAt = Instant.now()
        )
        saveManifest(updatedManifest)
        
        // 3. Git commit
        git.add().addFilepattern(".").call()
        git.commit()
            .setMessage("Install ${pkg.name}=${pkg.version}")
            .setAuthor("unipac", "unipac@localhost")
            .call()
        
        return InstallResult.success(pkg)
    }
    
    fun rollback(commitId: String): RollbackResult {
        try {
            // Checkout the specified commit
            git.checkout()
                .setName(commitId)
                .call()
            
            // Reload manifest from checked-out state
            val manifest = loadManifest()
            
            return RollbackResult.success(
                commit = commitId,
                packages = manifest.packages
            )
        } catch (e: GitAPIException) {
            return RollbackResult.failure(e.message ?: "Git checkout failed")
        }
    }
    
    fun history(limit: Int = 50): List<CommitInfo> {
        return git.log()
            .setMaxCount(limit)
            .call()
            .map { commit ->
                CommitInfo(
                    id = commit.id.name,
                    message = commit.shortMessage,
                    author = commit.authorIdent.name,
                    timestamp = Instant.ofEpochSecond(commit.commitTime.toLong())
                )
            }
    }
    
    fun branch(newBranchName: String): BranchResult {
        try {
            git.branchCreate()
                .setName(newBranchName)
                .call()
            
            return BranchResult.success(newBranchName)
        } catch (e: GitAPIException) {
            return BranchResult.failure(e.message ?: "Branch creation failed")
        }
    }
}
```

#### Optimization: Git LFS for Large Binaries

For repositories with large binaries, use Git LFS to avoid bloating the repository:

```bash
# .gitattributes in each repo
*.so filter=lfs diff=lfs merge=lfs -text
*.a filter=lfs diff=lfs merge=lfs -text
usr/bin/* filter=lfs diff=lfs merge=lfs -text
```

Alternative: **Hybrid approach** (recommended)

- Don't store binaries in Git at all
- Git only tracks `manifest.json` (package list + versions)
- Binaries stored in content-addressable store: `~/.unipac/store/<sha256>/`
- On checkout, reconstruct filesystem from manifest by symlinking to store

```kotlin
fun reconstructFromManifest(manifest: Manifest, targetPath: Path) {
    for (pkg in manifest.packages) {
        val packageDir = packageStore.get(pkg.hash)
        
        // Create symlinks from repo to store
        for (file in pkg.files) {
            val link = targetPath.resolve(file.path)
            val target = packageDir.resolve(file.path)
            
            Files.createSymbolicLink(link, target)
        }
    }
}
```

This keeps Git repos tiny (<1MB) while still providing full version control.

### 4. Native Package Manager Integration

#### Plugin Interface

```cpp
// pm_plugin.hpp
class PMPlugin {
public:
    virtual ~PMPlugin() = default;
    
    // Metadata fetching
    virtual PackageIR fetch_metadata(const std::string& package_name) = 0;
    virtual std::vector<PackageIR> search(const std::string& query) = 0;
    virtual std::vector<PackageIR> list_installed(const std::string& prefix) = 0;
    
    // Installation
    virtual InstallResult install_to_prefix(
        const PackageSpec& spec,
        const std::string& prefix
    ) = 0;
    
    virtual UninstallResult uninstall_from_prefix(
        const std::string& package_name,
        const std::string& prefix
    ) = 0;
    
    // Validation
    virtual bool verify_installation(
        const std::string& package_name,
        const std::string& prefix
    ) = 0;
};
```

#### Pacman Plugin Implementation

```cpp
class PacmanPlugin : public PMPlugin {
private:
    std::string pacman_binary_ = "/usr/bin/pacman";
    
public:
    PackageIR fetch_metadata(const std::string& package_name) override {
        // Query pacman database
        auto output = exec_command({
            pacman_binary_, "-Si", package_name
        });
        
        return parse_pacman_info(output);
    }
    
    InstallResult install_to_prefix(
        const PackageSpec& spec,
        const std::string& prefix
    ) override {
        // Ensure prefix exists
        std::filesystem::create_directories(prefix);
        
        // Prepare pacman command with custom root
        std::vector<std::string> cmd = {
            pacman_binary_,
            "-r", prefix,                           // Custom root
            "--dbpath", prefix + "/var/lib/pacman", // Custom DB
            "-S",                                   // Sync install
            "--noconfirm",                          // No prompts
            "--needed",                             // Skip if already installed
            spec.to_string()
        };
        
        // Execute
        auto result = exec_command(cmd);
        
        if (result.exit_code != 0) {
            return InstallResult::failure(result.stderr);
        }
        
        // Generate PackageIR from installed package
        auto pkg_ir = fetch_metadata(spec.name);
        pkg_ir.installed_prefix = prefix;
        
        return InstallResult::success(pkg_ir);
    }
    
private:
    PackageIR parse_pacman_info(const std::string& output) {
        PackageIR ir;
        
        // Parse output format:
        // Name            : python
        // Version         : 3.12.1-1
        // Description     : ...
        // Depends On      : libc>=2.38 libffi ...
        
        std::istringstream stream(output);
        std::string line;
        
        while (std::getline(stream, line)) {
            if (line.starts_with("Name")) {
                ir.name = extract_value(line);
            } else if (line.starts_with("Version")) {
                ir.version = extract_value(line);
            } else if (line.starts_with("Depends On")) {
                ir.requires = parse_dependencies(extract_value(line));
            } else if (line.starts_with("Conflicts With")) {
                ir.conflicts = parse_conflicts(extract_value(line));
            }
        }
        
        return ir;
    }
};
```

#### APT Plugin Implementation

```cpp
class APTPlugin : public PMPlugin {
private:
    std::string apt_get_binary_ = "/usr/bin/apt-get";
    std::string dpkg_binary_ = "/usr/bin/dpkg";
    
public:
    InstallResult install_to_prefix(
        const PackageSpec& spec,
        const std::string& prefix
    ) override {
        // APT requires fakechroot to install to custom prefix
        std::vector<std::string> cmd = {
            "fakechroot",
            "fakeroot",
            apt_get_binary_,
            "-o", "Dir=" + prefix,
            "-o", "Dir::State::status=" + prefix + "/var/lib/dpkg/status",
            "install",
            "-y",
            spec.to_string()
        };
        
        auto result = exec_command(cmd);
        
        if (result.exit_code != 0) {
            return InstallResult::failure(result.stderr);
        }
        
        auto pkg_ir = fetch_metadata(spec.name);
        pkg_ir.installed_prefix = prefix;
        
        return InstallResult::success(pkg_ir);
    }
    
    PackageIR fetch_metadata(const std::string& package_name) override {
        // Use apt-cache to get package info
        auto output = exec_command({
            "apt-cache", "show", package_name
        });
        
        return parse_apt_info(output);
    }
};
```

---

## CLI Design & User Experience

### Command Structure

Unipac follows a git-like command structure for familiarity:

```bash
unipac <command> [options] [arguments]
```

### Core Commands

#### Environment Management

```bash
# Create new environment
unipac create <env-id> --distro <distro> [--from <parent-env>]
unipac create py39 --distro arch
unipac create py39-dev --from py39

# List environments
unipac list
unipac list --distro arch

# Show environment details
unipac info <env-id>
unipac info py39 --verbose

# Delete environment
unipac delete <env-id>
unipac delete py39 --force

# Clone environment
unipac clone <source-env> <new-env>
```

#### Package Operations

```bash
# Install packages
unipac install <pkg>... [-e <env>]
unipac install python=3.9 numpy cmake -e py39

# Search for packages
unipac search <query> [--distro <distro>]
unipac search python --distro ubuntu

# List installed packages
unipac packages -e <env>
unipac packages -e py39 --tree  # Show dependency tree

# Uninstall packages
unipac uninstall <pkg> -e <env>
unipac uninstall scipy -e py39
```

#### Activation & Sessions

```bash
# Activate environment (modify current shell)
eval $(unipac activate <env>)

# Start new shell with environment
unipac shell <env>
unipac shell py39

# Run command in environment
unipac run <env> <command>
unipac run py39 python --version

# Deactivate current environment
unipac deactivate
```

#### Version Control

```bash
# Show history
unipac history <env> [--limit <n>]
unipac history py39 --limit 20

# Rollback to previous state
unipac rollback <env> <commit-id>
unipac rollback py39 abc1234

# Create branch
unipac branch <env> <branch-name>
unipac branch py39 experimental

# Switch branch
unipac checkout <env> <branch>
unipac checkout py39 experimental

# Show diff between states
unipac diff <env> [<commit1> <commit2>]
unipac diff py39 HEAD~1 HEAD
```

#### Multi-Distro Operations

```bash
# Create multi-distro environment from config
unipac setup [<config-file>]
unipac setup unipac.yaml

# Validate multi-distro environment
unipac validate <env>
unipac validate my-mixed-dev --strict

# Show layer information
unipac layers <env>
```

#### Diagnostics

```bash
# Check environment health
unipac doctor <env>

# Repair environment
unipac repair <env>

# Show detailed debug info
unipac debug <env>
```

### Example Session

```bash
# Create base Arch environment
$ unipac create arch-base --distro arch
Creating environment 'arch-base'...
Initializing repository at ~/.unipac/repos/arch/arch-base
✓ Environment created

# Install base tools
$ unipac install gcc make cmake git -e arch-base
Resolving dependencies...
  gcc-13.2.1
  ├─ binutils-2.41
  └─ glibc-2.38
  make-4.4.1
  cmake-3.28.1
  git-2.43.0

Downloading packages... [====================] 100%
Installing to ~/.unipac/repos/arch/arch-base...
✓ Installation complete (4 packages, 145 MB)

Committing changes...
[arch-base abc1234] Install gcc make cmake git

# Create Python 3.12 environment (multi-distro)
$ cat > unipac.yaml << EOF
environment:
  id: py312-dev
  layers:
    - id: arch-base
      distro: arch
      packages: [gcc, make, cmake]
      priority: 1
    - id: ubuntu-python
      distro: ubuntu
      release: "24.04"
      packages: [python3.12, python3.12-dev]
      priority: 2
EOF

$ unipac setup
Creating environment 'py312-dev'...
Layer 1: arch-base (Arch Linux)
  ✓ gcc-13.2.1 already installed
  ✓ make-4.4.1 already installed
  ✓ cmake-3.28.1 already installed

Layer 2: ubuntu-python (Ubuntu 24.04)
  Downloading packages...
  Installing python3.12... ✓
  Installing python3.12-dev... ✓

Validating environment...
  ✓ All dependencies resolved
  ⚠ Mixed glibc: 2.38 (arch) and 2.39 (ubuntu)
    → Forward compatible, should work fine

✓ Environment ready!

# Activate and use
$ unipac shell py312-dev
(unipac:py312-dev) $ python --version
Python 3.12.1

(unipac:py312-dev) $ which python
/home/user/.unipac/mounts/py312-dev/usr/bin/python

(unipac:py312-dev) $ gcc --version
gcc (GCC) 13.2.1

(unipac:py312-dev) $ exit

# Check history
$ unipac history py312-dev
abc1234 (HEAD -> main) Setup multi-distro environment
def5678 Install ubuntu packages: python3.12, python3.12-dev
789abcd Install arch packages: gcc, make, cmake
initial Initial environment

# Create experimental branch
$ unipac branch py312-dev test-numpy-2.0
Created branch 'test-numpy-2.0'

$ unipac checkout py312-dev test-numpy-2.0
Switched to branch 'test-numpy-2.0'

$ unipac install numpy==2.0.0b1 -e py312-dev
Installing numpy==2.0.0b1...
✓ Installed

# Test... breaks something

$ unipac checkout py312-dev main
Switched to branch 'main'
# Back to stable state immediately
```

---

## Implementation Roadmap

### Phase 1: Foundation (6-8 weeks)

**Goal:** Prove the core concept with single-distro support

**Deliverables:**

1. **FUSE filesystem (unipacfs)**
    
    - Basic path interception and redirection
    - Resolution map parsing and lookup
    - Simple LRU cache
    - Mount/unmount lifecycle
2. **Kotlin CLI skeleton**
    
    - Command parsing (using Clikt or kotlinx-cli)
    - Basic environment CRUD operations
    - gRPC client to talk to C++ engine
3. **One package manager plugin (Pacman)**
    
    - Fetch metadata
    - Install to custom prefix
    - Generate PackageIR
4. **Git integration**
    
    - Initialize repos with Git
    - Commit on package operations
    - Basic history/rollback
5. **Simple activation**
    
    - Generate shell activation scripts
    - PATH/LD_LIBRARY_PATH manipulation
    - FUSE mount on activation

**Success Criteria:**

- User can create Arch environment, install packages, activate, and use
- Rollback works correctly
- FUSE redirection proven with test binaries

### Phase 2: Multi-Distro (8-10 weeks)

**Goal:** Enable mixing packages from multiple distros

**Deliverables:**

1. **Additional PM plugins**
    
    - APT (Ubuntu/Debian)
    - DNF (Fedora/RHEL)
    - Each produces PackageIR
2. **PackageIR schema finalization**
    
    - JSON schema with validation
    - ABI compatibility metadata
    - File list with checksums
3. **Multi-layer FUSE resolution**
    
    - Priority-based lookup
    - Explicit overrides
    - Conflict detection
4. **Dependency resolver**
    
    - Cross-distro dependency resolution
    - ABI compatibility checking
    - Conflict reporting
5. **unipac.yaml support**
    
    - Parser for declarative configs
    - Multi-layer environment creation
    - Validation and error reporting

**Success Criteria:**

- Mix Arch + Ubuntu packages in one environment
- ABI conflicts detected and reported
- Applications work correctly with mixed packages

### Phase 3: Performance & Polish (6-8 weeks)

**Goal:** Production-ready performance and user experience

**Deliverables:**

1. **FUSE optimizations**
    
    - Multi-level caching
    - Inotify-based cache invalidation
    - Kernel FUSE features (writeback cache, splice)
    - Performance benchmarking
2. **Improved dependency resolution**
    
    - Smarter conflict resolution strategies
    - Suggested fixes for common conflicts
    - Dry-run mode with detailed explanations
3. **Enhanced CLI**
    
    - Rich terminal output (colors, progress bars)
    - Shell completion (bash, zsh, fish)
    - Man pages and help documentation
4. **Testing infrastructure**
    
    - Unit tests (C++: GoogleTest, Kotlin: JUnit)
    - Integration tests (real PM invocations)
    - FUSE tests (filesystem operations)
    - Performance regression tests
5. **Documentation**
    
    - User guide
    - Architecture documentation
    - Plugin development guide

**Success Criteria:**

- FUSE overhead <5% in benchmarks
- Environment activation <50ms
- Comprehensive test coverage (>80%)

### Phase 4: Advanced Features (8-12 weeks)

**Goal:** Power-user features and ecosystem growth

**Deliverables:**

1. **Application wrappers**
    
    - Desktop file generation
    - Systemd user service integration
    - Transparent app launching in environments
2. **GUI (Compose Multiplatform)**
    
    - Environment browser
    - Visual dependency graph
    - Interactive conflict resolution
    - One-click operations
3. **Sharing infrastructure**
    
    - Environment registry (Git-based)
    - Publish/pull commands
    - Verification/signing
4. **Advanced Git features**
    
    - Remotes support
    - Merge strategies for environments
    - Garbage collection for old packages
5. **Additional PM support**
    
    - Zypper (openSUSE)
    - Portage (Gentoo)
    - Nix integration (optional)

**Success Criteria:**

- Users can share environments via Git
- GUI provides intuitive environment management
- Community ecosystem starting to form

---

## Security Considerations

### Privilege Model

**Core Principle:** Unipac operates entirely in userspace by default.

1. **No root required for:**
    
    - Environment creation
    - Package installation (via fakechroot/fakeroot)
    - Activation/deactivation
    - FUSE mounts (using user namespaces or native FUSE)
2. **Optional privileged helper:**
    
    - Small, auditable setuid binary (if needed)
    - Only handles FUSE mount/unmount if kernel doesn't support unprivileged FUSE
    - Narrowly scoped, defense-in-depth

### Sandboxing

1. **Package manager isolation:**
    
    - Each PM invocation uses custom root/dbpath
    - No PM ever writes to global system paths
    - PM databases kept separate per environment
2. **FUSE filesystem isolation:**
    
    - Each environment has its own FUSE mount
    - Mounts are per-user (not system-wide)
    - Proper permission checking in FUSE callbacks
3. **Optional seccomp filtering:**
    
    - For untrusted environments, apply seccomp-bpf filters
    - Restrict syscalls to safe subset
    - User can opt-in per environment

### Package Verification

1. **Native PM verification:**
    
    - Leverage existing signature checking (pacman, apt, dnf)
    - Fail installation if signatures invalid
2. **PackageIR integrity:**
    
    - Hash all files in PackageIR
    - Verify file integrity on environment validation
3. **Plugin signing (future):**
    
    - Sign PM plugins with developer keys
    - Verify signatures before loading
    - Warn on unsigned plugins

### Attack Surface Analysis

**Potential vulnerabilities:**

1. **FUSE code bugs:** Memory corruption in C++ FUSE implementation
    
    - Mitigation: Extensive fuzzing, memory sanitizers, audits
2. **PM command injection:** If package specs aren't sanitized
    
    - Mitigation: Strict input validation, parameterized commands
3. **Symlink attacks:** Malicious packages creating symlinks
    
    - Mitigation: Validate package contents before installation
4. **Path traversal:** FUSE lookup escaping repository boundaries
    
    - Mitigation: Canonicalize all paths, check boundaries

---

## Performance Characteristics

### Expected Performance Profile

|Operation|Target|Rationale|
|---|---|---|
|Environment creation|<2s|Git init + directory creation|
|Package install (small)|~1x native PM|We invoke native PM, minimal overhead|
|Package install (large)|~1.1x native PM|Git commit adds slight overhead|
|Environment activation|<50ms|Source shell script + mount FUSE|
|FUSE cold lookup|<1ms|One cache miss + disk access|
|FUSE cached lookup|<50μs|Memory lookup only|
|Runtime overhead|<5%|FUSE adds minimal syscall overhead|
|Environment deactivation|<10ms|Unmount FUSE + clear env vars|

### Benchmarking Plan

```bash
# Performance test suite
unipac benchmark --suite all

Tests:
  1. Environment creation time
  2. Package installation overhead vs native
  3. FUSE lookup latency (cold/warm)
  4. Application runtime overhead
  5. Memory usage per environment
  6. Disk space efficiency (deduplication)

Results saved to: benchmark-results.json
```

### Optimization Strategies

**1. Lazy operations:**

- Don't rebuild FUSE resolution map on every change
- Incremental updates to caches
- Lazy loading of PackageIR metadata

**2. Parallelization:**

- Package downloads parallelized
- Dependency resolution can be parallel per layer
- Git operations can use background threads

**3. Caching:**

- PackageIR metadata cached to disk
- FUSE lookup results cached in memory
- Native PM metadata cached

**4. Deduplication:**

- Content-addressable storage for packages
- Hardlinks for identical files across environments
- Git object deduplication

---

## Testing Strategy

### Test Levels

**1. Unit Tests**

- **C++ (GoogleTest):**
    
    - FUSE path resolution logic
    - PackageIR parsing
    - Resolution map building
    - Cache implementations
- **Kotlin (JUnit 5):**
    
    - Dependency resolver
    - ABI compatibility checker
    - CLI command parsing
    - Config file parsing

**2. Integration Tests**

- Real package manager invocations
- End-to-end environment lifecycle
- Multi-distro mixing scenarios
- Git operations

**3. FUSE Tests**

- Filesystem operation correctness
- Concurrent access handling
- Error condition handling
- Performance under load

**4. Regression Tests**

- Known bug scenarios
- Performance regression detection
- Compatibility across kernel versions

### Test Environments

```yaml
# CI matrix
test_matrix:
  distros:
    - arch-latest
    - ubuntu-22.04
    - ubuntu-24.04
    - fedora-39
    - debian-12
  
  kernels:
    - 5.15  # Oldest supported
    - 6.1   # LTS
    - 6.6   # Current stable
  
  architectures:
    - x86_64
    - aarch64  # ARM support
```

### Example Integration Test

```kotlin
@Test
fun `test multi-distro environment creation and usage`() {
    // Create environment from config
    val config = """
        environment:
          id: test-mixed
          layers:
            - distro: arch
              packages: [gcc]
            - distro: ubuntu
              packages: [python3.12]
    """.trimIndent()
    
    val env = unipac.setup(config)
    
    // Verify packages installed
    assertTrue(env.hasPackage("gcc"))
    assertTrue(env.hasPackage("python3.12"))
    
    // Activate environment
    unipac.activate(env)
    
    // Run test binary
    val result = unipac.run(env, "python3 --version")
    assertEquals(0, result.exitCode)
    assertTrue(result.stdout.contains("Python 3.12"))
    
    // Check GCC works
    val gccResult = unipac.run(env, "gcc --version")
    assertEquals(0, gccResult.exitCode)
    
    // Deactivate
    unipac.deactivate()
}
```

---

## Future Directions

### Potential Extensions

**1. Container Integration**

- Export Unipac environments as OCI images
- Use Unipac inside containers for even finer control
- Hybrid: containers for heavy isolation, Unipac for development

**2. Remote Environments**

- Store environments on remote servers
- SSH-based activation (work on remote, feels local)
- Shared team environments

**3. Language-Specific Integration**

- Python: Generate requirements.txt from environment
- Rust: Cargo integration for cross-compilation
- Node: npm/yarn workspace integration

**4. Build System Integration**

- CMake toolchain files generated from environments
- Meson cross-files
- Bazel platform definitions

**5. IDE Integration**

- VS Code extension for environment management
- IntelliJ plugin
- Environment-aware debugging

**6. Nix/Guix Interop**

- Use Nix store as a layer
- Import Nix derivations into Unipac
- Best of both worlds: Nix reproducibility + traditional PM flexibility

---

## Comparison with Existing Solutions

|Feature|Unipac|Docker/Podman|Nix|Conda|Distrobox|
|---|---|---|---|---|---|
|**Multi-distro mixing**|✓|✗|✗|✗|✗|
|**Native PM support**|✓|✗|✗|✗|✓|
|**Isolation level**|Filesystem|Full container|Filesystem|Userspace|Full container|
|**Performance overhead**|<5%|10-20%|~0%|~0%|10-20%|
|**Hardcoded paths**|✓ (FUSE)|✗|✗|✗|✓|
|**Version control**|✓ (Git)|✗|✓ (built-in)|✗|✗|
|**Shareable configs**|✓|✓ (Dockerfile)|✓ (flakes)|✓ (yml)|✓|
|**Learning curve**|Medium|High|Very High|Low|Medium|
|**Privilege required**|No|Yes (rootless complex)|No|No|Yes|

**Unipac's unique value:**

- Only solution that lets you mix Arch + Ubuntu + Fedora packages in one environment
- Works with existing package managers (no new package format)
- Git-based versioning for environments
- FUSE ensures even hardcoded binaries work
- Native performance (not containerized)

---

## Conclusion

Unipac represents a pragmatic approach to solving Linux package management fragmentation. By treating distributions as composable layers, using FUSE for transparent redirection, and integrating Git for version control, it provides a powerful yet understandable tool for managing complex software environments.

The architecture balances several competing concerns:

- **Performance:** FUSE overhead minimized through caching; no container tax
- **Compatibility:** Native PMs used; works with existing packages
- **Flexibility:** Mix any distros; works with hardcoded binaries
- **Simplicity:** Git-like CLI; declarative configs; no new concepts

The phased roadmap ensures incremental value delivery while proving core concepts early. The emphasis on testing, documentation, and performance ensures production readiness.

**Next steps:**

1. Implement Phase 1 (FUSE + single-distro support)
2. Validate performance and usability
3. Gather community feedback
4. Iterate toward multi-distro support

With proper execution, Unipac could become the standard tool for managing development environments on Linux, finally solving the "works on my machine" problem in a Linux-native way.