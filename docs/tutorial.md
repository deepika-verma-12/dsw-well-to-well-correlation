# How-To Tutorial: Step-by-Step Pipeline Replication

This tutorial guides you through setting up your local repository workspace and running the well-log correlation workflow using the provided synthetic datasets.
---

## Phase 1: Environment Preparation

1. Open your system's terminal interface and clone this repository:
   ```bash
   git clone [https://github.com/deepika-verma-12/dsw-well-to-well-correlation.git](https://github.com/deepika-verma-12/dsw-well-to-well-correlation.git)
   cd dsw-well-to-well-correlation

Install the necessary Python package dependencies:
pip install -r requirements.txt

Workspace Verification: Ensure that the provided synthetic Excel logging files (e.g., All-J5 .xlsx, All-J7A.xlsx) are visible within your local data/ directory. The analysis notebooks are hardcoded to ingest inputs directly from this relative path.

Phase 2: Running Alignment ComputationsWith the environment configured, you can execute any structural matching profile in the workspace:Launch your local Jupyter workspace (jupyter notebook) or open the directory within your preferred IDE.Navigate into the notebooks/ directory and open a target processing file (for example, J5_J7A.ipynb).Execute the code blocks sequentially from top to bottom.Expected Pipeline Behavior:Data Ingestion: The notebook loads the designated .xlsx workbooks directly from the ../data/ directory.Preprocessing & Scaling: The numeric log channels are isolated and normalized.Warp Optimization: The constrained Dynamic Time Warping path runs utilizing your optimal window_percents ($\phi$) constraint.Review Results: The final cell renders a high-contrast well panel plot with dark-red tie-lines locking corresponding structural horizons across the stratigraphy. The resulting figure exports automatically as a publication-ready graphic file inside your local workspace.
