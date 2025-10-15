# Fraud Detection – Rule-Based EDA

This project focuses on analyzing simulated transaction data to identify patterns and behaviors associated with fraudulent activity.  
The goal is to perform **Exploratory Data Analysis (EDA)** and derive **interpretable rule-based models** that can be used to detect and prevent future fraud.

---

## Project Objective
Financial institutions face ongoing challenges in detecting fraudulent transactions.  
While machine learning models are often used for this purpose, rule-based systems remain valuable for their simplicity, ease of implementation and efficiency.  

This project demonstrates how exploratory data analysis and feature engineering can lead to the creation of **data-driven, interpretable rules** that help identify fraudulent transactions with clear business logic.

## The main objectives are to:
1. Conduct comprehensive **EDA** to explore transaction characteristics and fraud distribution.  
2. Engineer relevant features that describe user and transaction behavior.  
3. Define **rule-based detection methods** derived from data insights.  
4. Evaluate each rule to assess detection performance.

---

## Methodology Overview
1. **Data Preparation:** Cleaning and normalizing the BankSim dataset, removing duplicates and constant columns, handling missing values and creating relevant features for further exploration.  
2. **Exploratory Data Analysis:** Conducting detailed exploration of both categorical and numerical variables to understand fraud distribution across transaction types, merchants, categories, time of day, and customer attributes. Visualized fraud rates and key distribution patterns to highlight the most fraud-prone transactions.
3. **Feature Engineering:** Creating behavioral and statistical features to capture customer and transaction patterns, including:
   - Transaction bursts — high frequency of transactions within short time windows  
   - First-time merchant indicators — flags transactions representing a customer’s first purchase with a given merchant  
   - Significant deviation from each customer's median transaction amount  
   - Missing-age indicator to capture incomplete demographic data 
4. **Rule Definition:** Designing clear and interpretable fraud detection rules with strong predictive power, derived from the exploratory findings, such as:
   - Transactions exceeding the 99th percentile of transaction amount  
   - Merchants or categories with high lift (fraud rate significantly above the global average)  
   - Combined high-risk rules that integrate categorical, amount-based, and behavioral conditions
5. **Performance Evaluation:** Measuring the effectiveness of each rule against the labeled fraud data using precision, recall, and lift.

---

## Key Findings

- **High-lift merchants and categories** are the most consistent sources of fraud concentration.  
  Transactions associated with a small group of merchants or categories show significantly higher fraud rates, 
  enabling broad fraud coverage (recall ≈0.9–0.97) but present lower precision score.  
  These patterns highlight that fraud is not uniformly distributed but clustered in specific transaction groups.

- **Amount-based indicators** are powerful but less generalizable.  
  Transactions with extremely high amounts (especially above the global 99th percentile) 
  achieved the highest precision (≈0.76) and lift (≈63× the global fraud rate), 
  but they cover a smaller portion of all fraud cases i.e have lower recall score.  
  This makes them ideal for targeted high-confidence alerts rather than general screening.

- **Combined rules** integrate categorical, amount, and behavioral signals. 
  Their precision/recall balance depends on the AND/OR design and chosen cutoffs (stricter AND yields higher precision, looser OR yields higher recall). 
  The benefit is flexible, interpretable logic aligned to fraud-detection needs.


- **Behavioral and contextual signals** (e.g., transaction bursts, first-time merchant) showed limited predictive power as standalone rules, 
  but add clarity and interpretability when combined with categorical and amount signals.


---
**Results (partial)**
*Partial view of the evaluation; see notebook for complete results: [BankSim_Fraud_Analysis.ipynb](./BankSim_Fraud_Analysis.ipynb)*
<img width="550" height="107" alt="image" src="https://github.com/user-attachments/assets/107dfe06-3bec-4178-a1fd-e77619b09769" />


---

**Conclusions**
- Simple categorical rules deliver **very high recall** with moderate precision.  
- Amount-based rules deliver **very high precision** but limited coverage.  
- Combined-logic rules achieve a more **balanced, high-performing trade-off**.

Overall, this project shows that rule-based systems, when guided by quantitative exploration, can deliver strong real-world performance,
providing transparency, explainability, and a solid foundation for extending into machine-learning–based fraud models.

## Overall Summary

This analysis reveals that fraud detection benefits most from **interpretable, data-driven rule systems** grounded in exploratory data insights.  
Fraud is highly concentrated within specific merchants, categories, and extreme-amount transactions — 
making these dimensions the backbone of practical detection rules.

--- 
## Environment & Setup
- **Python:** 3.10+
- **Install:** `pip install -r requirements.txt`
- **Data:** place `bs140513_032310.csv` under `data/`
- **Run locally:** open `BankSim_Fraud_Analysis.ipynb` in Jupyter and **Run All**
- **Run in Colab:** open `BankSim_Fraud_Analysis.ipynb` → create a `data/` folder → upload `bs140513_032310.csv` into `data/` → **Run All**
---

## Repository Structure
.
├─ BankSim_Fraud_Analysis.ipynb
├─ data/
│  └─ README.md
├─ requirements.txt
├─ .gitignore
└─ README.md

## Quickstart

```bash
pip install -r requirements.txt
# Place bs140513_032310.csv under data/
jupyter notebook
# Open BankSim_Fraud_Analysis_main_parts.ipynb and Run All
