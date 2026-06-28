# How-To Tutorial: Step-by-Step Pipeline Replication

This tutorial demonstrates a step-by-step example workflow for executing the constrained Dynamic Space Warping framework on a well correlation pair.

---

## Phase 1: Environment Preparation

1. **Clone the Repository** Open your system's terminal interface and clone this repository:
   ```bash
   git clone [https://github.com/deepika-verma-12/dsw-well-to-well-correlation.git](https://github.com/deepika-verma-12/dsw-well-to-well-correlation.git)
   cd dsw-well-to-well-correlation

Alternatively, you can click the green "Code" button on the GitHub page and select "Download ZIP".

2. **Install Dependencies**  
   Install the necessary Python package dependencies using your system terminal:
   ```bash
   pip install -r requirements.txt


3. **Workspace Verification**  
   Ensure that the provided synthetic Excel logging files (e.g., `All-J5 .xlsx`, `All-J7A.xlsx`) are visible within your local `data/` directory. The analysis notebooks are hardcoded to ingest inputs directly from this relative path.

---

## 🚀 Phase 2: Running Alignment Computations

With the environment configured, you can execute any structural matching profile in the workspace by following these steps:

1. **Launch Workspace**  
   Launch your local Jupyter workspace (`jupyter notebook`) or open the repository directory within your preferred IDE.

2. **Open Notebook**  
   Navigate into the `notebooks/` directory and open a target processing file (for example, `J5_J7A.ipynb`).

3. **Execute Cells**  
   Execute the code blocks sequentially from top to bottom.

---

## 📋 Expected Pipeline Behavior

* **Data Ingestion:** The notebook loads the designated `.xlsx` workbooks directly from the `../data/` directory.
* **Preprocessing & Scaling:** The numeric log channels are isolated and normalized automatically.
* **Warp Optimization:** The constrained Dynamic Time Warping path runs utilizing your optimal `window_percents` ($\phi$) constraint.
* **Review Results:** The final cell renders a high-contrast well panel plot with background stratigraphic zone color-fills and clean, dark-red correlation lines. Figures save automatically as `.jpg` files.
