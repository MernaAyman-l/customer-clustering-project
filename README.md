# Customer Segmentation Project

An end-to-end machine learning project that segments mall customers using **K-Means** and **DBSCAN** clustering algorithms based on **Annual Income (k$)** and **Spending Score (1–100)**, and generates actionable marketing insights per customer segment.

---

## Project Overview

Understanding customer buying behavior helps businesses tailor promotions, loyalty programs, and product recommendations. In this project:
- Exploratory Data Analysis (EDA) is performed on `Mall_Customers.csv` (`200` rows, `5` columns, no missing values).
- Features (`Annual Income (k$)` and `Spending Score (1-100)`) are standardized using `StandardScaler`.
- The optimal number of clusters (`k = 5`) is evaluated using the **Elbow Method (WCSS)** and **Silhouette Score** across `k = 2` to `10`.
- **K-Means (`k = 5`, `init='k-means++'`, `random_state=42`)** is applied and visualized on both scaled and original feature scales.
- **DBSCAN (`eps=0.5`, `min_samples=5`)** is tested as a density-based comparison and outlier detector.
- Final segment labels are exported to `customer_segmentation_results.csv`.

---

## Repository Structure

```text
├── Task2 Customer Segmentation.ipynb   # Main analysis, modeling, and visualization notebook
├── Mall_Customers.csv                  # Input dataset (200 customers)
├── customer_segmentation_results.csv   # Output dataset with Cluster and DBSCAN_Cluster labels
└── README.md                           # Project documentation
```

---

## Dataset Summary (`Mall_Customers.csv`)

| Column | Description | Data Type |
| :--- | :--- | :--- |
| `CustomerID` | Unique identifier for each customer | `int64` |
| `Gender` | Customer gender (`Male` / `Female`) | `object` |
| `Age` | Customer age in years | `int64` |
| `Annual Income (k$)` | Annual income in thousands of dollars | `int64` |
| `Spending Score (1-100)` | Score assigned based on spending behavior and purchasing data | `int64` |

---

## K-Means Clustering Results (`k = 5`)

| Cluster | Count | Avg. Age | Avg. Income (k$) | Avg. Spending Score | Segment Profile |
| :---: | :---: | :---: | :---: | :---: | :--- |
| **0** | 81 | 42.72 | 55.30 | 49.52 | Average Income, Moderate Spending (Core / Volume segment) |
| **1** | 39 | 32.69 | 86.54 | 82.13 | High Income, High Spending (VIP / High-value target) |
| **2** | 22 | 25.27 | 25.73 | 79.36 | Younger, Low Income, High Spending (Deals & value offers) |
| **3** | 35 | 41.11 | 88.20 | 17.11 | High Income, Low Spending (Upsell & engagement opportunity) |
| **4** | 23 | 45.22 | 26.30 | 20.91 | Low Income, Low Spending (Budget / discount-driven) |

### DBSCAN Comparison (`eps=0.5`, `min_samples=5`)
- **Cluster `0` (157 customers):** Main density cluster (`Avg. Income: 52.49k$`, `Avg. Spending Score: 43.10`).
- **Cluster `1` (35 customers):** High-income, high-spending cluster (`Avg. Income: 82.54k$`, `Avg. Spending Score: 82.80`).
- **Cluster `-1` (8 customers):** Noise / outliers (`Avg. Income: 122.75k$`, `Avg. Spending Score: 46.88`).

---

## How to Run

1. **Install dependencies:**
   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn jupyter
   ```

2. **Launch Jupyter Notebook:**
   ```bash
   jupyter notebook "Task2 Customer Segmentation.ipynb"
   ```

3. **Run all cells** to reproduce the plots, cluster profiles, and `customer_segmentation_results.csv`.

---

## Tech Stack

- **Python** (`pandas`, `numpy`)
- **Visualization** (`matplotlib`, `seaborn`)
- **Machine Learning** (`scikit-learn`: `KMeans`, `DBSCAN`, `StandardScaler`, `silhouette_score`)
