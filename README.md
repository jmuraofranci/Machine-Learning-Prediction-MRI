# Machine Learning–Based Prediction of Structural MRI Measures from Military Environmental Exposures in Veterans

## Overview

This repository contains code and analysis investigating whether military environmental exposures (MEE) can predict structural MRI-derived brain measures in Veterans.
The study leverages machine learning regression models to test associations between exposure history and cortical/structural variation, providing a data-driven approach to evaluate subtle neural effects that may not be captured through traditional statistical methods.

The dataset analyzed included:

* **286 Veterans** evaluated at the War Related Illness and Injury Study Center (WRIISC).
* **MRI data** processed with *FreeSurfer* by the WRIISC Neuroimaging team.
* **Self-reported exposures** from the WRIISC Military Environmental Exposures Questionnaire.

---

## Key Methods

### Machine Learning Pipeline

The predictive modeling pipeline was built using Python and scikit-learn, and includes the following components:

* **Preprocessing**

  * `pandas` and `numpy` for data handling.
  * `SimpleImputer` for handling missing values.
  * `StandardScaler` for feature normalization.

* **Modeling**

  * `LinearRegression` from `sklearn.linear_model`
  * `KFold` cross-validation (10-fold) for model evaluation.

* **Evaluation Metrics**

  * `R²` (explained variance)
  * `RMSE` (Root Mean Squared Error) – custom scorer with `make_scorer`.
  * `MAE` (Mean Absolute Error).

---

## Findings

* Across >7,000 MRI–exposure prediction tests, linear regression models showed weak explained variance (mean R² ≈ 0.10).
* The strongest single model predicted cortical thickness in the right medial orbitofrontal cortex from chemical nerve agent exposure (mean R² = 0.072), but predictive power diminished after adjusting for age, sex, and traumatic brain injury (mean R² = 0.017).
* When exposures and covariates were included together, age consistently emerged as the strongest predictor of cortical thickness, explaining up to \~18–20% of the variance (mean R² = 0.196).
* Errors were low across all models (≈ 5.5% RMSE and 4.2% MAE relative to mean MRI values), but weak R² confirmed that environmental exposures did not meaningfully predict MRI outcomes.

---

## Repository Contents

* `pipeline_final.ipynb` – Jupyter Notebook containing the full ML pipeline, preprocessing, modeling, and evaluation code.

---

## Requirements

To run the pipeline, install dependencies via `pip`:

```bash
pip install numpy pandas scikit-learn matplotlib
```

---

## How to Run

1. Clone the repository:

   ```bash
   git clone https://github.com/USERNAME/REPO_NAME.git
   cd REPO_NAME
   ```
2. Open the notebook:

   ```bash
   jupyter notebook pipeline_final.ipynb
   ```
3. Run all cells to reproduce preprocessing, modeling, and evaluation.

---

## Limitations & Future Directions

* Lack of Gulf War Illness (GWI) diagnostic data limits interpretability, as prior studies show GWI itself influences brain structure.
* Reliance on self-reported exposures introduces potential recall bias.
* Future work should incorporate longitudinal MRI data, additional covariates (e.g., PTSD, education). 

---

## Disclaimer

**The views expressed are those of the presenter and do not necessarily represent the views or policy of the VA or the U.S. Government. The presenter has no financial conflicts of interest to disclose.**
