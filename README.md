# 🚀 End-to-End Azure Data Pipeline (E-commerce Analytics)

## 📌 Overview
This project demonstrates the design and implementation of a complete data pipeline on Azure.

The goal is to ingest, transform, and analyze e-commerce sales data to generate business insights.

---

## 🎯 Business Use Case
A company wants to:
- Track sales performance
- Identify top-selling products
- Analyze revenue trends

---

## 🏗️ Architecture
Source (Kaggle Dataset)
↓
Landing Zone (Raw Upload)
↓
Azure Data Factory (Ingestion Pipeline)
↓
Bronze Layer (Raw Data Storage)
↓
[Next: Transformation with Databricks]

---

## ⚙️ Technologies Used

- Azure Data Factory  
- Azure Data Lake Storage  
- Azure Databricks (upcoming)  
- SQL / PySpark  

---

## 📂 Data Architecture

### 🟣 Landing Layer
- Raw data uploaded manually  
- Source: Kaggle (Online Retail Dataset)

### 🟤 Bronze Layer
- Data ingested using Data Factory  
- Stored without transformation  

---

## 🔄 Pipeline Workflow

### 1. Data Ingestion
- Dataset uploaded to **Landing zone**
- Azure Data Factory pipeline copies data to **Bronze layer**

---

## 📊 Pipeline Visualization

### Azure Data Factory Pipeline
![Pipeline](./architecture/pipeline.png)

### Bronze Layer Output
![Bronze](./architecture/bronze.png)

---

## 🧠 What I Learned

- Designing data lake architecture (Landing → Bronze)
- Building ingestion pipelines with Azure Data Factory
- Structuring data for scalable processing

---

## 📈 Next Steps

- Data cleaning with Azure Databricks (Silver layer)
- Data transformation and aggregation (Gold layer)
- Business insights generation

---

## 👨‍💻 Author

Aboudoul Karim OUATTARA  
Azure Data Engineer  
