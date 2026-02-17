# Online-Retail-Analysis

## Project Overview

This project provides a comprehensive data science solution for a UK-based online retail dataset (UCI Online Retail II). Beyond basic exploration, it implements a full-stack analytics pipeline: from automated data ingestion and cleaning to advanced customer segmentation, sales forecasting, Customer Lifetime Value (CLV) prediction, and a personalized recommendation engine.



The goal is to transform raw transactional data into actionable business intelligence, visualized through integration with Power BI.



---



## Technical Stack

\- Language: Python 3.x (Windows 11 Environment)

\- Data Processing: Pandas, NumPy

\- Machine Learning: Scikit-learn (K-Means), Lifetimes (BG/NBD, Gamma-Gamma)

\- Time Series: Statsmodels (Holt-Winters Exponential Smoothing)

\- Recommender System: Surprise (SVD/Collaborative Filtering)

\- Visualization: Matplotlib, Seaborn, Power BI



---



## Repository Structure

```text

├── code/

│   ├── 01_Data_Processing.ipynb    # ETL, cleaning, and feature engineering

│   └── 02_Modeling_Analysis.ipynb  # Advanced modeling and evaluation

├── data/                           # Processed CSV outputs for BI tools

├── others/                         # Power BI templates (.pbix) and rule-based metadata

└── requirements.txt                # Project dependencies
```



---



## Key Technical Modules

### 1. Customer Segmentation (RFM + K-Means)
Identifies distinct customer personas to enable precision marketing.
* **Methodology:** Calculated **Recency, Frequency, Monetary (RFM)** metrics.
* **Optimization:** Applied **Log Transformation** and **StandardScaler** to handle skewness, used **IQR** to remove statistical outliers, and selected optimal $k$ via the **Elbow Method**.
* **Outcome:** Segmented user base into actionable groups (e.g., *Champions, Loyalists, At-Risk, Hibernating*).

### 2. Sales Forecasting (Time Series)
Predicts future revenue trends to optimize inventory management.
* **Model:** **Holt-Winters Triple Exponential Smoothing** (Additive Trend & Seasonality).
* **Configuration:** Resampled data to **Weekly ('W')** frequency with a 52-week seasonal period to capture annual retail cycles.
* **Impact:** Generates an 8-week forward-looking sales forecast with confidence intervals.

### 3. Customer Lifetime Value (CLV) Prediction
Estimates the future monetary value of each customer using the **Buy-'Til-You-Die (BTYD)** framework.
* **Frequency Model:** **BG/NBD** (Beta-Geometric/Negative Binomial Distribution) to predict future transaction counts.
* **Monetary Model:** **Gamma-Gamma** to estimate average transaction value.
* **Result:** Predicted 12-month CLV for individual users to guide Customer Acquisition Cost (CAC) allocation.

### 4. Recommendation Engine
Increases cross-selling opportunities through personalized product suggestions.
* **Algorithm:** **SVD (Singular Value Decomposition)** from the `scikit-surprise` library.
* **Feature:** Collaborative filtering based on implicit feedback (Purchase Quantity).
* **Metric:** Evaluated using **Hit Rate @ 10** to ensure relevance of top recommendations.
