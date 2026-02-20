# FCCAnalyses Python Module — Phased Refactoring Roadmap

**Constraints driving every decision in this plan:**

- Backward compatibility is a hard requirement. Existing user scripts must continue to work unchanged throughout the entire refactor.
- Small team (1–3 people). Each phase must be completable by one person in a focused sprint, with a clean stopping point.
- Priority order: consistent interface across all stages → typed/documented configuration → testability without LXPlus.

---

## Guiding Principles

**The Strangler Fig pattern.** Every phase introduces the new structure alongside the old, with the runner detecting which style is in use and routing accordingly. The old style is never removed within this roadmap — it is deprecated with warnings and documented as legacy. Removal is a future decision with a proper deprecation window.

**Green at every commit.** No phase is complete until the existing integration tests pass and any new unit tests added in that phase are green. The module must be importable and functional after every merged PR.

**One concern per phase.** Each phase has a single, clearly named architectural concern. This keeps PRs reviewable by a small team without needing deep context across the entire codebase.

---

## Phase 0 — Foundations (Pre-work, ~1 week)

**Goal:** Establish the scaffolding that every subsequent phase depends on. No user-visible changes.

### 0.1 — Establish the test harness

Create a `tests/python/` directory in the repository. Set up `pytest` with a minimal `conftest.py` that provides two fixtures used by every subsequent phase:

```
tests/python/
├── conftest.py          # shared fixtures: mock ROOT, mock EOS catalog
├── fixtures/
│   ├── mock_proc_dict.json    # minimal process dictionary for tests
│   └── mock_analysis.py       # minimal valid Analysis class
└── unit/                # empty, populated in later phases
```

The `conftest.py` should define two key fixtures. The first is a `mock_root` autouse fixture that monkeypatches `ROOT.EnableImplicitMT`, `ROOT.RDataFrame`, and `ROOT.gSystem.Load` so that tests never require a ROOT installation. The second is a `proc_dict_path` fixture that returns the path to `mock_proc_dict.json`.

Write a single smoke test that asserts `import FCCAnalyses` succeeds and that the `fccanalysis` entry point is discoverable. This phase is complete when `pytest tests/python/` passes in a clean Python environment without ROOT.

### 0.2 — Introduce the internal package layout

Create an `FCCAnalyses/internal/` sub-package. This is where all new infrastructure will live. It is explicitly not part of the public API yet — nothing in `FCCAnalyses/__init__.py` exposes it. This prevents users from accidentally depending on in-progress interfaces before they are stable.

```
python/FCCAnalyses/
├── __init__.py          # unchanged
├── run_analysis.py      # unchanged
├── run_histmaker.py     # unchanged
├── run_final.py         # unchanged
├── run_plots.py         # unchanged
├── helpers.py           # unchanged
└── internal/
    └── __init__.py      # empty for now
```

### 0.3 — Audit and document the legacy attribute surface

Before any code changes, produce a single file `internal/legacy_attrs.py` that is the canonical record of every attribute the old module-level and `__init__`-based configuration styles accept, their types, defaults, and which runner(s) consume them. This becomes the contract that backward-compatibility tests are written against.

```python
# internal/legacy_attrs.py
# This file is the authoritative record of the legacy configuration surface.
# It is used by the compatibility shim in Phase 1 and by unit tests.

RUN_ATTRS = {
    # (legacy_name, type, default, new_name)
    "processList":   (dict,  None,    "process_list"),
    "outputDir":     (str,   None,    "output_dir"),
    "nCPUS":         (int,   4,       "n_threads"),
    "runBatch":      (bool,  False,   "run_batch"),
    "prodTag":       (str,   None,    "prod_tag"),
    "inputDir":      (str,   None,    "input_dir"),
    "procDict":      (str,   None,    "proc_dict"),
    "includePaths":  (list,  [],      "include_paths"),
    "useDataSource": (bool,  False,   "use_data_source"),
    "nEvents":       (int,   -1,      "n_events"),
}

FINAL_ATTRS = { ... }  # same treatment for final stage

PLOTS_ATTRS = { ... }  # same treatment for plots stage
```

**Exit criteria for Phase 0:** `pytest tests/python/` is green, `internal/legacy_attrs.py` exists and is complete, the existing integration tests are unchanged and passing.

---

## Phase 1 — Typed Configuration (The Core of the Refactor, ~2–3 weeks)

**Goal:** Introduce the `RunConfig`, `FinalConfig`, and `PlotConfig` dataclasses and a compatibility shim that normalises both the old and new configuration styles into the new typed objects before any runner logic runs. After this phase, all runner code works on typed objects internally even when the user script uses the old camelCase globals.

**Priority alignment:** This directly delivers "typed/documented configuration" and is the prerequisite for "consistent interface across all stages".

### 1.1 — Introduce `RunConfig`

Create `internal/config.py`. Start with `RunConfig` only:

```python
# internal/config.py
from __future__ import annotations
from dataclasses import dataclass, field
from pathlib import Path
from typing import Optional

@dataclass
class ProcessParams:
    fraction:      float = 1.0
    cross_section: Optional[float] = None
    n_generated:   Optional[int]   = None
    input_files:   list[str]       = field(default_factory=list)

@dataclass
class RunConfig:
    """
    Configuration for 'fccanalysis run'.

    All attributes have sensible defaults except process_list, which is
    required. The framework validates this object at construction time so
    errors surface before any file I/O or ROOT initialisation occurs.

    Attributes:
        process_list:    Mapping of process name to ProcessParams.
        output_dir:      Directory where output ROOT files are written.
        n_threads:       Number of ROOT implicit MT threads. -1 = all cores.
        run_batch:       If True, submit jobs to the configured batch backend.
        prod_tag:        Key4hep production tag for remote sample lookup.
        input_dir:       Override for local input file directory.
        proc_dict:       Path or name of the process dictionary JSON/YAML.
        include_paths:   List of C++ header paths to load before running.
        use_data_source: Use PODIO DataSource instead of TChain.
        n_events:        Maximum events to process. -1 = all.
    """
    process_list:    dict[str, ProcessParams]

    output_dir:      Path             = Path("./outputs/")
    n_threads:       int              = 4
    run_batch:       bool             = False
    prod_tag:        Optional[str]    = None
    input_dir:       Optional[Path]   = None
    proc_dict:       Optional[str]    = None
    include_paths:   list[str]        = field(default_factory=list)
    use_data_source: bool             = False
    n_events:        int              = -1

    def __post_init__(self):
        if not self.process_list:
            raise ValueError(
                "RunConfig.process_list must not be empty."
            )
        if self.n_threads == 0:
            raise ValueError(
                "RunConfig.n_threads must be non-zero (use -1 for all cores)."
            )
        self.output_dir = Path(self.output_dir)
        if self.input_dir is not None:
            self.input_dir = Path(self.input_dir)
```

Write unit tests immediately alongside it in `tests/python/unit/test_config.py`:

```python
def test_runconfig_requires_process_list():
    with pytest.raises(ValueError, match="process_list"):
        RunConfig(process_list={})

def test_runconfig_zero_threads_rejected():
    with pytest.raises(ValueError, match="n_threads"):
        RunConfig(process_list={"p": ProcessParams()}, n_threads=0)

def test_runconfig_output_dir_coerced_to_path():
    cfg = RunConfig(process_list={"p": ProcessParams()}, output_dir="./out")
    assert isinstance(cfg.output_dir, Path)

def test_runconfig_defaults():
    cfg = RunConfig(process_list={"p": ProcessParams()})
    assert cfg.n_threads == 4
    assert cfg.run_batch is False
    assert cfg.use_data_source is False
```

### 1.2 — Introduce `FinalConfig` and `PlotConfig`

Following the exact same pattern, add `FinalConfig` and `PlotConfig` to `internal/config.py`. These are the configs that `final` and `plots` have never had in typed form. Their fields are derived from the `FINAL_ATTRS` and `PLOTS_ATTRS` records created in Phase 0.

```python
@dataclass
class HistogramSpec:
    """Describes a single histogram: (title, n_bins, x_min, x_max)."""
    title:  str
    n_bins: int
    x_min:  float
    x_max:  float

@dataclass
class FinalConfig:
    """Configuration for 'fccanalysis final'."""
    process_list:   dict[str, ProcessParams]
    cut_list:       dict[str, str]           = field(default_factory=dict)
    histogram_list: dict[str, HistogramSpec] = field(default_factory=dict)
    input_dir:      Path                     = Path("./outputs/")
    output_dir:     Path                     = Path("./outputs/final/")
    do_tree:        bool                     = True
    lumi:           float                    = 1.0

    def __post_init__(self):
        self.input_dir  = Path(self.input_dir)
        self.output_dir = Path(self.output_dir)

@dataclass
class PlotConfig:
    """Configuration for 'fccanalysis plots'."""
    process_groups: dict[str, list[str]]     = field(default_factory=dict)
    legend_labels:  dict[str, str]           = field(default_factory=dict)
    input_dir:      Path                     = Path("./outputs/final/")
    output_dir:     Path                     = Path("./plots/")
    lumi:           float                    = 1.0
    ecm:            float                    = 240.0
    log_scale:      bool                     = False
```

### 1.3 — Write the compatibility shim

This is the most important single function in the entire refactor. It must accept the user's `Analysis` object (whether old-style globals, old-style `__init__`, or new-style class attribute) and return a typed config. The shim lives in `internal/compat.py`:

```python
# internal/compat.py
import warnings
import types
from .config import RunConfig, FinalConfig, PlotConfig, ProcessParams
from .legacy_attrs import RUN_ATTRS, FINAL_ATTRS, PLOTS_ATTRS

def _warn_legacy(attr_name: str, new_name: str):
    warnings.warn(
        f"Configuration attribute '{attr_name}' is deprecated. "
        f"Use '{new_name}' inside a RunConfig dataclass instead. "
        f"See: https://hep-fcc.github.io/FCCAnalyses/man/latest/fccanalysis-script.html",
        DeprecationWarning,
        stacklevel=3,
    )

def extract_run_config(analysis_obj) -> RunConfig:
    """
    Normalise any supported analysis configuration style into a RunConfig.

    Accepts:
      1. New style: analysis_obj has a 'run_config' class attribute of type RunConfig
      2. New-ish style: analysis_obj.__init__ sets self.process_list, self.n_threads, ...
      3. Old style: the analysis module has processList, nCPUS, ... at module level
    """
    # Style 1: already a RunConfig
    if hasattr(analysis_obj, 'run_config') and isinstance(analysis_obj.run_config, RunConfig):
        return analysis_obj.run_config

    # Style 2 & 3: read attributes, emit deprecation warnings for camelCase names
    kwargs = {}
    for legacy_name, (typ, default, new_name) in RUN_ATTRS.items():
        if hasattr(analysis_obj, legacy_name):
            _warn_legacy(legacy_name, new_name)
            kwargs[new_name] = getattr(analysis_obj, legacy_name)
        elif hasattr(analysis_obj, new_name):
            kwargs[new_name] = getattr(analysis_obj, new_name)

    # Coerce process_list values to ProcessParams if they are raw dicts
    if 'process_list' in kwargs:
        coerced = {}
        for name, params in kwargs['process_list'].items():
            if isinstance(params, dict):
                coerced[name] = ProcessParams(**{
                    k: v for k, v in params.items()
                    if k in ProcessParams.__dataclass_fields__
                })
            else:
                coerced[name] = params
        kwargs['process_list'] = coerced

    return RunConfig(**kwargs)
```

Write compatibility tests that confirm no warnings are emitted for new-style scripts and that `DeprecationWarning` is emitted for every camelCase attribute:

```python
def test_new_style_no_warning(new_style_analysis):
    with warnings.catch_warnings(record=True) as w:
        warnings.simplefilter("always")
        cfg = extract_run_config(new_style_analysis)
    assert not any(issubclass(x.category, DeprecationWarning) for x in w)

def test_old_style_emits_deprecation(old_style_analysis):
    with warnings.catch_warnings(record=True) as w:
        warnings.simplefilter("always")
        cfg = extract_run_config(old_style_analysis)
    deprecated = [x for x in w if issubclass(x.category, DeprecationWarning)]
    assert len(deprecated) > 0

def test_old_style_produces_identical_config(old_style_analysis, new_style_analysis):
    old_cfg = extract_run_config(old_style_analysis)
    new_cfg = extract_run_config(new_style_analysis)
    assert old_cfg.process_list == new_cfg.process_list
    assert old_cfg.n_threads    == new_cfg.n_threads
```

### 1.4 — Thread the shim into the runners

In each runner file, add a single line at the top of the `run()` function that converts whatever the user gave into a typed config. The rest of each runner continues to use its existing attribute access for now — the shim makes it seamless:

```python
# In run_analysis.py — add this at the top of the main run function
from FCCAnalyses.internal.compat import extract_run_config

def run(args):
    analysis = _load_script(args.script)
    cfg = extract_run_config(analysis)   # ← this is the only new line

    # Everything below this line accesses cfg.n_threads, cfg.output_dir, etc.
    # instead of analysis.nCPUS, analysis.outputDir, etc.
    # Replace attribute accesses one by one in this phase.
    ...
```

This is the wedge that separates the framework-internal code from the user-facing interface permanently. From this point forward, runner code never reads user script attributes directly.

**Exit criteria for Phase 1:** All three config dataclasses exist and are documented. The shim handles all three configuration styles. Deprecation warnings are emitted for legacy attributes. Existing integration tests pass without modification. The `tests/python/unit/test_config.py` and `test_compat.py` suites are green without ROOT.

---

## Phase 2 — Service Extraction (DatasetManager, LibraryLoader, ~2 weeks)

**Goal:** Pull the two most duplicated concerns — file resolution and library loading — out of the runners and into standalone, independently testable service classes. The runners become thin coordinators that call services rather than doing the work themselves.

**Priority alignment:** This is the prerequisite for testability, since the file resolution and library loading code is the part that currently requires a live CVMFS/EOS mount and a ROOT installation to test at all.

### 2.1 — `DatasetManager`

Create `internal/dataset.py`. Extract all file-discovery logic from the runners:

```python
# internal/dataset.py
from __future__ import annotations
import json
from pathlib import Path
from typing import Protocol
from .config import RunConfig, ProcessParams

class CatalogProvider(Protocol):
    """Anything that can resolve a process name to a list of file paths."""
    def get_files(self, process_name: str, prod_tag: str) -> list[str]: ...
    def get_cross_section(self, process_name: str) -> float: ...
    def get_n_generated(self, process_name: str) -> int: ...

class JsonCatalogProvider:
    """Reads the standard FCCAnalyses process dictionary JSON files."""
    def __init__(self, json_path: str | Path):
        with open(json_path) as f:
            self._data = json.load(f)

    def get_files(self, process_name: str, prod_tag: str) -> list[str]:
        entry = self._data.get(process_name, {})
        base  = entry.get("path", "")
        files = entry.get("files", [])
        return [str(Path(base) / f) for f in files]

    def get_cross_section(self, process_name: str) -> float:
        return self._data.get(process_name, {}).get("crossSection", 1.0)

    def get_n_generated(self, process_name: str) -> int:
        return self._data.get(process_name, {}).get("nEvents", -1)

class DatasetManager:
    def __init__(self, config: RunConfig, catalog: CatalogProvider | None = None):
        self._cfg     = config
        self._catalog = catalog or self._build_catalog()

    def _build_catalog(self) -> CatalogProvider:
        if self._cfg.proc_dict:
            return JsonCatalogProvider(self._cfg.proc_dict)
        # Fall back to CVMFS lookup — same logic as today, just centralised
        ...

    def resolve(self, process_name: str) -> list[Path]:
        """Return the list of input ROOT files for a given process."""
        if self._cfg.input_dir:
            return sorted(self._cfg.input_dir.glob(f"{process_name}*.root"))
        raw = self._catalog.get_files(process_name, self._cfg.prod_tag or "")
        fraction = self._cfg.process_list[process_name].fraction
        n = max(1, int(len(raw) * fraction))
        return [Path(f) for f in raw[:n]]
```

The `CatalogProvider` protocol is the key design decision here. It means the `DatasetManager` can be tested with a simple in-memory mock catalog, and future providers (iLCDirac, DIRAC, a local SQLite cache) can be added without touching the manager:

```python
# In tests:
class MockCatalog:
    def get_files(self, name, tag):
        return [f"/fake/path/{name}_0.root", f"/fake/path/{name}_1.root"]
    def get_cross_section(self, name): return 0.5
    def get_n_generated(self, name):   return 10000

def test_resolve_respects_fraction():
    cfg     = RunConfig(process_list={"sig": ProcessParams(fraction=0.5)})
    manager = DatasetManager(cfg, catalog=MockCatalog())
    files   = manager.resolve("sig")
    assert len(files) == 1   # 50% of 2 = 1
```

### 2.2 — `LibraryLoader`

Create `internal/loader.py`. This class owns the sequence of ROOT interactions needed before the dataframe is built. Its interface is intentionally narrow:

```python
# internal/loader.py
from __future__ import annotations
from pathlib import Path

class LibraryLoader:
    """
    Manages loading of C++ analyzer libraries into ROOT's interpreter.

    Tracks which headers and libraries have already been loaded to
    prevent duplicate declarations.
    """
    def __init__(self, root_module=None):
        # Accept ROOT as a parameter so tests can inject a mock
        self._ROOT      = root_module or _import_root()
        self._loaded    = set()

    def load_shared_lib(self, lib_name: str) -> None:
        if lib_name in self._loaded:
            return
        ret = self._ROOT.gSystem.Load(lib_name)
        if ret < 0:
            raise RuntimeError(f"Failed to load shared library: {lib_name}")
        self._loaded.add(lib_name)

    def declare_header(self, header_path: str | Path) -> None:
        key = str(header_path)
        if key in self._loaded:
            return
        self._ROOT.gInterpreter.Declare(f'#include "{header_path}"')
        self._loaded.add(key)

    def declare_inline(self, cpp_code: str) -> None:
        self._ROOT.gInterpreter.Declare(cpp_code)

    def load_from_config(self, config) -> None:
        """Load all headers and libs declared in a RunConfig."""
        for path in config.include_paths:
            self.declare_header(path)
```

Because `ROOT` is injected rather than imported at module level, tests can pass a mock:

```python
class MockROOT:
    class gSystem:
        @staticmethod
        def Load(name): return 0
    class gInterpreter:
        declared = []
        @classmethod
        def Declare(cls, code): cls.declared.append(code)

def test_declare_header_deduplication():
    loader = LibraryLoader(root_module=MockROOT)
    loader.declare_header("functions.h")
    loader.declare_header("functions.h")   # second call should be a no-op
    assert MockROOT.gInterpreter.declared.count('#include "functions.h"') == 1
```

### 2.3 — Wire services into all runners

Replace the inlined file-resolution and library-loading code in each runner with calls to `DatasetManager` and `LibraryLoader`. The runners shrink to roughly: load config → create services → call services → run dataframe → write outputs.

**Exit criteria for Phase 2:** `DatasetManager` and `LibraryLoader` exist in `internal/`. The runners use them exclusively. Unit tests for both services pass without ROOT or CVMFS. The existing integration tests pass unchanged.

---

## Phase 3 — `BaseRunner` and Runner Unification (~2 weeks)

**Goal:** Eliminate the code duplication across runner files by introducing a `BaseRunner` abstract class. This phase is purely internal — users see no interface change.

### 3.1 — Define `BaseRunner`

Create `internal/base_runner.py`:

```python
# internal/base_runner.py
from __future__ import annotations
from abc import ABC, abstractmethod
import logging
from .compat   import extract_run_config
from .dataset  import DatasetManager
from .loader   import LibraryLoader

logger = logging.getLogger(__name__)

class BaseRunner(ABC):
    """
    Abstract base for all FCCAnalyses runners.

    Concrete runners override _execute() only. All other steps —
    config extraction, input resolution, ROOT setup, library loading —
    are handled here and are identical across all stages.
    """
    def __init__(self, analysis_obj, cli_args):
        self._analysis = analysis_obj
        self._cli_args = cli_args
        self._config   = self._extract_config()

    @abstractmethod
    def _extract_config(self):
        """Return the stage-appropriate typed config object."""
        ...

    @abstractmethod
    def _execute(self, input_map: dict[str, list]) -> None:
        """Perform the stage-specific computation."""
        ...

    def run(self) -> None:
        logger.info("Starting %s", self.__class__.__name__)
        self._validate()
        input_map = self._resolve_inputs()
        self._setup_root()
        self._load_libraries()
        self._execute(input_map)
        logger.info("Finished %s", self.__class__.__name__)

    def _validate(self) -> None:
        # RunConfig.__post_init__ already validated at construction.
        # Additional cross-field validations go here.
        cfg = self._config
        if cfg.run_batch and cfg.input_dir is None and cfg.prod_tag is None:
            raise ValueError(
                "Batch submission requires either 'input_dir' or 'prod_tag'."
            )

    def _resolve_inputs(self) -> dict[str, list]:
        manager = DatasetManager(self._config)
        return {
            name: manager.resolve(name)
            for name in self._config.process_list
        }

    def _setup_root(self) -> None:
        import ROOT
        if self._config.n_threads == -1:
            ROOT.EnableImplicitMT()
        elif self._config.n_threads > 1:
            ROOT.EnableImplicitMT(self._config.n_threads)

    def _load_libraries(self) -> None:
        loader = LibraryLoader()
        loader.load_from_config(self._config)
```

### 3.2 — Implement concrete runners

Each runner file is reduced to a class that inherits from `BaseRunner` and implements only `_extract_config` and `_execute`:

```python
# run_analysis.py
from FCCAnalyses.internal.base_runner import BaseRunner
from FCCAnalyses.internal.compat      import extract_run_config

class StagedRunner(BaseRunner):
    def _extract_config(self):
        return extract_run_config(self._analysis)

    def _execute(self, input_map):
        import ROOT
        for process_name, files in input_map.items():
            chain = ROOT.TChain("events")
            for f in files:
                chain.Add(str(f))
            df    = ROOT.RDataFrame(chain)
            df2   = self._analysis.analyzers(df)
            cols  = self._analysis.output()
            out   = self._config.output_dir / f"{process_name}.root"
            df2.Snapshot("events", str(out), cols)

# The old module-level run() function remains as a thin wrapper for CLI compat:
def run(args):
    analysis = _load_script(args.script)
    StagedRunner(analysis, args).run()
```

The same pattern applies to `HistmakerRunner`, `FinalRunner`, and `PlotsRunner`. The key result is that the shared logic (steps 1–4 from the analysis) now lives in exactly one place.

**Exit criteria for Phase 3:** `BaseRunner` exists. All four runner files use it. The shared logic (input resolution, ROOT setup, library loading) is not duplicated anywhere. Integration tests pass.

---

## Phase 4 — Consistent Interface for `final` and `plots` (~1.5 weeks)

**Goal:** Complete the migration started for `run` by making `final` and `plots` class-based. This is the phase that delivers "consistent interface across all stages" as a user-visible improvement.

### 4.1 — Document the new `Analysis` contract

Before writing code, draft the new full `Analysis` class contract as a docstring in `internal/protocol.py`. This is a `Protocol` class in the `typing` sense — it documents what the framework expects, without forcing users to inherit from it:

```python
# internal/protocol.py
from typing import Protocol, runtime_checkable
from .config import RunConfig, FinalConfig, PlotConfig

@runtime_checkable
class AnalysisProtocol(Protocol):
    """
    The complete contract for an FCCAnalyses analysis class.

    Users do not inherit from this class. It exists to document the
    interface and to allow isinstance() checks in the runners.

    Only run_config + analyzers + output are required.
    final_config and plot_config are optional; omitting them means
    those stages cannot be run from this script.
    """
    run_config:   RunConfig
    final_config: FinalConfig   # optional
    plot_config:  PlotConfig    # optional

    def analyzers(self, dframe): ...
    def output(self) -> list[str]: ...
    def final_analyzers(self, dframe): ...  # optional
```

### 4.2 — Update `FinalRunner` and `PlotsRunner`

Implement `extract_final_config` and `extract_plot_config` in `compat.py`, following the exact same pattern as `extract_run_config`. These functions must handle both the legacy module-level globals style and the new `final_config` / `plot_config` class attributes.

The migration means a user who today writes:

```python
# Old final script (still works, emits DeprecationWarning)
processList = {"sig": {"fraction": 1}}
cutList  = {"baseline": "n_muons >= 2"}
histList = {"zmumu_m": ("m_{Z} [GeV]", 100, 50, 150)}
outputDir = "./outputs/final/"
```

Can now write (same file, new style):

```python
# New style — all stages in one file
class Analysis:
    run_config = RunConfig(
        process_list={"sig": ProcessParams(fraction=1.0)},
        output_dir="./outputs/stage1/",
    )
    final_config = FinalConfig(
        process_list={"sig": ProcessParams(fraction=1.0)},
        cut_list={"baseline": "n_muons >= 2"},
        histogram_list={"zmumu_m": HistogramSpec("m_Z [GeV]", 100, 50, 150)},
        output_dir="./outputs/final/",
    )

    def analyzers(self, df): ...
    def output(self): ...
```

This is the moment the "consistent interface" goal is fully realised: one file, one class, all stages, all typed.

**Exit criteria for Phase 4:** All three stages (`run`, `final`, `plots`) accept the class-based interface. Old module-level globals still work with deprecation warnings. Unit tests verify both paths for all three stages.

---

## Phase 5 — Public API and Documentation (~1 week)

**Goal:** Graduate the `internal/` interfaces to the public API and produce the documentation that makes the new interface discoverable.

### 5.1 — Promote to public API

Update `FCCAnalyses/__init__.py` to export the types users need:

```python
# FCCAnalyses/__init__.py
from .internal.config import (
    RunConfig,
    FinalConfig,
    PlotConfig,
    ProcessParams,
    HistogramSpec,
)
from .internal.dataset import DatasetManager
from .internal.protocol import AnalysisProtocol

__all__ = [
    "RunConfig", "FinalConfig", "PlotConfig",
    "ProcessParams", "HistogramSpec",
    "DatasetManager", "AnalysisProtocol",
]
```

### 5.2 — Update the man pages and website

The `fccanalysis-script(7)` man page should be regenerated to document the new class-based interface as the primary style, with the legacy style documented in a "Legacy / Backward Compatibility" section. Every attribute of every config dataclass should appear in the man page with its type, default, and a one-sentence description — these can be auto-generated from the dataclass docstrings.

### 5.3 — Migration guide

Publish a `MIGRATION.md` at the root of the repository that shows the before/after for each configuration style change. This is the document you point existing users to.

**Exit criteria for Phase 5:** `from FCCAnalyses import RunConfig` works. Man pages are updated. `MIGRATION.md` is merged.

---

## Parallel Track — Testability (runs alongside Phases 1–5)

Testability is not a phase with a single delivery — it grows incrementally. After each phase, the following tests should be added:

|After Phase|New tests to add|
|---|---|
|0|Smoke test: `import FCCAnalyses` succeeds|
|1|Config validation: required fields, type coercion, deprecation warnings|
|2|`DatasetManager.resolve()` with mock catalog; `LibraryLoader` deduplication|
|3|`BaseRunner` lifecycle: validate → resolve → setup → execute order|
|4|`extract_final_config` and `extract_plot_config` compatibility|
|5|Public API import test: all exported names are importable|

The goal by the end of Phase 5 is a `pytest` suite that runs in under 30 seconds on a laptop with no ROOT, no CVMFS, and no LXPlus, and that covers all configuration logic, the compatibility shim, and the service classes.

---

## Sequencing Summary

```
Week  1–2    Phase 0  — Test harness, internal/ package, legacy attribute audit
Week  3–5    Phase 1  — RunConfig, FinalConfig, PlotConfig + compatibility shim
Week  6–7    Phase 2  — DatasetManager, LibraryLoader (fully unit-testable)
Week  8–9    Phase 3  — BaseRunner + runner unification
Week 10–11   Phase 4  — final/plots class-based interface (user-visible)
Week 12      Phase 5  — Public API, man pages, migration guide

Throughout   Tests    — Grow the pytest suite after every phase
```

The most important property of this schedule is that **Phases 0–3 are entirely invisible to users**. Only Phase 4 changes what users can write (while keeping the old style working). This means the first 9–10 weeks of work carry zero risk of breaking anyone.

---

## What Deliberately Stays Out of Scope

The following items from the broader roadmap are intentionally deferred. They depend on the infrastructure built in Phases 1–5 but are independent enough to be handled separately, and including them here would make individual phases too large for a small team:

- **Pluggable batch backends** (Slurm, GRID). The `BatchBackend` protocol belongs after `BaseRunner` exists (Phase 3 completes), but is a separate PR.
- **Programmatic `import FCCAnalyses` API** for Jupyter/SWAN. Depends on `DatasetManager` and the public API work in Phase 5.
- **`mplhep` plotting integration**. Depends on `PlotConfig` being in place (Phase 4), but plotting is a large enough domain to be its own subsequent effort.
- **C++ string helper wrappers** (`sel_pt(10.0)("muons")`, etc.). Orthogonal to the structural work here; can be contributed incrementally.
- **Named `cutflow()` context manager**. Orthogonal; can be added to `BaseRunner` after Phase 3.