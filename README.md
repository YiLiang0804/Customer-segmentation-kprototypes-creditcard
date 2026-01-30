# Customer Segmentation Practice Project (K-Prototypes) — Credit Card Behavior

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

## Model selection: why we report **k = 4** (instead of k = 5)
On the synthetic dataset, the elbow curve can suggest **k = 5** as a reasonable candidate.  
However, this project reports results using **k = 4** because it is the best trade-off for **business segmentation**:

1) **Interpretability over marginal cost reduction**  
The improvement from k=4 → k=5 can be small, while the additional cluster often behaves like a split of an existing segment without a clearly different strategy. For a portfolio project, the goal is to produce segments that are easy to name and explain.

2) **Actionability: fewer segments = clearer decisions**  
In real targeting/retention workflows, fewer well-defined segments are easier to operationalize (rules, offers, monitoring). k=4 supports cleaner, decision-ready segment profiles.

3) **Stability with limited sample size (~1,000 customers)**  
Higher k can introduce smaller segments that are more sensitive to initialization noise. I include a small stability check (multiple seeds) and prefer the more consistent, explainable k=4 solution for the final business summary.

**Conclusion:** k=5 is not “wrong”, but **k=4 is the version that is most interpretable and actionable**, so it is used in the final outputs and recommendations.

## Results (k = 4)
The final solution uses **k = 4** and produces:
- Segment size distribution
- Segment profiles (means of key KPIs by segment)
- A short business-style recommendation section (including a high-priority VIP segment)

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
