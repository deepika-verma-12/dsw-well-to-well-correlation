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
* `line_density_step
