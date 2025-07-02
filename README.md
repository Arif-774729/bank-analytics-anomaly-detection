🏦 Banking Analytics & Anomaly Detection
This project explores customer-level behavioral analytics using Indian banking transaction data. Through structured feature engineering, unsupervised learning, and anomaly detection, we derive meaningful insights into customer segments and suspicious patterns.

📌 Objective
To analyze transaction patterns and customer behaviors to:

Segment users using unsupervised clustering

Detect anomalies (outlier transactions or users)

Derive actionable insights to support business decision-making in banking, fraud detection, and customer profiling

📁 Dataset
Source: Kaggle – Indian Bank Transactions

Rows: 1,048,567 transactions

Columns: Customer ID, Transaction Amount, Account Balance, Date, Time, Gender, DOB, Location

⚙️ Key Steps Performed
✅ 1. Data Cleaning & Parsing
Handled incorrect and future-looking DOBs

Parsed date and time columns

Constructed full TransactionDateTime

Extracted components: year, month, hour, weekday

✅ 2. Feature Engineering
Calculated age from DOB

Cleaned missing values with median/mode strategies

Derived log-transformed columns for skewed features

Aggregated transaction data to customer-level features like:

avg_txn_amt, max_txn_amt, txn_count

avg_bal, min_bal, max_bal

active_hours, active_months, avg_hour

✅ 3. Categorical Encoding
One-hot encoded CustGender and CustLocation

Pruned to top 20 locations + grouped others as "Other"

✅ 4. Scaling & Transformation
Applied StandardScaler to normalize numerical features

Log-transformed skewed financial attributes

✅ 5. Clustering (KMeans)
Applied PCA for dimensionality reduction

Clustered customers into behavioral segments

Explored clusters to identify patterns in spending & balance

✅ 6. Anomaly Detection
Used Isolation Forest to detect outliers

Flagged ~885 high-risk users from ~884k total customers

Visualized anomalies in PCA-reduced space

📊 Final Insights
Metric	Normal Users	Anomalies
Avg Txn Amount	₹1,524	₹52,683
Total Txn Amount	₹1,811	₹57,944
Avg Balance	₹1.0 Lakh	₹1.42 Cr
Txn Count	~1.18	~1.14
Active Months	~1.5	~1.1

Anomalous users transact with significantly higher amounts and maintain very large balances.

Likely HNI (High Net-worth Individuals) or potential laundering profiles.

Clusters show segmentation from small casual users to heavy financial movers.

📦 Files
File	Description
project.ipynb	Full notebook with all steps
PCA_2D_plot.png	PCA projection with clusters
anomaly_plot.png	Isolation Forest anomaly visualization

💡 Business Use Cases
📌 Fraud Detection: Flag anomalous customer behavior early

📊 Customer Segmentation: Build targeted marketing and support

🧠 Risk Profiling: Identify high-risk vs. low-risk customers
