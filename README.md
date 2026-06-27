<p align="center">
  <img src="./images/banner.png" alt="Azure Retail Analytics Platform Banner">
</p>

<h1 align="center">🚀 Azure Retail Analytics Platform</h1>

<p align="center">
Designing a scalable cloud-native analytics platform with Microsoft Azure
</p>

<p align="center">
A production-inspired end-to-end Data Engineering case study demonstrating how modern cloud architectures transform raw transactional data into trusted business insights.
</p>

<p align="center">

<a href="#-solution-architecture">Architecture</a> • <a href="#-pipeline-overview">Pipeline</a> • <a href="#-dashboard-preview">Dashboard</a> • <a href="#-technical-case-study">Case Study</a>

</p>

---

# 📖 Executive Summary

Modern organizations generate massive amounts of operational data every day. Without a well-designed data platform, transforming this information into reliable business insights becomes increasingly difficult.

This project presents the design and implementation of a production-inspired Azure Data Engineering platform for a retail analytics scenario. The solution demonstrates how modern cloud services can be combined to build scalable ETL pipelines, improve data quality, and deliver business-ready datasets for analytics.

The platform follows the **Medallion Architecture (Bronze → Silver → Gold)**, leveraging **Azure Data Factory**, **Azure Data Lake Storage Gen2**, **Azure Databricks (PySpark)**, and **Power BI** to create a complete end-to-end analytics solution.

Beyond the implementation itself, this repository documents the engineering decisions, architectural rationale, and production considerations behind the solution, making it a complete technical case study.

---

# 📊 Project at a Glance

| Category          | Details                      |
| ----------------- | ---------------------------- |
| Industry          | Retail & E-commerce          |
| Scenario          | Sales Analytics Platform     |
| Architecture      | Medallion Architecture       |
| Cloud Platform    | Microsoft Azure              |
| Storage           | Azure Data Lake Storage Gen2 |
| Processing        | Azure Databricks (PySpark)   |
| Orchestration     | Azure Data Factory           |
| Visualization     | Power BI                     |
| Storage Format    | Parquet                      |
| Engineering Focus | Cloud Data Engineering       |

---

# ⭐ Key Highlights

* End-to-End Azure Data Engineering Platform
* Medallion Architecture (Bronze → Silver → Gold)
* Automated data ingestion with Azure Data Factory
* Distributed processing using Azure Databricks & PySpark
* Business-ready Gold analytical layer
* Interactive Power BI dashboard
* Production-inspired cloud architecture
* Complete technical case study

---

# 🏗️ Solution Architecture

![Solution Architecture](./architecture/solution_architecture.png)

The solution separates data ingestion, storage, processing, and analytics into independent layers, following the Medallion Architecture to ensure scalability, maintainability, and data quality throughout the data lifecycle.

---
# 💼 Business Context

**Nova Retail Group** is a fast-growing international e-commerce company operating across multiple countries. As sales volumes increased, the organization struggled to transform raw transactional data into reliable business insights.

Business teams relied on manually prepared reports, resulting in inconsistent KPIs, delayed decision-making, and limited visibility into sales performance and customer behavior.

To support future growth, the company decided to modernize its analytics platform by implementing a scalable cloud-native data architecture capable of delivering trusted, business-ready datasets.

> 📖 **Want to learn more?** Explore the complete business scenario in the [Business Context](./case-study/01-business-context.md) document.

---

# ⚙️ Solution Overview

The platform follows a modern **Medallion Architecture**, progressively transforming raw operational data into high-quality analytical datasets.

```text
                    Raw Sales Data
                           │
                           ▼
                Azure Data Factory
                  (Data Ingestion)
                           │
                           ▼
          Azure Data Lake Storage Gen2
                           │
          ┌────────────────┼────────────────┐
          ▼                ▼                ▼
      Bronze           Silver            Gold
     Raw Data      Clean & Enriched   Business Ready
                           │
                           ▼
             Azure Databricks (PySpark)
                           │
                           ▼
                     Power BI Reports
```

### Platform Workflow

| Stage          | Description                                                                                      |
| -------------- | ------------------------------------------------------------------------------------------------ |
| **Ingestion**  | Raw CSV files are ingested using Azure Data Factory.                                             |
| **Storage**    | Data is stored in Azure Data Lake Storage Gen2 following the Medallion Architecture.             |
| **Processing** | Azure Databricks applies data cleansing, validation, and business transformations using PySpark. |
| **Analytics**  | Curated Gold datasets are exposed to Power BI for interactive reporting and KPI analysis.        |

---

# 🔄 Pipeline Overview

The solution is organized into four logical stages, each designed with a single responsibility.

## 🧩 Orchestration Layer

- Data ingestion workflow
- Pipeline execution
- Source-to-Bronze data movement
- Foundation for automated batch processing

📸 **Azure Data Factory Pipeline**

![Azure Data Factory Pipeline](./architecture/adf_pipeline.png)

---

## 🟤 Bronze Layer

* Raw data ingestion
* Immutable storage
* Historical traceability
* Single source of truth

📸 **Bronze Layer**

![Bronze Layer](./architecture/bronze_layer.png)

---

## ⚪ Silver Layer

* Data cleansing
* Duplicate removal
* Missing value handling
* Feature engineering
* Standardized schema

📸 **Silver Layer**

![Silver Layer](./architecture/silver_layer.png)

---

## 🟡 Gold Layer

* Business KPIs
* Revenue Analytics
* Product Analytics
* Customer Analytics
* RFM Segmentation
* Reporting-ready datasets

📸 **Gold Layer**

![Gold Layer](./architecture/gold_layer.png)

---

# 📊 Dashboard Preview

The curated Gold layer is consumed through an interactive **Power BI dashboard**, providing business stakeholders with trusted insights into sales performance.

The dashboard includes:

* 💰 Revenue KPIs
* 📈 Monthly Sales Trends
* 📦 Top Products
* 👥 Customer Analytics
* 🌍 Geographic Performance
* 🎯 Business Metrics

📸 **Power BI Dashboard**

![Dashboard](./images/dashboard.png)

---

## 🎯 Business Outcomes

The platform enables business stakeholders to:

* Monitor sales performance through trusted KPIs.
* Analyze monthly revenue trends.
* Identify high-value customers.
* Discover top-performing products.
* Reduce manual reporting efforts.
* Establish a single source of truth for analytics.
* Support faster, data-driven decision-making.

> 📖 The complete implementation, engineering decisions, and production considerations are documented in the **Technical Case Study** available in the `case-study/` folder.

