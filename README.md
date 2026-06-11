# # Automated Well-to-Well Correlation Using Dynamic Space Warping

## Overview

This repository provides a Python implementation for automated stratigraphic well-log correlation using Dynamic Space Warping (DSW) constrained by Sakoe–Chiba window parameter.

The workflow demonstrates automated well-to-well correlation and evaluates alignment quality under varying warping constraints.

## Related Manuscript

This repository accompanies the manuscript:

"Well-to-Well Correlation analysis of Geophysical Well-log data of the October Oil Field Gulf of Suez Using Dynamic Space Warping Technique"

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

1. Clone the repository and navigate to the project directory.
2. Install dependencies:

```bash
pip install -r requirements.txt
```

3. The synthetic datasets are located in the data/ directory.
4. All notebooks in notebooks/ are configured to access the datasets through the relative path ../data/.
5. Execute all cells.

 
## Dependencies

* numpy
* pandas
* scipy
* scikit-learn
* matplotlib
* openpyxl

## Authors

Deepika Verma, Reyi Karthik, E. Chandrasekhar

*Department of Earth Sciences, Indian Institute of Technology Bombay*
