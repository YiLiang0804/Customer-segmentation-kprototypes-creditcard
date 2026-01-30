# Customer Segmentation (K-Prototypes) — Credit Card Behavior

This project performs customer segmentation using **K-Prototypes** (mixed numeric + categorical features).  
It includes a documented fix for a common pitfall in clustering (**ID feature leakage**) and produces segment profiling outputs that translate clusters into actionable business insights.

## Overview
- Goal: Segment customers based on credit-card behavior to support targeting, retention, and risk-aware strategy.
- Method: K-Prototypes + scaling for numeric variables + elbow-style model selection.
- Output: Cluster labels and a segment-level summary table (means by segment).

## Data (Availability & Academic Policy)
This work was originally developed using a **course dataset provided by Prof. Tianxin Zou (University of Florida)** with approximately **1,000 customers**.

**The original dataset is not included in this public repository** to respect course policy and academic integrity guidelines.  
If you are a recruiter reviewing this repo, you can still evaluate the full workflow via:
- the notebooks (data prep → modeling → profiling),
- exported figures/tables in `/outputs`,
- and the documented modeling decisions and fixes.

> If you are a UF student in the course, use your authorized access to obtain the dataset locally and update the file path in the notebook.

## Key Pitfall & Fix: ID Feature Leakage
A frequent clustering mistake is accidentally including a customer identifier (e.g., `customer_id`) as a feature.
- Why it’s a problem: ID values do not represent behavior but still affect Euclidean distances, producing clusters that are hard to interpret.
- Fix applied here: drop pure identifiers and cluster only on behavioral features (numeric + categorical).

## Results Snapshot (k = 4)
Using k = 4, the notebook produces a segment summary table (means by segment) with variables such as:
- `BALANCE`, `PURCHASES`, `CREDIT_LIMIT`, `PAYMENTS`, `PRC_FULL_PAYMENT`
- plus a categorical proportion summary for `GENDER`

A screenshot / exported summary table is provided in `/outputs` (or embedded below if included).

## Repository Structure
- `Notebooks/` — analysis notebooks (prep → clustering → profiling)
- `outputs/` — exported figures and segment summary tables
- `requirements.txt` — Python dependencies

## How to Run
1. Clone the repo
2. Create environment and install dependencies:
   ```bash
   pip install -r requirements.txt
