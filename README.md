# Customer Segmentation (K-Prototypes) — Credit Card Behavior

Customer segmentation using **K-Prototypes** (mixed categorical + numeric features).  
This repo highlights a real-world clustering pitfall (**ID feature leakage**) and shows a clean, decision-oriented segmentation workflow with a short business-style summary.

## What this project demonstrates
- Mixed-type clustering with **K-Prototypes**
- Feature preprocessing (scaling numeric variables)
- Choosing k using an **elbow-style** diagnostic
- Translating clusters into **segment profiles + business actions**
- A practical quality check: **excluding `CUST_ID` to avoid leakage**

## Data policy (Academic integrity)
This project was originally developed using a course dataset provided by **Prof. Tianxin Zou (University of Florida)** (≈ 1,000 customers).  
**The original course dataset is NOT included** in this public repository.

To enable reproducibility for recruiters and portfolio review, this repo includes a **synthetic demo dataset** with the same schema:
- `data/synthetic_creditcard_behavior.csv`

The synthetic dataset is created for demonstration only, is not derived from the course dataset, and should not be used to infer real customer behavior.

## Features
- Identifier (not used for clustering): `CUST_ID`
- Categorical: `GENDER`
- Numeric: `BALANCE`, `PURCHASES`, `CREDIT_LIMIT`, `PAYMENTS`, `PRC_FULL_PAYMENT`

## Key pitfall & fix: ID feature leakage
Including identifiers (e.g., `CUST_ID`) as model inputs can distort distance calculations and produce clusters that look “stable” but are not behavior-driven.  
This repo includes a short comparison (with vs. without ID) and keeps the final model **ID-free** for interpretability.

## Results (k = 4)
The final solution uses **k = 4** and produces:
- Segment size distribution
- Segment profiles (means of key KPIs by segment)
- A short business-style recommendation section, including a **high-priority small VIP segment**

Key outputs are saved under:
- `outputs/` (plots and summary tables)

## Repository structure
- `notebooks/`
  - `01_segmentation_kprototypes.ipynb` (main notebook)
- `data/`
  - `synthetic_creditcard_behavior.csv` (demo dataset)
- `outputs/` (exported figures / segment summaries)
- `requirements.txt`

## How to run
1) Clone the repo  
2) Install dependencies:
```bash
pip install -r requirements.txt
