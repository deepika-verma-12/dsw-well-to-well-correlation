# How-To Tutorial: Step-by-Step Pipeline Replication

This tutorial guides you through creating the synthetic testing sandbox and running the correlation workflow.

---

## Phase 1: Initialize the Synthetic Environment
Because raw field datasets are protected to safeguard corporate data privacy, you must programmatically compile the synthetic testing files:

1. Launch your Jupyter Notebook environment (`jupyter notebook`) or open the repository within your IDE.
2. Open **`generate_dummy_data.ipynb`** and select **Run All Cells**.
3. **Expected Behavior:** The script runs an automated seed generation loop to simulate active stratigraphic sequences. It programmatically builds mock logging spreadsheets spanning a $5000\text{--}5150\text{ ft}$ interval.
4. **File Placement:** The mock Excel logs generate directly into your main repository root directory, making them instantly accessible to the correlation scripts without requiring manual moving.

---

## Phase 2: Run Well Alignment Computations

With your synthetic sandbox data successfully initialized, you can run any individual matching notebook:

1. Open a target matching combination file (e.g., **`gs172_2_j5.ipynb`**).
2. Execute the setup cells to import baseline scientific libraries (`pandas`, `numpy`, `matplotlib`, `scikit-learn`).
3. Run the data ingestion block. The notebook will automatically pull the synthetic files from your root folder, index the log variables, and run the constrained cost matrix calculations.
4. **Verify the Results:** The final cell executes the custom visualization block, outputting a high-resolution, twin-panel plot with dark red tie-lines linking corresponding horizons across the well structures using your optimal `window_percents` ($\phi$) value. The output is automatically saved as a production-grade image file inside your local `/L_curve` folder.
