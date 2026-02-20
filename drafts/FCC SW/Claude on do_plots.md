Now let me fetch the GitHub issue to understand the requested functionalities:Now I have a thorough understanding of both the code and the issue. Let me compose a comprehensive response.

---

## 1. Analysis of `do_plots.py`

**Overall structure:** The file is a single ~1162-line procedural Python script with no class hierarchy. It acts as both a library and a CLI entry point, mixing configuration loading, histogram management, rendering logic, and output in a flat sequence of top-level functions. Here is a breakdown of what each part does and where the pain points are.

**Functional blocks (what exists):**

- `removekey` / `sorted_dict_values` — small dict/list utilities, fine as standalone helpers.
- `formatStatUncHist` — builds a hatched uncertainty histogram from a list; works but has no guard for empty input and is only called in one context.
- `get_minmax_range` — scans histogram bins to find y-axis limits; the range logic has a subtle bug: the `or` in the bin-edge condition (`> xmin or < xmax`) should be `and`, otherwise every bin passes.
- `determine_lumi_scaling` — reads TFile metadata to decide the luminosity scale factor; calls `sys.exit` on error, which prevents any recovery or testing.
- `load_hists` / `mapHistosFromHistmaker` — parallel implementations of the same operation (loading and scaling histograms) for two analysis modes (staged vs. histmaker). The code is almost identical — file discovery, `deepcopy`, scale, rebin, accumulate — repeated twice.
- `runPlots` / `runPlotsHistmaker` — again two near-identical orchestrators that build legends, collect yields, and call `draw_plot`. Legend construction, yield collection, and color assembly are copy-pasted verbatim.
- `draw_plot` — the monolithic 300-line rendering function. It handles: canvas setup, axis labeling (including special cutflow logic), background/signal stacking, stat-uncertainty overlays, x/y range determination (with duplicated logic for stack vs. nostack), all the TLatex annotation layers, and a completely different branch for the `AAAyields` summary page — all in one function body.
- `save_canvas` — clean and minimal, this is a good function.
- `run` — configuration loader via `importlib`, handles both analysis types, iterates over variables/selections.
- `do_plots` — thin CLI entry point.

**Key structural problems:**

- **Massive code duplication.** `load_hists` and `mapHistosFromHistmaker` share ~90% of logic; `runPlots` and `runPlotsHistmaker` share ~85%. Any new feature (e.g., overflow handling, normalization) must be implemented twice and kept in sync.
- **`draw_plot` is a God function.** It does canvas management, axis logic, stacking, stat uncertainty, _and_ yields-page rendering. Adding a ratio panel, for instance, requires deep surgery inside this one function.
- **Configuration is a raw dict passed everywhere.** There's no schema or type safety; config keys are string literals scattered across 15+ call sites, making refactoring fragile.
- **Two-mode divergence at the top level.** The staged vs. histmaker split happens by `if config['ana-type'] == 'histmaker': sys.exit()`, causing the two flows to share no code despite being very similar.
- **`sys.exit` inside library functions.** `determine_lumi_scaling` and `load_hists` call `sys.exit`, making them impossible to unit-test or call from a higher-level orchestrator.
- **`AAAyields` is a string-hack.** The yields summary plot is triggered by checking whether `'AAAyields'` is in the variable name — a naming convention used as a feature flag, with duplicated TLatex rendering code inside an `if` branch of `draw_plot`.
- **Mixed naming conventions.** `camelCase` (`scaleSig`, `intLumi`, `plotStatUnc`) from the user script API, `snake_case` in internal functions, and hyphenated-key dicts (`config['int-lumi']`) are all mixed together.
- **Hardcoded collider strings.** `if 'ee' in script_module.collider` is the sole way to detect FCC-ee vs. FCC-hh, with no enum or registry.
- **Legend construction duplicated.** The same ~15 lines of `TLegend` setup appear in both `runPlots` and `runPlotsHistmaker`.

---

## 2. How to Enhance the Structure

The key architectural move is to replace the procedural soup with a small class hierarchy that separates concerns cleanly. Here's a concrete proposal:

**`PlotConfig` dataclass** — a typed, validated container for all the configuration that is currently a raw `dict`. Every key becomes an attribute with a type annotation and a default. It is constructed once in `run()` and passed around by reference. This eliminates string-literal key access and makes IDE completion and static analysis work.

```python
@dataclass
class PlotConfig:
    input_dir: Path
    output_dir: Path
    int_lumi: float = 1.0
    do_scale: bool = False
    scale_sig: float = 1.0
    scale_bkg: float = 1.0
    stack_sig: list[str] = field(default_factory=lambda: ['stack'])
    x_axis_scales: list[str] = field(default_factory=lambda: ['lin'])
    y_axis_scales: list[str] = field(default_factory=lambda: ['lin'])
    formats: list[str] = field(default_factory=lambda: ['png', 'pdf'])
    plot_stat_unc: bool = False
    normalize: bool = False          # new: unit-area normalization
    add_overflow: bool = False        # new: merge overflow into last bin
    ratio_panel: str | None = None   # new: 'sig/bkg', 'data/bkg', etc.
    split_leg: bool = False
    leg_position: list[float | None] = field(default_factory=lambda: [None]*4)
    legend_text_size: float = 0.035
    collider: str = 'ee'
    energy: float = 240.0
    ...
```

**`HistogramLoader` class** — unifies `load_hists` and `mapHistosFromHistmaker` into one class with a common interface. Both analysis modes produce the same output (`dict[str, list[TH1]]` for signal and backgrounds); only the file naming pattern and the scale-determination path differ. These become two `classmethod` constructors or a strategy parameter.

```python
class HistogramLoader:
    def load(self, proc_name, file_stems, config) -> ROOT.TH1: ...
    def apply_overflow(self, hist): ...     # new
    def normalize(self, hist): ...          # new
    @classmethod
    def from_staged(cls, config): ...
    @classmethod
    def from_histmaker(cls, param): ...
```

**`LegendBuilder` class** — the ~30 lines of TLegend construction that are copy-pasted in both run functions become one reusable object:

```python
class LegendBuilder:
    def build(self, hsignal, hbackgrounds, config, legend_map) -> tuple[TLegend, TLegend | None]: ...
```

**`PlotDrawer` class** — replaces `draw_plot`. Instead of a 300-line function, this becomes a class with clear sub-methods. Crucially, it can support an optional ratio pad as a first-class feature:

```python
class PlotDrawer:
    def __init__(self, config: PlotConfig): ...
    def setup_canvas(self, name, with_ratio=False): ...   # TPad split if ratio
    def draw_stacks(self, pad, histos, nsig, nbkg, plot_params): ...
    def draw_stat_unc(self, pad, stack): ...
    def draw_labels(self, pad, lt, rt, ana_tex, extralab, custom): ...
    def draw_ratio(self, ratio_pad, hsignal, hbackgrounds, plot_params): ...  # new
    def draw_yields_page(self, yields, config): ...        # extracted from draw_plot
    def save(self, canvas, name): ...
```

**`RatioPanel` class** — a dedicated, extensible abstraction for the ratio pad:

```python
class RatioPanel:
    MODES = {'sig/bkg', 'data/mc', 'sig/sqrt(bkg)', 'custom'}
    def compute(self, numerator_hists, denominator_hists, mode) -> ROOT.TH1: ...
    def draw(self, pad, ratio_hist, ref_line=1.0): ...
```

**`YieldsTable` class** — the text yield table printed to file currently uses `sys.stdout` redirection and raw string formatting. This should be a proper class supporting multiple output formats:

```python
class YieldsTable:
    def compute(self, hsignal, hbackgrounds, cuts=None): ...
    def to_text(self, path): ...
    def to_latex(self, path): ...    # new
    def to_csv(self, path): ...      # new
```

**`ColliderProfile` registry** — instead of `if 'ee' in collider`, a small registry maps collider identifiers to their display strings, energy units, and default lumi labels:

```python
COLLIDER_PROFILES = {
    'ee': ColliderProfile(label='FCC-ee Simulation (Delphes)', energy_unit='GeV'),
    'hh': ColliderProfile(label='FCC-hh Simulation (Delphes)', energy_unit='TeV'),
}
```

**Module layout** — rather than a 1162-line monolith, the module should be split into:

```
python/FCCAnalyses/plot/
    __init__.py          # public API: do_plots(), PlotConfig
    config.py            # PlotConfig dataclass + loader
    loader.py            # HistogramLoader
    drawer.py            # PlotDrawer, RatioPanel
    legend.py            # LegendBuilder
    yields.py            # YieldsTable
    colliders.py         # ColliderProfile registry
    utils.py             # get_minmax_range, formatStatUncHist, etc.
```

---

## 3. What a Rich Plotting Module Should Have for FCCAnalyses

Going beyond what the issue requests, a mature HEP plotting module in FCCAnalyses should include the following:

**Core rendering features (directly in scope of the issue):**

- Unit-area normalization mode, individually configurable per plot or globally.
- Overflow-into-last-bin merging, configurable per histogram.
- Ratio panel as a first-class feature: signal/background, data/MC, significance `S/√B` as a function of cut, with configurable reference line, y-axis range, and axis title.
- Data points with Poisson error bars (for unblinding / data overlay workflows).

**Histogram manipulation:**

- Per-process rebinning (not just a global rebin factor).
- Variable-width bin support (important for distributions with very different density regions).
- Symmetric/asymmetric error band propagation when combining multiple files.
- Optional underflow display alongside overflow.

**Styling and layout:**

- A `PlotStyle` profile system: `FCCee_default`, `FCChh_default`, `publication`, `internal`, mapping to font sizes, pad margins, color palettes, and label conventions. This avoids hardcoded `0.04`, `0.035`, `0.14`, `0.08` etc. scattered throughout `draw_plot`.
- CMS/ATLAS-style color palette presets in addition to the current arbitrary user-defined color maps.
- Configurable canvas aspect ratio (currently hardcoded `800x800`).
- Support for 2D histograms (TH2), which are currently entirely absent.

**Statistical features:**

- Systematic uncertainty bands (not just statistical), rendered as a differently-hatched band that can be set from external inputs.
- Signal significance `S/√(S+B)` or `S/√B` overlay or secondary y-axis.
- Automatic Chi² or KS test display between distributions when in comparison mode.

**Output and reporting:**

- LaTeX yield tables (`.tex` fragment ready for inclusion in papers) alongside the current plain-text format.
- CSV yield tables for spreadsheet consumption.
- A plot index HTML page auto-generated alongside the output images (like many ATLAS/CMS tools produce), making it easy to browse many plots.
- JSON sidecar files containing plot metadata (luminosity, scale factors, bin contents) for reproducibility.

**Usability and developer experience:**

- A `--dry-run` flag that validates all config and input files without rendering anything.
- A `--list-plots` flag that prints which plots would be produced.
- Per-plot configuration overrides inside the `plots` dict (e.g., a specific plot can override the global `logy` or `rebin` without touching the global config).
- Parallel plot rendering (`multiprocessing.Pool` or `concurrent.futures`) for large analysis configurations.
- Proper unit tests via `pytest` with small synthetic ROOT files, decoupled from `sys.exit`.

---

## 4. Draft GitHub Issue Response

Here is a well-structured comment you can post directly on issue #420:The analysis above covers the four parts you asked for. Let me pull everything together clearly.

---

## Summary

### 1. File Analysis

The 1162-line script is organized into roughly six functional zones: utilities, histogram loading (two parallel implementations), two run orchestrators, one monolithic draw function, and a CLI entry point. The most significant problems are:

- **~90% code duplication** between `load_hists`/`mapHistosFromHistmaker` and between `runPlots`/`runPlotsHistmaker` — adding the three issue features requires touching all four functions simultaneously.
- **`draw_plot` is a 300-line God function** mixing canvas setup, axis ranging, stacking logic, stat uncertainty, all TLatex annotations, and the `AAAyields` summary page in one body. The ratio panel cannot be added cleanly here without deep surgery.
- **A subtle range-logic bug** in `get_minmax_range` where `or` should be `and` in the bin-edge check.
- **`sys.exit` inside library functions** making them untestable.
- **Mixed naming conventions** (`camelCase` user API, `snake_case` internals, hyphenated dict keys) and hardcoded collider detection via string matching.
- **`AAAyields` as a naming hack** used as a feature flag, with a duplicate rendering branch inside `draw_plot`.

### 2. Structural Enhancement

The key moves are: a typed `PlotConfig` dataclass replacing the raw `dict`; a unified `HistogramLoader` class eliminating the staged/histmaker duplication; decomposing `draw_plot` into a `PlotDrawer` class with clear sub-methods; a dedicated `RatioPanel` class for computed ratio distributions; a `YieldsTable` class supporting text/LaTeX/CSV output; a `ColliderProfile` registry; and splitting the monolith into a `python/FCCAnalyses/plot/` subpackage. All of this keeps the public user-script API 100% unchanged.

### 3. What a Rich Plotting Module Should Have

Beyond the three requested features, a mature module should include: data-overlay with Poisson error bars; systematic uncertainty bands; per-plot config overrides; 2D histogram support; significance overlays (S/√B); configurable plot style profiles for internal vs. publication use; auto-generated HTML browsing pages for output; JSON sidecar metadata; parallel rendering via `--jobs N`; and a `--dry-run` validation mode. The yields infrastructure should emit LaTeX-ready table fragments and CSV in addition to plain text.

### 4. Issue Response

The draft GitHub comment above (ready to copy-paste) explains the approach at the right level of detail for collaborators: it acknowledges the issue, identifies the structural problems, describes the refactoring plan with concrete class names, lists all new features with backward-compatibility guarantees, and proposes a staged PR strategy (refactor-first, features-second) to keep the diff reviewable.