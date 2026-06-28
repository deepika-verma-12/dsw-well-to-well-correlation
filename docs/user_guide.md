# User Guide: Inputs, Outputs, and Tunable Options

This guide describes the data file schemas, configuration options, and expected operational behaviors for replicating the well-log correlation framework.

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

When a well-pair processing notebook is executed, the pipeline steps through three key visual optimization and alignment stages:

### Stage 1: Sakoe-Chiba Window Optimization
* **Description:** Optimization of the Sakoe-Chiba (SC) window parameter shown in the form of an L-curve to identify the optimal SC Parameter value ($\phi$).

### Stage 2: Constrained Warping Path trajectories
* **Description:** The minimum-cost warping path trajectory overlaid on the cumulative cost matrix, dynamically constrained within the optimal Sakoe-Chiba window SC parameter.

### Stage 3: Lithological Well Panel Alignments
* **Description:** Final visual well-to-well correlation panel displaying the target logs side-by-side with background stratigraphic zone color-fills connected by clear, explicit correlation paths between the aligned lithologies. Output graphics save automatically as `.jpg` images.
