# User Guide: Software Specifications, Configuration Options & Expected Behavior

This document serves as the formal technical manual describing the underlying data structures, hyperparameter selections, and algorithmic execution behaviors for the constraint-based well-log alignment framework.


## 📊 1. Input Data Specifications & Preprocessing

To ensure seamless execution, target subsurface profiles must strictly conform to the structural layout outlined below. 

### Spreadsheet Schema Requirements
* **File Format:** Microsoft Excel (`.xlsx`) workbooks. Data arrays must reside within the first active spreadsheet.
* **Direct Structural Indexing:** Slicing arrays map input logging curves based on explicit positional column channels:
  * **Column Index 0:** `Depth` (Continuous numeric tracking vector recorded in feet).
  * **Column Index 1:** `GR` / `GR (API)` (Gamma Ray logs recorded in standard API units).
  * **Column Index 2:** `Neutron Porosity` / `NPHI` (Neutron Porosity log channel index values).

### Automated Preprocessing
Raw geophysical measurements span completely different physical magnitudes—Gamma Ray ranges from $0\text{--}150\text{ API}$ while Neutron Porosity evaluates fractions between $0.05\text{--}0.45\text{ v/v}$. 

To counter signal imbalance, the software automatically standardizes input vectors prior to distance matrix construction utilizing a standard variance scaling approach:

$$z = \frac{x - \mu}{\sigma}$$

This guarantees both stratigraphic features exert uniform mathematical weight during path optimization regardless of their native recording units.

---

## ⚙️ 2. Tunable Hyperparameters & Software Options

Users can modify specific core control parameters directly inside the individual well-pair processing notebooks:

* **`window_percents`** (Float, range `0.0` to `1.0`): Defines the optimal Sakoe-Chiba window constraint width. This maps directly to the parameter notated as $\phi$ within the manuscript text. It is expressed as a decimal fraction of total sequence array length (e.g., setting `0.11` restricts the optimal warp path grid search computation to an 11% diagonal corridor bandwidth, enforcing geological reality by checking extreme thickness variations).

---

## 🧠 3. Expected Operational Behavior & Analytical Outputs

When a processing pipeline for a given well-pair is executed, the framework computes separate optimization pipelines for both Gamma Ray (GR) and Neutron Porosity (NPHI) logs. Each sequence follows a three-stage visual and computational workflow:

### Stage 1: Parameter Optimization via L-Curve Analysis
* **Mechanism:** The software evaluates a range of Sakoe-Chiba constraint window widths against the total cumulative alignment cost.
* **Output Graphic:** Generates an L-curve visualization displaying a distinct inflection elbow point (marking the transition into the "Stability Zone"). This automated selection identifies the mathematically optimal window percentage ($\phi$) constraint required to balance structural deformation against computational over-warping.

### Stage 2: Cumulative Cost Matrix & Warping Path Overlay
* **Mechanism:** Using the optimized window constraint ($\phi$), the software masks the out-of-bounds nodes of the distance grid with infinity ($\infty$). It then solves the absolute minimum cost path across the valid matrix space using dynamic programming.
* **Output Graphic:** Renders a high-contrast 2D heat map of the cumulative cost matrix. The calculated minimum-distance path is overlaid directly on top as a vibrant, continuous cyan line trajectory tracking from matrix coordinate $(0,0)$ to $(N,M)$.

### Stage 3: Final Stratigraphic Well-to-Well Correlation Panel
* **Mechanism:** The discrete coordinate pairings from the calculated warp path are transformed into explicit depth-to-depth tie links.
* **Output Graphic:** Renders a twin-panel depth log plot detailing the two target wells side-by-side. 
  * The log tracks are displayed alongside background color-fills mapping key stratigraphic zones.
  * Publication-ready, dark-red structural tie-lines lock corresponding horizons across the well path gap, cleanly visualizing the final structural alignment.
  * **File Formats:** All plots are automatically exported directly as sharp, standalone `.jpg` image assets inside the project folder for manuscript assembly.
