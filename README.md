# Drug_Sensitivity_Analysis_Using_Genomics

This project explores how **basal gene expression profiles** of cancer cell lines can be used to predict their **response to anticancer drugs**, with a focus on **Palbociclib**, a CDK4/6 inhibitor. The goal is to derive biological insight and develop predictive models that can contribute to **precision oncology** efforts.

---

## Objective

- Predict the drug sensitivity (LN(IC50)) of cancer cell lines using their normalized gene expression data.
- Identify genes most associated with sensitivity or resistance to the drug.
- Evaluate model performance and interpret results through diagnostics and visualizations.

---

## Dataset Overview

Data is sourced from the **Genomics of Drug Sensitivity in Cancer (GDSC)** database:

- `Cell_line_RMA_proc_basalExp.txt` — Gene expression matrix.
- `GDSC2_fitted_dose_response_27Oct23.xlsx` — Drug response values (LN(IC50)).
- `Cell_Lines_Details.xlsx` — Cell line metadata.
- `mutations_all_20250318.csv` — (Not used in this phase).

---

## Project Workflow

1. **Data Preparation**
   - Filtered for target drug: **Palbociclib**.
   - Merged gene expression with response values.
   - Removed missing values and cleaned feature names.

2. **Feature Selection**
   - Used Ridge Regression to rank genes by importance.
   - Selected top 100 genes for model input.

3. **Modeling**
   - Ridge Regression with `RidgeCV` for hyperparameter tuning.
   - Performance metrics calculated on test set.

4. **Diagnostics & Interpretation**
   - Residual and QQ plots for model evaluation.
   - Visualized top gene contributions.
   - Interpreted top features in biological context.

---

## Results

- **Tuned Ridge Regression Performance:**
  - **RMSE:** ~1.17
  - **R² Score:** ~0.48

- Top predictive genes include: `ENKUR`, `FAM53A`, `RB1`, `CXorf30`, `SDR16C6P`.

---

## Biological Insight

The top-ranked genes may act as biomarkers for drug sensitivity or resistance. Known tumor suppressors like `RB1` validate the approach, while others suggest directions for further wet-lab exploration.

---

## Getting Started

1. Clone the repository.
2. Install required libraries.
3. Run the notebook in Jupyter.

```bash
git clone https://github.com/yourusername/drug-response-prediction.git
cd drug-response-prediction
python -m venv venv
source venv/bin/activate  # or .\venv\Scripts\activate on Windows
pip install -r requirements.txt
jupyter notebook
```
