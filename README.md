# # Well-to-Well Correlation Analysis of Geophysical Well-Log Data of the October Oil Field, Gulf of Suez, Using Dynamic Space Warping Technique

## Overview

This repository provides a Python implementation for automated stratigraphic well-log correlation using Dynamic Space Warping (DSW) constrained by Sakoe–Chiba window parameter.

The workflow demonstrates automated well-to-well correlation and evaluates alignment quality under varying warping constraints.

## Data Availability Statement

To comply with industrial data privacy requirements, all authentic subsurface datasets have been completely redacted. This repository contains randomized, synthetic dummy well-log datasets (`data/`) spanning a 5000–5130 ft interval to demonstrate the operational flow and mathematical execution of the algorithms.

## Repository Structure

```text
data/
    Synthetic well-log datasets (.xlsx)

notebooks/
    Jupyter notebooks implementing the workflow

requirements.txt
    Python package dependencies

LICENSE
    MIT License
```

## How to Run

1. Clone the repository and navigate into it.
2. Install dependencies:

```bash
pip install -r requirements.txt
```

3. Run `notebooks/generate_dummy_data.ipynb` to initialize the data environment.
4. Open and execute any structural pair notebook (e.g., `gs172_2_j5.ipynb`) to reproduce the results

## Crucial Notes for Code Execution & Replication

If you are replicating this study or running the Jupyter notebooks from scratch using the synthetic data generation script, please note the following minor structural configurations to ensure the notebooks run flawlessly:

### 1. Data Directory Setup
The synthetic data generation script (`generate_dummy_data.ipynb`) is configured to output its generated Excel files into a directory named `/synthetic_data`. 
* **Action Required:** Before running the 6 correlation notebooks, please rename this output folder from `synthetic_data` to `data` (or move the generated `.xlsx` files into a folder named `data` in your root directory). The alignment notebooks are configured to look for files inside `../data/`.

### 2. Note on Column Indexing (`iloc`)
The alignment notebooks utilize positional slicing (`.iloc[:, [1, 2]]`) to extract the logging parameters for the Dynamic Time Warping (DTW) algorithm. 
* **If running on the provided synthetic data script:** The dummy data generator includes an index column, shifting the log columns. To run the correlation notebooks flawlessly against the *synthetic* data generation script without modifying the notebook code, ensure your input data matches the shape expected by the slicer (where columns 1 and 2 represent the target logs), or map your data tracks accordingly. 
* *Note: The notebooks are preserved in their finalized, fully-executed state to showcase the exact mathematical outputs and figures presented in the study.*


## Dependencies

* numpy
* pandas
* scipy
* scikit-learn
* matplotlib
* openpyxl

## Author

Deepika Verma
