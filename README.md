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

## Data Visualization (Power BI)

An interactive dashboard integrates the modeling outputs, bridging the gap between machine learning and business strategy.

* **Executive View:** Real-time KPIs (Total Revenue, AOV, Active Customers).
* **Cohort Analysis:** Visualizes customer retention rates month-over-month.
* **Forecast vs. Actuals:** Tracks the accuracy of Holt-Winters predictions against real sales data.
* **Migration Analysis:** Sankey-style logic to view how customers move between segments over time.

> **[Click here to view the Interactive Dashboard](https://app.powerbi.com/reportEmbed?reportId=239e5a8d-5272-4353-9a00-af745c8728f2&autoAuth=true&ctid=5ba5ef5e-3109-4e77-85bd-cfeb0d347e82)**

## Quick Start

### Prerequisites
* Python 3.8+
* Jupyter Notebook or JupyterLab
* Power BI Desktop (for dashboard viewing)

### Installation
1.  **Clone the repository**
    ```bash
    git clone [https://github.com/your-username/online-retail-analysis.git](https://github.com/your-username/online-retail-analysis.git)
    cd online-retail-analysis
    ```

2.  **Install dependencies**
    ```bash
    pip install -r requirements.txt
    ```

### Usage
1.  **Data Processing**
    Run the first notebook to fetch and clean the raw data:
    ```bash
    jupyter notebook code/01_Data_Processing.ipynb
    ```
    *Output: Generates `data/online_retail_II_cleaned.csv`*

2.  **Modeling & Analysis**
    Run the second notebook to execute RFM clustering, forecasting, and CLV prediction:
    ```bash
    jupyter notebook code/02_Modeling_Analysis.ipynb
    ```
    *Output: Generates prediction files in `data/` for the Power BI dashboard.*
