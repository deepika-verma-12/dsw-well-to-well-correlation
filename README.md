# Automated Stratigraphic Correlation via Constraint-Based DTW

## 📝 Overview
This repository provides a Python-based scientific implementation for automated stratigraphic well-log alignment using Dynamic Time Warping (DTW). The matching framework integrates a customizable Sakoe-Chiba window constraint parameter ($p$) to optimize execution runtimes and prevent mathematically unrealistic vertical geological distortions during automated matching.

---

## 📚 User Guide & Software Specifications

To comply with *Computers & Geosciences* reproducibility guidelines, this section serves as the formal software manual describing data structures, configuration options, and expected operational behaviors.

### 1. Input Data Specifications & Preprocessing
The alignment scripts are engineered to process tabular digital well logs. Custom user datasets must strictly conform to the following schema:
* **File Format:** Microsoft Excel (`.xlsx`) workbooks. The target log profiles must reside in the first sheet.
* **Column Mapping Framework:** The optimization arrays pull variables via direct structural indexing:
  * **Column Index 0:** `Depth` (Continuous numeric tracking vector in feet).
  * **Column Index 1:** `GR` (Gamma Ray logging curves in standard API units).
  * **Column Index 2:** `Neutron Porosity` / `NPHI` (Neutron Porosity index data values).
* **Automatic Scaling:** Input curves are automatically normalized using a standard scaling variance approach ($z = (x - \mu)/\sigma$). This ensures both logging properties contribute equally to the distance matrix regardless of their raw physical units.

### 2. Tunable Hyperparameters & Software Options
Users can adjust the operational parameters directly inside the notebook script blocks:
* `window_p` (Float, range `0.0` to `1.0`): The Sakoe-Chiba constraint width parameter expressed as a decimal percentage of total sequence array length. For example, setting `window_p = 0.11` restricts the optimal warp path grid computation to an 11% diagonal corridor bandwidth, enforcing strict geological compliance.
* `line_density_step` (Integer): Controls visual output spacing. Adjusts the frequency of drawn correlation tie-lines (e.g., `step = 120` prints every 120th coordinate step to avoid graphical clutter).

### 3. Expected Operational Behavior
When a well-correlation notebook cell sequence is executed, the software operates along the following pipeline:
1. **Matrix Compilation:** Computes an $N \times M$ Euclidean distance matrix between multivariate well-log tracks.
2. **Boundary Masking:** Elements outside the Sakoe-Chiba constraint bounds ($\lvert i - j \rvert > \text{round}(p \times \max(N, M))$) are dynamically set to infinity ($\infty$), blocking invalid paths.
3. **Warp Optimization:** Solves the cumulative minimum cost matching path via dynamic programming.
4. **Graphic Export:** Renders a publication-grade twin-panel display. Correlation tie-lines anchor perfectly to the inside margins of the data frames. The output saves automatically as a high-contrast 300+ DPI `.jpg` file inside a local `/L_curve` folder.

---

## 🚀 How-To Tutorial: Step-by-Step Replication

Follow these steps to initialize your local workspace environment and run the full pipeline using the synthetic sandbox data.

### Step 1: Environment Setup
Clone this repository to your local system and install the required library dependencies using your preferred package manager:
```bash
git clone [https://github.com/deepika-verma-12/dsw-well-to-well-correlation.git](https://github.com/deepika-verma-12/dsw-well-to-well-correlation.git)
cd dsw-well-to-well-correlation
pip install -r requirements.txt

Step 2: Initialize the Synthetic Data EnvironmentBecause authentic subsurface logs are redacted to protect data privacy guidelines, you must programmatically initialize the simulation databases before running matches:Launch your local Jupyter interface (jupyter notebook) or open the directory within your IDE workspace.Open notebooks/generate_dummy_data.ipynb and select Run All Cells.Expected Behavior: The script initializes an automated generation loop, building mock spreadsheets containing synthetic randomized logs spanning a $5000\text{--}5150\text{ ft}$ sequence interval.Action Required: The mock logs generate inside your active workspace. Ensure these files remain visible to the correlation engines within your file pathways.Step 3: Run Alignment Computations & DiagnosticsNavigate into the notebooks/ directory and open any matching combination profile (e.g., gs172_2_j5.ipynb).Execute the cells sequentially. The data loading blocks will pull the matching spreadsheets, map the log variables, and calculate the cumulative distance matrix.Verify Output: The final code cell displays and exports your high-resolution well panels with crisp, dark-red correlation lines connecting identical structural horizons across the stratigraphy.
