**1.** EURepoC Financial-Sector Cyber Incident Analysis Pipeline

This repository contains the Python analysis pipeline developed for the thesis:

**Financial-Sector Targeting in Cyber Incidents: An Explainable Machine Learning and Temporal Knowledge Graph Approach**

The code implements the empirical analysis framework used in Chapter 4 of the thesis, based on cyber incident data from the **European Repository of Cyber Incidents (EURepoC)**.

**2.** Project Overview

The objective of this project is to identify and predict cyber incidents targeting the financial sector relative to other sectors. The analysis combines structured incident variables, semantic text features, explainable machine learning, graph-based representations, panel-data construction, and robustness checks.

The pipeline covers the following sections:

```text
4.1 Descriptive Analysis
4.2 Econometric Analysis
4.3 Semantic Analysis
4.4 Explainable Machine Learning
4.5 Graph-Based Analysis
4.6 Panel Data and Event-History Analysis
4.7 Robustness and Sensitivity Analysis
```

**3.** Repository Structure

```text
.
├── eurepoc_chapter4_analysis_pipeline.py
├── requirements.txt
├── README.md
├── data/
│   └── eurepoc_global_dataset.xlsx
├── chapter4_outputs/
│   ├── descriptive_results.csv
│   ├── logit_results.csv
│   ├── probit_results.csv
│   ├── semantic_features.csv
│   ├── machine_learning_results.csv
│   ├── graph_results.csv
│   └── robustness_results.csv
└── figures/
    └── output_figures.png
```

**4.** Data Requirement

The analysis requires the EURepoC incident-level dataset in Excel format.

Before running the script:

1. Place the EURepoC Excel file in the project folder or in the `data/` directory.
2. Update the `FILE_PATH` variable in the script if the file name or location differs.

Example:

```python
FILE_PATH = "data/eurepoc_global_dataset.xlsx"
```

The original dataset is included in this repository. Download file aand follow instructions on Data Requirement to load file for processing

**5.** Environment Requirements

The code was developed and tested in Python 3.10+ / Google Colab.

Recommended environment:

```text
Python >= 3.10
pip >= 23.0
```

If running locally, it is recommended to create a virtual environment:

```bash
python -m venv venv
```

Activate the environment:

```bash
# Windows
venv\Scripts\activate

# macOS/Linux
source venv/bin/activate
```

Then install the required packages:

```bash
pip install -r requirements.txt
```

**6.** Required Libraries

The main libraries used in this project are:

```text
pandas
numpy
matplotlib
openpyxl
statsmodels
scikit-learn
xgboost
lightgbm
catboost
shap
sentence-transformers
bertopic
umap-learn
hdbscan
networkx
node2vec
torch
transformers
tqdm
```

**7.** Suggested `requirements.txt`

```text
numpy==2.0.2
pandas==2.2.2
matplotlib
openpyxl
statsmodels
scikit-learn
xgboost
lightgbm
catboost
shap
tqdm
umap-learn
hdbscan
networkx
node2vec>=0.6.0
sentence-transformers
transformers
bertopic
torch
```

**8.** Google Colab Setup

If running in Google Colab, install dependencies using:

```python
!pip install numpy==2.0.2
!pip install pandas==2.2.2
!pip install matplotlib openpyxl statsmodels scikit-learn xgboost lightgbm catboost shap tqdm
!pip install umap-learn hdbscan networkx node2vec>=0.6.0 sentence-transformers transformers bertopic torch
```

If dependency conflicts occur, restart the runtime and rerun the installation cells.

**9.** Running the Pipeline

Run the full script using:

```bash
Python Analysis - Agnes Thesis 20260020.ipynb
```

Or, in Jupyter/Colab, run the notebook/script cells sequentially.

The pipeline automatically creates the output directory:

```text
chapter4_outputs/
```

All generated CSV files, figures, model outputs, and robustness results are saved there.

**10.** Main Analysis Components

**11.** 4.1 Descriptive Analysis

Generates descriptive tables and figures showing cyber incidents by year, sector, incident type, and correlation patterns.

**12.** 4.2 Econometric Analysis

Estimates:

```text
Logit model
Probit model
Elastic Net Logistic Regression
Average Marginal Effects
```

These models identify structured determinants associated with financial-sector cyber targeting.

**13.** 4.3 Semantic Analysis

Uses transformer-based sentence embeddings and BERTopic to extract latent semantic themes from incident descriptions. The resulting topic features are used in subsequent machine learning models.

**14.** 4.4 Explainable Machine Learning

Implements:

```text
XGBoost
LightGBM
CatBoost
SHAP explainability
```

Model A uses structured variables only, while Model B combines structured and semantic features.

**15.** 4.5 Graph-Based Analysis

Constructs a cyber-incident knowledge graph linking incidents, threat actors, sectors, countries, attack methods, and incident types. Node2Vec is used to generate graph embeddings for Model C.

**16.** 4.6 Panel Data and Event-History Analysis

Transforms the incident-level dataset into a balanced country-sector-month panel and estimates a discrete-time event-history model to examine temporal persistence in cyber incidents.

**17.** 4.7 Robustness and Sensitivity Analysis

Includes:

```text
Alternative financial-sector definition
Europe-only analysis
Expanding-window validation
```

These tests assess the stability of the main findings across definitions, regions, and time periods.

**18.** Output Files

The pipeline produces outputs such as:

```text
4_1_1_incidents_by_year_sector.csv
4_2_1_logit_results.csv
4_2_2_probit_results.csv
4_2_3_elastic_net_results.csv
4_2_4_logit_marginal_effects.csv
4_3_1_bertopic_topic_info.csv
4_4_model_A_structured_results.csv
4_4_model_B_structured_semantic_results.csv
4_4_5_shap_importance.csv
4_5_4_model_C_structured_semantic_graph_results.csv
4_5_5_incremental_model_comparison.csv
4_6_1_country_sector_month_panel.csv
4_6_2_event_history_logit_results.csv
4_7_1_strict_finance_robustness.csv
4_7_2_europe_only_logit.csv
4_7_3_expanding_window_validation.csv
```

**19.** Notes on Reproducibility

Random seeds are set where applicable to improve reproducibility. However, some components, particularly BERTopic, UMAP, HDBSCAN, and Node2Vec, may produce slightly different results depending on package versions, hardware, and runtime environment.

For best reproducibility, users should:

```text
Use the same Python version
Use the package versions listed in requirements.txt
Set random seeds consistently
Run the full pipeline from a clean runtime
Avoid modifying intermediate datasets manually
```

**20.** Citation

If using this code or methodology, please cite the associated thesis:

```text
Ogbuka, C. A. (2026). Financial-Sector Targeting in Cyber Incidents: An Explainable Machine Learning and Temporal Knowledge Graph Approach. Master’s Thesis, NOVA Information Management School, Universidade Nova de Lisboa.
```

**21.** Author

**Chidinma Agnes Ogbuka**
Master’s in Statistics and Information Management
Specialization in Risk Analysis and Management
NOVA Information Management School, Universidade Nova de Lisboa
