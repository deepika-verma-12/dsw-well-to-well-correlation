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
   Ensure that the provided synthetic Excel well log files (e.g., `All-J5 .xlsx`, `All-J7A.xlsx`) are located within the local `data/` directory. The analysis notebooks are configured to read input data directly from this relative path.

---

## Phase 2: Running Alignment Computations

Once the environment is configured, the notebooks can be executed within the workspace by following these steps:

1. **Launch Workspace**  
   Launch your local Jupyter workspace (`jupyter notebook`) or open the repository directory within your preferred IDE.

2. **Open Notebook**  
   Navigate into the `notebooks/` directory and open a target processing file (for example, `J5_J7A.ipynb`).

3. **Execute Cells**  
   Execute the code blocks sequentially from top to bottom.

---

## 📋 Expected Notebook Execution Flow

* **Data Loading:** The notebook reads the `.xlsx` files directly from the `../data/` directory.
* **Data Preparation:** The selected well-log curves (applicable to both NPHI and GR data using the same code structure) are prepared and processed for the alignment.
* **Warping Computation:** The constrained Dynamic Space Warping path is calculated using the specified window constraint parameter ($\phi$).
* **Visualization Output:** The final code block generates a well-log correlation plot with colored stratigraphic zones and correlation lines. The final figure is automatically saved as a `.jpg` file.
