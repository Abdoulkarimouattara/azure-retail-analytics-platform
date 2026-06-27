# 06 — Pipeline Walkthrough

| Document Information |                                 |
| -------------------- | ------------------------------- |
| **Project**          | Azure Retail Analytics Platform |
| **Case Study**       | Nova Retail Group               |
| **Document**         | Pipeline Walkthrough            |
| **Status**           | Final                           |
| **Version**          | 1.0                             |
| **Author**           | Aboudoul Karim OUATTARA         |
| **Last Updated**     | June 2026                       |

---

# Executive Overview

The Azure Retail Analytics Platform follows a structured data processing workflow designed to progressively transform raw operational data into trusted analytical datasets.

Rather than applying all transformations in a single step, the platform separates ingestion, cleansing, enrichment, and analytics into distinct stages. This layered approach improves traceability, maintainability, and scalability while ensuring that business users interact only with curated, high-quality data.

This document follows the complete lifecycle of the data through each stage of the platform.

---

# End-to-End Pipeline

```text
                Raw Sales Data (CSV)
                         │
                         ▼
              Azure Data Factory
               Data Ingestion Pipeline
                         │
                         ▼
         Azure Data Lake Storage Gen2
                         │
         ┌───────────────┼───────────────┐
         ▼               ▼               ▼
      Bronze          Silver          Gold
    Raw Data      Clean & Enriched   Business Ready
                         │
                         ▼
          Azure Databricks (PySpark)
                         │
                         ▼
                 Power BI Dashboard
```

---

# Step 1 — Data Ingestion

## Objective

Collect raw transactional data from the source system and preserve it without modification.

## Process

The source CSV dataset is uploaded to the Landing Zone.

Azure Data Factory orchestrates the ingestion workflow and transfers the files into the Bronze layer stored in Azure Data Lake Storage Gen2.

No transformations are applied during this stage.

### Technologies

* Azure Data Factory
* Azure Data Lake Storage Gen2

### Output

* Raw transactional data
* Immutable historical records
* Single source of truth

📸 **Azure Data Factory Pipeline**

![ADF Pipeline](../architecture/adf_pipeline.png)

📸 **Bronze Layer**

![Bronze Layer](../architecture/bronze_layer.png)

---

# Step 2 — Data Cleansing & Standardization

## Objective

Improve data quality while preserving business meaning.

## Process

Azure Databricks processes the Bronze dataset using PySpark.

The transformation pipeline performs:

* Missing value handling
* Duplicate removal
* Data type corrections
* Business rule validation
* Feature engineering

New analytical attributes are generated:

* `line_total`
* `year`
* `month`
* `is_return`

The resulting datasets are stored in the Silver layer using the Parquet format.

### Technologies

* Azure Databricks
* PySpark

### Output

* Cleansed datasets
* Standardized schema
* Enriched business attributes
* Optimized Parquet files

📸 **Silver Layer**

![Silver Layer](../architecture/silver_layer.png)

---

# Step 3 — Business Data Modeling

## Objective

Transform cleansed transactional data into reusable business-ready analytical datasets.

## Process

PySpark notebooks aggregate transactional data into curated Gold tables optimized for reporting.

The platform produces several analytical data products, including:

* Business KPIs
* Monthly Revenue Trends
* Product Performance
* Customer Analytics
* Top Customers
* RFM Segmentation

These datasets are designed to be consumed directly by reporting tools without additional transformations.

### Technologies

* Azure Databricks
* PySpark

### Output

* Gold analytical tables
* Standardized KPIs
* Reporting-ready datasets

📸 **Gold Layer**

![Gold Layer](../architecture/gold_layer.png)

---

# Step 4 — Business Intelligence

## Objective

Deliver trusted business insights to decision-makers.

## Process

Power BI connects directly to the curated Gold datasets to create interactive dashboards.

Business users can monitor:

* Revenue performance
* Sales trends
* Customer behavior
* Product performance
* Executive KPIs

The reporting layer consumes only Gold datasets, ensuring consistency and eliminating the need for manual calculations.

### Technologies

* Power BI

### Output

* Interactive dashboards
* Executive KPIs
* Business insights

📸 **Power BI Dashboard**

![Dashboard](../images/dashboard.png)

---

# Pipeline Summary

| Stage          | Primary Responsibility       | Main Technology              |
| -------------- | ---------------------------- | ---------------------------- |
| Data Ingestion | Collect raw operational data | Azure Data Factory           |
| Bronze Layer   | Preserve raw datasets        | Azure Data Lake Storage Gen2 |
| Silver Layer   | Cleanse and enrich data      | Azure Databricks (PySpark)   |
| Gold Layer     | Produce analytical datasets  | Azure Databricks (PySpark)   |
| Reporting      | Deliver business insights    | Power BI                     |

---

# Key Takeaways

The platform follows a structured, layered processing model that separates ingestion, transformation, and analytics.

This architecture provides:

* Reliable and repeatable processing
* Progressive data quality improvement
* Reusable analytical datasets
* Consistent business KPIs
* Scalable cloud-native architecture

By isolating responsibilities across each layer, the platform remains easier to maintain, extend, and evolve as business requirements change.

---

## 📦 Data Journey

A single sales transaction follows the lifecycle below:

1. Generated by the operational sales system.
2. Ingested into Azure Data Lake through Azure Data Factory.
3. Stored unchanged in the Bronze layer.
4. Cleansed and enriched in the Silver layer.
5. Aggregated into business-ready Gold datasets.
6. Exposed to Power BI for business reporting.

This controlled journey ensures that every business metric displayed in Power BI can be traced back to its original source data.

---

**Previous Document ←** `05-architecture-decisions.md` | **Next Document →** `07-engineering-decisions.md`
