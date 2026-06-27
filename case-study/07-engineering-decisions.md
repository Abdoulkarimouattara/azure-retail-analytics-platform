# 🚀 End-to-End Azure Data Pipeline (E-commerce Analytics)

## 📌 Overview
This project showcases the design and implementation of a **scalable end-to-end data pipeline on Microsoft Azure**.

It covers the full lifecycle of data:
- Ingestion  
- Storage  
- Transformation  
- Analytics  

The pipeline follows a **Medallion Architecture (Bronze → Silver → Gold)** to deliver clean, reliable, and business-ready datasets.

---

## 📊 Dashboard Preview

This dashboard provides a high-level overview of sales performance, including revenue trends, KPIs, and customer insights.

[![Dashboard](./architecture/dashboard.png)](./architecture/dashboard.png)

---

## 🎯 Business Use Case
The goal is to enable a company to:
- 📊 Monitor sales performance  
- 📦 Identify top-selling products  
- 📈 Analyze revenue trends over time  
- 👥 Understand customer behavior and segmentation  

---

## 🏗️ Architecture
```
Source (Kaggle Dataset)
↓
Landing Zone (Raw Upload)
↓
Azure Data Factory (Ingestion Pipeline)
↓
Bronze Layer (Raw Data Storage)
↓
Azure Databricks (Data Processing)
↓
Silver Layer (Cleaned Data)
↓
Gold Layer (Business Aggregations)  
↓  
BI Layer (Power BI)
```
---

## ⚙️ Technologies Used

-  **Azure Data Factory** – Data ingestion & orchestration  
- **Azure Data Lake Storage Gen2 (ADLS)** – Scalable storage  
- **Azure Databricks** – Data processing (PySpark)  
- **SQL / PySpark** – Data transformation & analytics  

---

## 📁 Repository Structure
```
project/
│
├── architecture/
│ ├── adf_pipeline.png
│ ├── bronze_layer.png
| ├── silver_layer.png
│ └── gold_layer.png
│
├── data/
│ ├── bronze/ 
│ ├── silver/ 
│ └── gold/ 
│
├── notebooks/
│ ├── 02_bronze_to_silver_data_cleaning
│ └── 03_silver_to_gold_analytics
│
├── README.md
```

### ⚠️ Note:
The `data/` folder contains **sample extracts only**.
All full datasets are processed in **Azure Data Lake (Bronze/Silver layers)**.

---


## 📂 Data Architecture

### 🟣 Landing Layer
- Raw dataset ingestion   
- Source: Kaggle (Online Retail Dataset)  

### 🟤 Bronze Layer
- Raw, unprocessed data  
- Stored as-is for traceability  

### ⚪ Silver Layer
- Cleaned and enriched data  
- Transformations include:
  - Missing values handling  
  - Data type corrections  
  - Feature engineering:
    - `line_total` (revenue per transaction line)  
    - `is_return` (returns flag)  
    - `year`, `month` (time analysis)  

## 🥇 Gold Layer (Business Analytics)

Optimized datasets for decision-making:

### 📊 KPIs
- Total Revenue  
- Total Orders  
- Total Customers  
- Average Order Value (AOV)  

### 📈 Trends
- Monthly revenue  
- Monthly orders  
- Monthly customers  

### 📦 Products
- Top products by revenue  
- Top products by quantity  

### 👥 Customers
- Top customers by spending  
- RFM segmentation (Recency, Frequency, Monetary)  

---

## 🔄 Pipeline Workflow

### 1. Data Ingestion
- Data uploaded to **Landing zone**
- Azure Data Factory pipelines move data to **Bronze layer**

### Azure Data Factory Pipeline
![Pipeline](./architecture/adf_pipeline.png)

### Bronze Layer Output
![Bronze layer](./architecture/bronze_layer.png)


### 2. Data Transformation (Databricks)
- Data cleaning and validation  
- Feature engineering  
- Output stored in **Silver Layer (Parquet format)**  

### 📸 Silver Layer Output
![Silver layer](./architecture/silver_layer.png)


### 3. Data Analytics (Gold)
- KPI computation  
- Trend analysis  
- Product & customer insights  
- RFM segmentation  

### 📸 Silver Layer Output
![Gold layer](./architecture/gold_layer.png)

---

## 📊 Key Insights

- 💰 Total revenue exceeds **8.3M**, indicating strong performance  
- 📈 Clear **seasonality trend** with peak in **Q4**  
- 🛍️ Revenue driven by:
  - High-value products  
  - High-volume transactions  

- 👥 Customer segmentation reveals:
  - Loyal high-value customers  
  - Low-frequency buyers  

- 🎯 RFM analysis helps identify:
  - Retention opportunities  
  - At-risk customers  

---

## 🧠 What I Learned

- Designing **scalable data lake architectures**  
- Building **robust ETL pipelines on Azure**  
- Transforming raw data into **business-ready insights**  
- Applying **analytical techniques (KPIs, trends, segmentation)**  

---

## 🚀 Project Value

This project demonstrates:
- End-to-end data engineering workflow  
- Cloud-based data architecture (Azure)  
- Real-world business analytics use cases  

## 👨‍💻 Author

Aboudoul Karim
Azure Data Engineer  
