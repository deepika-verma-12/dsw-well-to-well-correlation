# User Guide: Data Structures, Options, and Expected Behavior

This manual details the input specifications, runtime configuration options, and mathematical execution profiles for the Dynamic Time Warping (DTW) stratigraphic matching software.

---

## 1. Input Specifications & Preprocessing

The algorithm operates on tabular well-log data formats. To process custom fields or run the provided notebooks, inputs must strictly comply with the following structures:

### File Format
* **Extension:** Microsoft Excel (`.xlsx`) workbooks.
* **Sheet Placement:** The logging data must reside in the first sheet of the workbook.

### Data Columns (Ordering Framework)
The correlation arrays rely on positional column mapping. Input spreadsheets must maintain this index orientation:
| Column Index | Field Name | Description | Units | Type |
| :--- | :--- | :--- | :--- | :--- |
| `0` | `Depth` | Measured continuous depth track | Feet (ft) | Float |
| `1` | `GR (API)` / `GR` | Gamma Ray logging curve readings | API units | Float |
| `2` | `Neutron Porosity` / `NPHI` | Neutron Porosity index logging curve values | Decimals / v/v | Float |

### Data Preprocessing
Before cost-matrix compilation, the program automatically scales data via `StandardScaler`:
$$z = \frac{x - \mu}{\sigma}$$
This standardizes variance across the different scaling magnitudes of Gamma Ray ($\sim 0\text{--}150\text{ API}$) and Neutron Porosity ($\sim 0.05\text{--}0.45\text{ v/v}$), ensuring both measurements contribute equally to the distance calculation.

---

## 2. Configuration Options & Hyperparameters

The software provides tunable alignment parameters inside the notebook execution blocks:

* **Window Constraint Parameter (`window_p`):** Represents the Sakoe-Chiba constraint width expressed as a decimal fraction ($0.00$ to $1.00$) of the total sequence length. 
  * *Example:* A `window_p = 0.11` restricts the optimal warp path searching grid to a band within $11\%$ of the main diagonal matrix tracking line.
* **Line Density Step (`line_density_step`):** Controls visualization layout. Adjusts how many matched tie-lines are drawn between well panels (e.g., `step = 120` draws every 120th path step to prevent graphic clutter).

---

## 3. Expected Operational Behavior

When execution cells are launched, the operational pipeline steps run sequentially:

1. **Matrix Initialization:** An $N \times M$ Euclidean distance matrix is populated between the multi-variate tracks of Well A and Well B.
2. **Constraint Masking:** Matrix cells violating the Sakoe-Chiba boundary condition $\lvert i - j \rvert > \text{round}(p \times \max(N, M))$ are populated with infinity ($\infty$), ensuring the optimization pass cannot route through unrealistic geological thicknesses.
3. **Warp Optimization:** The minimum cumulative cost path is solved back from $(N, M)$ to $(0,0)$.
4. **Visualization Output:** A high-resolution matplotlib figure (300 to 400 DPI) is displayed and saved locally inside the `/L_curve` folder, anchoring dark red tie-lines perfectly to the inner borders of the well data tracks.
