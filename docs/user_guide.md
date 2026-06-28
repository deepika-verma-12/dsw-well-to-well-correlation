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
Raw geophysical measurements are automatically standardized prior to distance matrix construction using standard variance scaling:

$$z = \frac{x - \mu}{\sigma}$$

This balances numeric scales across different logging channels (e.g., Gamma Ray and Neutron Porosity) to ensure uniform mathematical weight during path optimization.

---

## ⚙️ 2. Tunable Hyperparameters & Software Options

* **`window_percents`** (Float, range `0.0` to `1.0`): Specifies the Sakoe-Chiba window constraint width, corresponding to the parameter $\phi$ in the manuscript text. It is expressed as a decimal representation of a percentage of the total sequence length, restricting the warping path grid search computation to a diagonal corridor bandwidth to limit extreme thickness variations.


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
