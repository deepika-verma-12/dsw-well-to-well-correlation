# How-To Tutorial: Step-by-Step Pipeline Replication

This tutorial demonstrates a step-by-step workflow for running the Dynamic Space Warping code on different well pairs.
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
   Ensure that the provided synthetic Excel well log files (e.g., `All-J5 .xlsx`, `All-J7A.xlsx`) are located within the local `data/` directory. The analysis notebooks are configured to read input data directly from this relative path.

---

## Phase 2: Running Alignment Computations

Once the environment is configured, the notebooks can be executed within the workspace by following these steps:

1. **Launch Workspace**  
   Launch your local Jupyter workspace (`jupyter notebook`) or open the repository directory within your preferred IDE.

2. **Open Notebook**  
   Navigate into the `notebooks/` directory and open a target processing file (for example, `J5_J7A.ipynb`).

3. **Execute Cells**  
Go to the top menu of the notebook, click Cell, and select Run All (or press Shift + Enter to run each cell sequentially from top to bottom) to run the entire analysis.
---

## 📋 Expected Notebook Execution Flow

* **Data Loading:** The notebook reads the `.xlsx` files directly from the `../data/` directory.
* **Data Preprocessing:** Standardizes both Gamma Ray (GR) and Neutron Porosity (NPHI) curves using StandardScaler (Z-score normalization) to achieve a mean of 0 and a standard deviation of 1.
* **Window Optimization:** Executes a grid search across constraint percentages to identify the optimal Sakoe-Chiba window via elbow curve analysis.
* **Distance & Path Computation:** Calculates the minimum alignment cost and the optimal warping path using the constrained Dynamic Space Warping algorithm.
* **Output Visualization:** Each notebook pipeline executes completely from top to bottom and automatically generates 6 final figures (3 for GR and 3 for NPHI):

