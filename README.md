# Automated Stratigraphic Correlation via Constraint-Based DTW

## 📝 Overview
This repository provides a Python-based scientific implementation for automated stratigraphic well-log alignment using Dynamic Time Warping (DTW) with a customizable Sakoe-Chiba window constraint.

---

## 🔒 Confidentiality & Use of Synthetic Data
The authentic subsurface well-log datasets utilized to develop and validate this methodology belong to the October Oil Field (Suez Rift, Egypt). Due to strict corporate data privacy policies and industrial confidentiality agreements, the raw field production data cannot be made publicly available. 

To satisfy the open-science reproducibility guidelines of *Computers & Geosciences*, this repository utilizes a programmatic data generator to produce synthetic sandbox datasets. These simulated logs mirror the exact structural dimensionality, data ranges, and variance properties of the real field logs. This allows researchers to completely test, verify, and execute the entire alignment pipeline without compromising restricted data assets.

---

## 📚 Project Documentation & User Manuals
Comprehensive instructions, technical specifications, and execution walkthroughs have been separated into dedicated documentation modules to ensure repository clarity:

* **[User Guide: Data Specifications & Options](./docs/user_guide.md)** — Detailed manual outlining file schemas, logging tracks, variable normalization, and tunable mathematical constraints.
* **[How-To Tutorial: Replicating the Pipeline](./docs/tutorial.md)** — A step-by-step walkthrough detailing environment setup, synthetic database generation, and notebook execution.

---

## 🛠️ Quick Start
1. Clone the repository and install the baseline environment requirements:
   ```bash
   git clone [https://github.com/deepika-verma-12/dsw-well-to-well-correlation.git](https://github.com/deepika-verma-12/dsw-well-to-well-correlation.git)
   cd dsw-well-to-well-correlation
   pip install -r requirements.txt

Install Dependencies:

```bash
pip install -r requirements.txt
