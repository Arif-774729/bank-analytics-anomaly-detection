# Banking Analytics & Anomaly Detection

This project explores customer-level behavioral analytics using Indian banking transaction data. Through structured feature engineering, unsupervised learning, and anomaly detection techniques, we derive meaningful insights into customer segments and suspicious patterns.

---

## Objective

To analyze transaction patterns and customer behaviors in order to:

- Segment users using unsupervised clustering (KMeans)
- Detect anomalies (unusual transactions or outlier customers)
- Derive actionable insights to support decision-making in:
  - Banking risk profiling
  - Fraud detection
  - Customer segmentation

---

## Dataset

- **Source**: Kaggle – Indian Bank Transactions
- **Records**: 1,048,567 transactions
- **Features**: Customer ID, Transaction Amount, Account Balance, Date, Time, Gender, DOB, Location

---

## ⚙️ Key Steps Performed

### 1. Data Cleaning & Parsing

- Fixed inconsistent and future-looking Date of Birth values
- Parsed date and time columns, created unified `TransactionDateTime`
- Extracted temporal components: `year`, `month`, `hour`, `weekday`

### 2. Feature Engineering

- Calculated customer `age` from DOB
- Handled missing values with median/mode imputation
- Created log-transformed versions for skewed financial attributes
- Aggregated transactions per customer to generate features like:
  - `avg_txn_amt`, `max_txn_amt`, `txn_count`
  - `avg_bal`, `min_bal`, `max_bal`
  - `active_hours`, `active_months`, `avg_hour`

### 3. Categorical Encoding

- One-hot encoded gender and customer location
- Retained top 20 locations, grouped the rest as `"Other"`

### 4. Scaling & Transformation

- Applied `StandardScaler` to normalize numerical features
- Log-transformed skewed values to reduce influence of outliers

### 5. Clustering (KMeans + PCA)

- Applied PCA to reduce dimensionality for visualization
- Performed KMeans clustering to segment customers into behavioral clusters
- Interpreted clusters to understand patterns in spending, balance, and transaction activity

### 6. Anomaly Detection (Isolation Forest)

- Used Isolation Forest to flag anomalous customer behavior
- Identified ~885 high-risk users from ~884,000 total customers
- Visualized anomalies in PCA-reduced space

---

##  Final Insights

| Metric                | Normal Users   | Anomalies        |
|------------------------|----------------|------------------|
| Avg Txn Amount         | ₹1,524         | ₹52,683          |
| Total Txn Amount       | ₹1,811         | ₹57,944          |
| Avg Balance            | ₹1.0 Lakh      | ₹1.42 Crore      |
| Transaction Count      | ~1.18          | ~1.14            |
| Active Months          | ~1.5           | ~1.1             |

- Anomalous users transact with significantly higher amounts and maintain very large balances.
- Likely High Net-worth Individuals (HNIs) or potential laundering profiles.
- Clustering revealed segments ranging from low-activity users to heavy financial movers.

---

## Business Use Cases

- **Fraud Detection**: Detect unusual patterns or high-risk behaviors early
- **Customer Segmentation**: Build targeted marketing strategies
- **Risk Profiling**: Identify low vs. high-risk customers for credit and service decisions

---

## Files Included

| File Name            | Description                                    |
|----------------------|------------------------------------------------|
| `project.ipynb`      | Complete Jupyter Notebook with all code steps |


---

## 🛠 Technologies Used

- Python, Pandas, NumPy
- Scikit-learn (PCA, KMeans, Isolation Forest)
- Matplotlib, Seaborn
