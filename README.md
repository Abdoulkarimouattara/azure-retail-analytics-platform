# 🚀 End-to-End Azure Data Pipeline (E-commerce Analytics)

## 📌 Overview
This project demonstrates the design and implementation of a complete data pipeline on Azure.

The pipeline ingests raw data, processes it through multiple layers (Bronze, Silver, Gold), and produces business-ready datasets for analysis.

---

## 🎯 Business Use Case
A company wants to:
- Monitor sales performance  
- Identify top-selling products
- Analyze revenue trends
- Understand customer behavior

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
Azure Databricks (Data Cleaning & Transformation)
↓
Silver Layer (Cleaned & Enriched Data)
↓
[Next: Gold Layer - Analytics]

---

## ⚙️ Technologies Used

- Azure Data Factory  
- Azure Data Lake Storage (ADLS Gen2)   
- Azure Databricks  
- SQL / PySpark  

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
The `data/` folder contains **sample extracts only** for demonstration purposes.  
Actual data is stored and processed in **Azure Data Lake (Bronze/Silver layers)**.
---


## 📂 Data Architecture

### 🟣 Landing Layer
- Raw data uploaded manually  
- Source: Kaggle (Online Retail Dataset)

### 🟤 Bronze Layer
- Data ingested using Data Factory  
- Stored without transformation 

### ⚪ Silver Layer
- Data cleaned and transformed using Databricks  
- Missing values handled  
- Data types corrected  
- New features created:
  - `line_total` (revenue per line)
  - `is_return` (returns indicator)
  - `year`, `month` (time analysis)

## 🥇 Gold Layer (Business Analytics)

Curated datasets organized by business use case:

### 📊 KPIs
- Total Revenue  
- Total Orders  
- Total Customers  
- Average Order Value  

### 📈 Trends
- Monthly revenue  
- Monthly orders  
- Monthly customers  

### 📦 Products
- Top products by revenue  
- Top products by quantity  

### 👥 Customers
- Top customers by total spending  
- RFM segmentation (Recency, Frequency, Monetary) 

---

## 🔄 Pipeline Workflow

### 1. Data Ingestion
- Dataset uploaded to **Landing zone**
- Azure Data Factory pipeline copies data to **Bronze layer**

### Azure Data Factory Pipeline
![Pipeline](architecture/adf_pipeline.png)

### Bronze Layer Output
![Bronze](architecture/bronze_layer.png)


### 2. Data Transformation (Databricks)
- Data cleaning (null handling, type casting)
- Feature engineering (revenue, returns, time features)
- Output written to **Silver layer in Parquet format**

### 📸 Silver Layer Output
![Silver](architecture/silver_layer.png)


### 3. Data Analytics (Gold)
- Compute KPIs  
- Generate trends  
- Identify top products & customers  
- Perform RFM segmentation  

### 📸 Silver Layer Output
![Silver](architecture/gold_layer.png)

---

## 📊 Key Insights

- Total revenue exceeds **8.3M**, showing strong business performance  
- Clear seasonality with peak sales in **Q4**  
- Revenue driven by both:
  - High-value products  
  - High-volume products  

- Customer base includes:
  - Low-frequency buyers  
  - High-value loyal customers  

- RFM analysis highlights:
  - Customer churn opportunities  
  - High-value segments for retention 

---

## 🧠 What I Learned

- Designing scalable data lake architecture (Bronze → Silver → Gold)  
- Data transformation using PySpark  
- Building business-oriented datasets  
- Performing advanced analytics (KPIs, trends, segmentation)  

---

## 📈 Next Steps

- Build dashboards (Power BI / Tableau)  
- Automate pipeline scheduling  
- Improve customer segmentation (clustering, ML) 

---

## 👨‍💻 Author

Aboudoul Karim
Azure Data Engineer  
