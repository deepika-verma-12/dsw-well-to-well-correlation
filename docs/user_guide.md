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

## 🧠 3. Expected Operational Behavior & Outputs

When a well-pair notebook is executed, the pipeline processes both Gamma Ray (GR) and Neutron Porosity (NPHI) logs through three sequential visual stages:

### Stage 1: L-Curve Parameter Optimization
* **What it does:** Plots Sakoe-Chiba window constraint percentages against cumulative alignment cost.
* **Output:** An L-curve graph revealing a clear inflection "elbow" to identify the optimal window value ($\phi$).

### Stage 2: Cumulative Cost Matrix Overlay
* **What it does:** Generates a 2D distance grid masked by the optimized window constraint ($\phi$).
* **Output:** A cumulative cost matrix heatmap featuring the optimal minimum-cost warping path plotted on top as a continuous trajectory line.

### Stage 3: Final Well-to-Well Correlation Panel
* **What it does:** Translates the computed warping path coordinates into explicit depth-to-depth tie lines.
* **Output:** A twin-panel log plot mapping the wells side-by-side with background stratigraphic zone color-fills connected by clean, dark-red correlation lines. Figures save automatically as `.jpg` files.
