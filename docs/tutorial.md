# How-To Tutorial: Replicating Strategic Match Implementations

This tutorial provides a complete step-by-step walkthrough to initialize your environment, programmatically build the synthetic logs sandbox, and run the matching pipeline.

---

## Phase 1: Environment & Directory Preparation

1. Open your system command terminal and clone the repository:
   ```bash
   git clone [https://github.com/deepika-verma-12/dsw-well-to-well-correlation.git](https://github.com/deepika-verma-12/dsw-well-to-well-correlation.git)
   cd dsw-well-to-well-correlation
   Install the necessary software libraries using the provided requirements document:Bashpip install -r requirements.txt
Verify that your root directory contains an empty folder named data/ and an executable workspace named notebooks/.Phase 2: Generating the Synthetic Sandbox EnvironmentBecause the authentic logging profiles remain confidential to respect corporate privacy, you must first initialize the simulation database.Launch your local Jupyter environment by typing jupyter notebook in your terminal, or open the folder workspace within VS Code.Navigate into the notebooks/ directory and open generate_dummy_data.ipynb.Click "Run All Cells".Expected Behavior: The notebook initializes a randomized seed generation loop and programmatically builds 8 standard Excel files (All-NO159-2.xlsx, All-J5 .xlsx, etc.) representing active logging intervals from $5000\text{ to }5150\text{ ft}$.Action Required: The dummy file outputs will generate inside the folder where the script is located. To match the file pathways expected by your correlation engines, make sure these generated .xlsx spreadsheets are placed inside your root data/ directory.Phase 3: Executing Well Alignment ComputationsWith the log assets now populated inside the database, you can run any matching combination profile.Open a target pair notebook from the notebooks/ directory—for example, gs172_2_j5.ipynb.Run the initialization blocks to load the standardized dependencies (pandas, numpy, scikit-learn).Execute the data loading block. The spreadsheet data will pull from ../data/ and map column fields directly into active arrays.Run the core DTW optimization computation. The system will restrict path steps to your target window limit (window_p = 0.11).Review Results: The final cell executes the specialized graphic generation block. It will output a publication-ready vertical well-to-well matching display with crisp, dark-red correlation ladders connecting the stratigraphy. A copy of the graphic is generated and saved automatically into a local subfolder named L_curve/.
5. Scroll down and click **`Commit changes`**.

---

### What to do next:
Once these files are saved, your repository homepage will look updated, professional, and completely covered by the detailed documentation the *Computers & Geosciences* editors requested. 

Copy your repository link (`https://github.com/deepika-verma-12/dsw-well-to-well-correlation`) and reply to the journal editor, letting them know that the repository has been updated with a full **`docs/`** suite including complete user manuals, data specifications, parameter lists, and run tutorials. They will love this layout!
