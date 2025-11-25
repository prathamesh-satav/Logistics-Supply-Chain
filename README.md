# Logistics Performance Analytics Pipeline

## 📖 Overview
This project implements a robust **ETL (Extract, Transform, Load) pipeline** to clean real-world logistics data and visualize supply chain performance. It transforms raw, dirty shipment logs into actionable insights regarding **delivery delays, transporter efficiency, and cost optimization**.

The workflow consists of a Python-based data cleaning script and a Power BI dashboard optimized for Natural Language Query (Q&A).

## Tech Stack
* **Python:** Pandas, NumPy (Data Processing)
* **Data Cleaning:** Outlier capping (1st/99th percentile), Median Imputation
* **Visualization:** Power BI (Q&A, Key Influencers)
* **Environment:** Google Colab / Jupyter Notebooks

## Key Features

### 1. Automated Data Cleaning Pipeline
The Python script (`clean_logistics_data.py`) performs 8 rigorous steps:
* **Validation:** Automatically detects negative values, duplicates, and inconsistent categories.
* **Date Logic:** Calculates *true* delays by comparing `Scheduled` vs `Actual` dispatch dates, overwriting inaccurate manual logs.
* **Outlier Handling:** Caps extreme values in `Package Weight` and `Transport Cost` using the 1st and 99th percentile method to preserve data integrity without skewing averages.
* **Imputation:** Handles missing data intelligently (Median for numeric, Calculated Dates for missing timestamps).

### 2. Feature Engineering
New metrics generated for business context:
* `Is_Delayed`: Binary flag (1/0) for ML modeling.
* `Delay_Category`: Segmentation (Early, On Time, Slight Delay, Serious Delay).
* `Route`: Origin → Destination mapping.
* `Cost_per_kg`: Efficiency metric for transport spending.

### 3. Power BI Q&A Integration
The clean dataset is optimized for Power BI's **Natural Language Query** engine, allowing users to ask questions like:
* *"Average Dispatch Delay by Transporter"*
* *"Total Transport Cost by Season as waterfall chart"*
* *"Count of Serious Delays by Origin map"*

## Dataset Structure
The processed dataset (`clean_incom2024_delay_dataset.csv`) contains:
* **Dimensions:** Order ID, Shipment Mode, Transporter, Origin, Destination, Season, Priority.
* **Metrics:** Dispatch Delay (Days), Transport Cost, Package Weight, Delivery Time.

## How to Run
1.  Clone the repo.
2.  Install dependencies: `pip install pandas numpy`
3.  Run the pipeline: `python clean_logistics_data.py`
4.  Open `Logistics_Dashboard.pbix` in Power BI Desktop to view the visuals.
