# User Guide: Data Structures, Hyperparameters, and Expected Behavior

This document serves as the formal technical specification manual for the constraint-based DTW stratigraphic alignment software.

---

## 1. Input Data Specifications & Preprocessing

Custom user datasets must strictly match the array-slicing architecture defined below:
* **File Format:** Microsoft Excel (`.xlsx`) workbooks. The data arrays must be located on the first active spreadsheet.
* **Structural Column Mapping:** Tracking paths pull data via direct positional index locations:
  * **Index 0:** `Depth` (Continuous depth vector in feet).
  * **Index 1:** `GR` / `GR (API)` (Gamma Ray curve readings in standard API units).
  * **Index 2:** `Neutron Porosity` / `NPHI` (Neutron Porosity index data values).
* **Automatic Scaling:** Input curves are automatically scaled via a standard variance normalization formula ($z = (x - \mu)/\sigma$). This ensures Gamma Ray logs ($\sim 0\text{--}150\text{ API}$) and Neutron Porosity logs ($\sim 0.05\text{--}0.45\text{ v/v}$) carry uniform mathematical weight during cumulative cost calculation.

---

## 2. Tunable Hyperparameters & Software Options

* `window_percents` (Float, range `0.0` to `1.0`): Represents the optimized Sakoe-Chiba window constraint width (notated as $\phi$ in the manuscript text) expressed as a decimal fraction of total sequence length. Setting `window_percents = 0.11` restricts the path optimization grid to an 11% diagonal corridor bandwidth, preventing geologically impossible thickness variations.
* `line_density_step` (Integer): Adjusts the step interval for plotting (e.g., `step = 120` draws every 120th path step to keep the diagnostic figures clear and clean).

---

## 3. Expected Operational Behavior

When execution cells are launched, the operational pipeline steps run sequentially:
1. **Matrix Initialization:** An $N \times M$ Euclidean distance matrix is computed between the multi-variate log tracks.
2. **Boundary Masking:** Matrix nodes violating the Sakoe-Chiba constraint condition ($\lvert i - j \rvert > \text{round}(\phi \times \max(N, M))$) are flagged with infinity ($\infty$).
3. **Path Optimization:** The minimum cumulative cost path is solved back from $(N, M)$ to $(0,0)$.
4. **Graphic Export:** Generates a high-contrast 300+ DPI twin-panel vector visualization. The output saves automatically as a `.jpg` graphic file inside a local `/L_curve` subfolder.
