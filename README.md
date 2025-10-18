# Business-Value-Driven Regression Test in Agile: An Intelligence Approach

This repository contains the code and datasets for a research project comparing five different algorithms for the constrained test case selection problem: a baseline Binary Constrained Particle Swarm Optimization (BCPSO), a Greedy algorithm, a Requirement-centric Genetic Algorithm (RTSGA), a hybrid GA with Hill Climbing (RTSGA-HC), and a purely Random Selector (RAND).

The project is structured to allow for the generation of synthetic datasets and the subsequent analysis of these datasets by each algorithm.

---

## Repository Structure

```
.
├── CodeFiles/
│   ├── Baseline/
│   │   ├── 124-40/
│   │   ├── 248-80/
│   │   └── BCPSO Code.ipynb
│   ├── Greedy/
│   │   ├── 124-40/
│   │   ├── 248-80/
│   │   └── Greedy_Algorithm.ipynb
│   ├── RTSGA-HC/
│   │   ├── 124-40/
│   │   ├── 248-80/
│   │   └── RTSGA-HC Code.ipynb
│   ├── RTSGA/
│   │   ├── 124-40/
│   │   ├── 248-80/
│   │   └── RTSGA Code.ipynb
│   └── Random/
│       ├── 124-40/
│       ├── 248-80/
│       └── Random Selection Code.ipynb
├── Dataset/
│   ├── mapped-dataset-124-40-defaultJS.xlsx
│   └── mapped-dataset-248-80-defaultJS.xlsx
└── Combined Visualization & Stat Reports/
    ├── 124-40/
    ├── 248-80/
    ├── final plotting code.ipynb
    └── statistical report code.ipynb
```

### Directory Descriptions

- **Algorithm Folders** (`Baseline/`, `Greedy/`, `RTSGA/`, `RTSGA-HC/`, `Random/`): Each folder contains the specific Jupyter Notebook (`.ipynb`) for that algorithm. The sub-folders (`124-40/`, `248-80/`) contain the pre-generated Excel report files:
  - `Baseline/124-40/` and `Baseline/248-80/`: Contains `BCPSO Results.xlsx`
  - `Greedy/124-40/` and `Greedy/248-80/`: Contains `Greedy Results.xlsx`
  - `RTSGA/124-40/` and `RTSGA/248-80/`: Contains `RTSGA Results.xlsx`
  - `RTSGA-HC/124-40/` and `RTSGA-HC/248-80/`: Contains `RTSGA-HC Results.xlsx`
  - `Random/124-40/` and `Random/248-80/`: Contains `RandomSelection Report.xlsx`

- **`Dataset/`**: Contains the input `mapped_dataset` files required to run the analysis scripts.

- **`Combined Visualization & Stat Reports/`**: Contains high-level notebooks for generating summary plots and performing rigorous statistical comparisons across all algorithm results.

---

## Workflow: How to Run the Experiments

The repository contains pre-generated results files in each algorithm's respective folders (`124-40/` and `248-80/`). If you want to reproduce the results or run experiments with different parameters, follow these steps in order for both the half-size (`124-40`) and full-size (`248-80`) datasets.

### Step 1: Run the BCPSO Baseline

The BCPSO algorithm serves as the primary baseline for comparison.

1. **Open the Notebook**: Navigate to `Baseline/` and open `BCPSO Code.ipynb`.
2. **Run the Script**: Execute all cells in the notebook.
3. **Provide Input**: When prompted, upload the corresponding dataset file from the `Dataset/` directory (e.g., `mapped-dataset-248-80-defaultJS.xlsx`).
4. **Get Output**: The script will generate a comprehensive Excel report named `BCPSO_Statistical_Analysis_Report.xlsx`.
5. **Organize Output**: Move this generated Excel file into the appropriate output directory (e.g., `Baseline/248-80/`) or compare with the existing `BCPSO Results.xlsx` file.

### Step 2: Run the Random Selection Baseline

This script establishes a naive baseline to gauge the effectiveness of the intelligent algorithms.

1. **Open the Notebook**: Navigate to `Random/` and open `Random Selection Code.ipynb`.
2. **Run the Script**: Execute all cells.
3. **Provide Input**: When prompted, upload the same dataset file you used for the BCPSO run.
4. **Get Output**: The script will generate an Excel report named `Random_Selection_Report_*.xlsx`.

### Step 3: Run the Greedy Algorithm

The Greedy algorithm provides a deterministic heuristic approach for comparison with the metaheuristic methods.

1. **Open the Notebook**: Navigate to `Greedy/` and open `Greedy_Algorithm.ipynb`.
2. **Run the Script**: Execute all cells in the notebook.
3. **Provide Input**: When prompted, upload the same dataset file used previously.
4. **Get Output**: The script will generate an Excel report with the greedy selection results.
5. **Organize Output**: Save the results in the appropriate sub-folder (`Greedy/124-40/` or `Greedy/248-80/`).

### Step 4: Run the RTS-GA Experiments

This notebook is designed to run multiple variations of the Genetic Algorithm.

1. **Open the Notebook**: Navigate to `RTSGA/` and open `RTSGA Code.ipynb`.
2. **Select a Version**: In **Cell 1**, you will find a dictionary named `GA_CONFIGURATIONS`. You can select which version to run by editing the `VERSION_TO_RUN` variable.
3. **Run the Script**: Execute all cells.
4. **Provide Input**: When prompted, upload the same dataset file used previously. The script will run 30 times for each budget level and may take a significant amount of time. It will save its progress to a `.csv` file after each budget is completed.
5. **Get Output**: At the end of the run, the script will generate a final Excel report named `Comprehensive_Report_[VersionName].xlsx`.
6. **Repeat**: Repeat this process for each of the GA variations you wish to test.

### Step 5: Run the RTS-GA-HC (Hybrid) Experiments

This notebook follows the exact same procedure as the standard RTS-GA.

1. **Open the Notebook**: Navigate to `RTSGA-HC/` and open `RTSGA-HC Code.ipynb`.
2. **Select a Version, Run, and Provide Input**: Follow the same steps as described in Step 4.
3. **Get Output**: The script will generate a `Comprehensive_Report_[VersionName].xlsx` file.
4. **Repeat**: Repeat the process for all desired GA-HC variations.

---

## Advanced Analysis: Combined Reports and Statistical Tests

The repository includes pre-generated Excel reports for all algorithms in their respective folders. You can directly use these files for comparative analysis using the scripts in the `Combined Visualization & Stat Reports/` directory.

### Final Plotting

- **File**: `final plotting code.ipynb`
- **Purpose**: This notebook loads multiple final report files (e.g., `BCPSO Results.xlsx` from `Baseline/248-80/`, Greedy results, Random results, and GA versions) and generates high-quality, combined comparative plots on a single axis. This is useful for creating figures for presentations or papers.
- **How to Run**: Open the notebook and follow the internal instructions. You can upload the existing Excel reports from the respective algorithm folders for comparison.

### Statistical Significance Reporting

- **File**: `statistical report code.ipynb`
- **Purpose**: This is the most advanced script. It performs a rigorous, publish-ready statistical analysis to determine if the performance differences between the algorithms are statistically significant.
- **How to Run**:
  1. Open the notebook and execute the cells.
  2. When prompted, upload the **existing Excel reports** from the algorithm folders (e.g., `BCPSO Results.xlsx` from `Baseline/248-80/`, Greedy results, Random results, RTS-GA results, etc.) for the five algorithms you wish to compare.
  3. The script will compile a single "tidy" dataset and then, for each time budget, it will:
     - Generate descriptive statistics and a box-whisker plot
     - Run a one-way ANOVA to check for overall significance
     - If a significant difference is found, it will run a Tukey HSD post-hoc test to identify exactly which pairs of algorithms are statistically different
  4. The final output is a comprehensive, multi-sheet Excel report containing all statistical tables and plots, with one sheet dedicated to each specific analysis (e.g., "BusinessValue_at_5pct_Budget").

---

## Using Pre-Generated Results

The repository includes pre-generated result files in each algorithm's output folders:

- **BCPSO Results**: `Baseline/124-40/BCPSO Results.xlsx` and `Baseline/248-80/BCPSO Results.xlsx`
- **Greedy Results**: `Greedy/124-40/Greedy Results.xlsx` and `Greedy/248-80/Greedy Results.xlsx`
- **Random Selection Results**: Available in `Random/124-40/` and `Random/248-80/`
- **RTS-GA Results**: Available in `RTSGA/124-40/` and `RTSGA/248-80/`
- **RTS-GA-HC Results**: Available in `RTSGA-HC/124-40/` and `RTSGA-HC/248-80/`

You can directly use these files with the analysis notebooks in `Combined Visualization & Stat Reports/` without needing to re-run the individual algorithm experiments.

---

## Notes

This structured workflow ensures that all experiments are reproducible and that the final analysis is comprehensive. The pre-generated results allow for immediate comparative analysis, while the included Jupyter notebooks enable reproduction of experiments with different parameters or datasets. For questions or issues, please refer to the individual notebook documentation or open an issue in the repository.
