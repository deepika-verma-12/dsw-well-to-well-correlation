# Automated Stratigraphic Correlation via Constraint-Based DSW

## Overview

This repository provides a Python implementation for automated stratigraphic well-log correlation using Dynamic Space Warping (DsW) constrained by Sakoe–Chiba window parameter.

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
4. Open and execute any structural pair notebook (e.g., `gs172_2_j5.ipynb`) to reproduce the results.

## Dependencies

* numpy
* pandas
* scipy
* scikit-learn
* matplotlib
* openpyxl

## Author

Deepika Verma
