
# Census Income Prediction Project

This project uses the 1994 Census database (commonly known as the "Adult" or "Census Income" dataset) to build and evaluate machine learning classification models that predict whether an individual's income exceeds $50K/year.

## Table of Contents

1. [Project Overview](#project-overview)
2. [Dataset Description](#dataset-description)
3. [Setup and Requirements](#setup-and-requirements)
4. [Repository Structure](#repository-structure)
5. [Code Structure](#code-structure)
6. [How to Run](#how-to-run)
7. [References](#references)

---

### 1. Project Overview

This project demonstrates classification modeling using scikit-learn, including data preprocessing pipelines, custom transformers, model training, and evaluation with metrics beyond accuracy.

### 2. Dataset Description

- Source: 1994 Census database ([UCI ML Repository](https://archive.ics.uci.edu/dataset/2/adult))
- Columns include demographic and employment information (age, workclass, education, marital status, occupation, race, sex, capital_gain, capital_loss, days_per_week, hours_per_day, native_country, and income label).

### 3. Setup and Requirements

- Python 3.8+
- Libraries: pandas, numpy, scikit-learn, jupyter (for notebook)
- File required: `census_income.csv` (provided by instructor/Brightspace)

### 4. Repository Structure

```
.
├── census_income_assignment.ipynb   # Main Jupyter notebook with all code, pipeline, model training, and evaluation
├── census_income.csv                # Dataset file (not included in repo, provided separately)
├── README.md                        # Project summary and instructions
├── report.md                        # Project report detailing steps, rationale, and results
```

### 5. Code Structure

- `census_income_assignment.ipynb` — Contains all code for data loading, preprocessing, modeling, and evaluation.
- `README.md` — This file; provides summary, setup instructions, repo structure, and references.
- `report.md` — Detailed project report including explanations, metrics, and conclusions.

### 6. How to Run

1. Install dependencies:  
   `pip install pandas numpy scikit-learn jupyter`
2. Place `census_income.csv` in the working directory.
3. Open and run the notebook in Jupyter:  
   `jupyter notebook census_income_assignment.ipynb`

### 7. References

- [UCI Machine Learning Repository: Adult Dataset](https://archive.ics.uci.edu/dataset/2/adult)
- scikit-learn documentation: [https://scikit-learn.org/](https://scikit-learn.org/)
