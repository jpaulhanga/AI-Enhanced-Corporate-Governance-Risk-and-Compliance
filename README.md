# AI-Enhanced-Corporate-Governance-Risk-and-Compliance

This Project explore an **AI-approach towards achieving Corporate Governance, Risk and Compliance engineering** with the main aim of accurately and efficiently to better handle complex corporate governance documents and compliance regulations across different jurisdictions, enforce compliance, automatically generate audit logs, coordinate compliance reporting, alert escalation, regulatory filings, and cross-department knowledge transfer, and proactively simulate compliance risks and advise on preventive measures. Therefore, expanding from **decision support to decision augmentation**, transforming governance operations. 

The proposed solutionn seeks to extend the baseline paper about improving corporate governance and compliance using AI, to an AI-driven governance framework where each document get both **Risk level** (low/Medium?high) and Risk Type ( Financial, Legal, Operational).

## Methodology.

**Step 1: Data Collection :- Gather structured + unstructured inputs**

  Numeric financial dataset: - **Corporate Financial Risk Assessment Dataset** Provides structured financial indicators.
  
  Text dataset (10-K reports): - **SEC EDGAR Annual Financial Filings – 2021, SEC Filings Financial Summary – Apple/Tesla/Microsoft** Contains long governance/financial texts.
  
ESG ratings dataset: - **Public Company ESG Ratings, S&P 500 ESG Risk Ratings** Provides governance, environmental, and social risk scores.

**Output**: Unified dataset aligned on ('ticker', 'year').

**Method**: Same as baseline — collect data, join by company + year.

**Step 2: Preprocessing:- Prepare clean inputs and labels**

  Numeric preprocessing: fill missing values, normalize with StandardScaler.

  Text preprocessing: clean raw 10-K text (remove special characters, whitespace).

  Label design:
  
    Risk Level: Low/Medium/High
      
    Risk Type (extended): added 8 categories (Financial, Legal, Operational, Ethical, Strategic, Reputational, Cyber, ESG).

      
  Output:

  X_num = numeric features
  
  texts = cleaned texts

  y_level, y_type = labels

**Step 3: NLP Feature Extraction:-Convert texts into numerical embeddings.**

  Models:
  
    FinBERT for financial texts
    
    Legal-BERT for regulatory texts

  Method: chunk text into 512 tokens, embed with transformer, pool into single vector per document.
  
  Optional (extension): Add lexicon-based features for each risk type (keyword counts).
  
Output: X_text = dense vectors representing each 10-K.

**Step 4: Machine Learning (extended beyond baseline) : - Train models to predict risk level and risk type.**

  **Feature fusion:**
  
    Concatenate X_text + X_num.

  **Models:**

    Risk Level → multi-class classifier (Logistic Regression / Random Forest / Neural Network).

    Risk Type → multi-label classifier (extension: One-vs-Rest Logistic Regression or multi-task neural net with sigmoid outputs).
  
  **Evaluation:**

    Risk Level: Accuracy, Macro-F1, Confusion Matrix (same as baseline).

    Risk Type: per-class Precision/Recall/F1, Hamming Loss (extension).
  
  **Output:**

    risk_level_pred.csv → one label (low/medium/high)

    risk_type_pred.csv → multiple labels from the 8 categories


