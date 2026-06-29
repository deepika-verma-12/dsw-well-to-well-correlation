# User Guide: Inputs, Outputs, and Tunable Options

This guide describes the data file schemas, configuration options, and expected operational behaviors for replicating the well-log correlation framework.

## 1. Input Data Specifications & Preprocessing

To ensure seamless execution, target subsurface profiles must strictly conform to the structural layout outlined below. 

### Spreadsheet Schema Requirements
* **File Format:** Microsoft Excel (`.xlsx`) files. All data must be placed in the very first tab (Sheet 1) of the Excel file.
* **Column Positions:** The code reads and maps your well logs based on their specific column numbers:
*  * **Column Index 0:** `Depth` (Measured depth values recorded in feet).
*  * **Column Index 1:** `GR` / `GR (API)` (Gamma Ray log recorded in standard API units).
*  * **Column Index 2:** `Neutron Porosity` / `NPHI` (Neutron Porosity log index values).

Prior to cost matrix construction, log channels are automatically standardized:

$$z = \frac{x - \mu}{\sigma}$$

---

## 2. Configuration Parameters

* **`window_percents`** (Float, range `0.0` to `1.0`): Specifies the Sakoe-Chiba window constraint width, corresponding to the parameter $\phi$ in the manuscript text. It is expressed as a decimal representation of a percentage of the total sequence length, restricting the warping path search window to ensure a realistic warping path and geologically realistic correlation.

---

## 3. Expected Operational Behavior & Outputs

When a well-pair processing notebook is executed, the pipeline steps through three key visual optimization and alignment stages:

### Stage 1: Sakoe-Chiba Window Selection
* **Description:** Optimization of the Sakoe-Chiba (SC) window parameter shown in the form of an L-curve to identify the optimal SC Parameter value ($\phi$).

### Stage 2: Constrained Warping Path 
* **Description:** The minimum-cost warping path overlaid on the cumulative cost matrix, dynamically constrained within the optimal Sakoe-Chiba window parameter.

### Stage 3: Well-to-Well Correlation
* **Description:** The final well-to-well correlation panel displaying the target logs (NPHI or GR) side-by-side for the wells processed in the selected notebook. This correlation is based on Dynamic Space Warping (DSW) calculations, constrained using the Sakoe-Chiba parameter. The plot includes background color-fills for the lithology zones, connected by explicit correlation paths between the aligned depths, and the final graphic is automatically saved as a `.jpg` image.
