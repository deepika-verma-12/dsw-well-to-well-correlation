# Well-to-Well Correlation analysis of Geophysical Well-log data of the October Oil Field Gulf of Suez Using Dynamic Space Warping Technique


## Overview
This repository provides a Python-based scientific implementation for automated stratigraphic well-log alignment using Dynamic Space Warping (DSW) with a customizable Sakoe-Chiba window constraint.

---

## Data Privacy & Use of Synthetic Data
The subsurface well-log datasets utilized to develop and validate this methodology belong to the October Oil Field (Gulf of Suez, Egypt). Due to data privacy requirements and confidentiality restrictions, the raw field data cannot be made publicly available.

To facilitate workflow replication, this repository provides pre-generated synthetic datasets located directly within the `data/` folder. These files retain the original naming conventions used throughout the manuscript, but the underlying log curves are fully synthetic to protect data privacy.

---

## Project Documentation & User Manuals
Comprehensive instructions, technical specifications, and execution walkthroughs have been separated into dedicated documentation modules to ensure repository clarity:

* **[User Guide: Data Specifications & Options](./docs/user_guide.md)** — A comprehensive user guide describing inputs, outputs, tunable options, and expected behavior.
* **[How-To Tutorial: Replicating the Pipeline](./docs/tutorial.md)** — A practical tutorial providing how-to instructions and execution workflows for typical use cases.

---

## Quick Start
1. Clone the repository and install the baseline environment requirements:
   ```bash
   git clone [https://github.com/deepika-verma-12/dsw-well-to-well-correlation.git](https://github.com/deepika-verma-12/dsw-well-to-well-correlation.git)
   cd dsw-well-to-well-correlation
   pip install -r requirements.txt

Install Dependencies:

```bash
pip install -r requirements.txt
