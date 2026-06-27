# 03 — Solution Strategy

| Document Information | |
|----------------------|-----------------------------|
| **Project** | Azure Retail Analytics Platform |
| **Case Study** | Nova Retail Group |
| **Document** | Solution Strategy |
| **Status** | Final |
| **Version** | 1.0 |
| **Author** | Aboudoul Karim OUATTARA |
| **Last Updated** | June 2026 |

---

## Executive Overview

As Nova Retail Group expanded its operations across multiple countries, the volume of transactional data increased rapidly. While this growth created valuable business opportunities, it also exposed significant limitations in the company's existing reporting process.

This document outlines the key business and technical challenges that motivated the implementation of a modern Azure Data Platform.

---

# Existing Challenges

The current reporting process relies on manually prepared datasets extracted from operational systems.

Although functional for small volumes of data, this approach no longer meets the organization's growing analytical needs.

The following challenges were identified.

---

## Challenge 1 — Fragmented Data

Sales transactions are stored as raw CSV files exported from operational systems.

Without a centralized platform, different teams work with separate copies of the data, increasing the risk of inconsistencies and duplicated work.

### Business Impact

* Multiple versions of the same dataset.
* Lack of a single source of truth.
* Difficult collaboration across departments.

---

## Challenge 2 — Poor Data Quality

Raw transactional data contains missing customer identifiers, duplicate records, inconsistent data types, and cancelled transactions.

Without standardized cleansing rules, analytical results become unreliable.

### Business Impact

* Inaccurate KPIs.
* Reduced confidence in reports.
* Additional manual data preparation.

---

## Challenge 3 — Manual Reporting

Business analysts manually clean and transform data before building reports.

As transaction volumes increase, this process becomes increasingly time-consuming and difficult to maintain.

### Business Impact

* Delayed reporting cycles.
* Low productivity.
* High risk of human error.

---

## Challenge 4 — Limited Scalability

The existing reporting workflow was designed for relatively small datasets.

As the company grows, manual processing cannot efficiently support increasing data volumes or additional business domains.

### Business Impact

* Longer processing times.
* Reduced operational efficiency.
* Difficulty supporting future business expansion.

---

## Challenge 5 — Inconsistent Business Metrics

Different business teams calculate KPIs using different methodologies.

For example, revenue, customer counts, or order metrics may vary depending on the report being used.

### Business Impact

* Conflicting dashboards.
* Lack of trust in business metrics.
* Poor decision-making.

---

# Why These Challenges Matter

Reliable analytics depends on three fundamental principles:

* Trusted data.
* Consistent business logic.
* Scalable data processing.

Without these capabilities, business users spend more time preparing data than analyzing it.

The objective of this project is therefore not simply to automate ETL pipelines, but to establish a modern data platform capable of delivering trusted analytical datasets across the organization.

---

# Key Takeaways

The existing reporting process presents several limitations:

* Data is fragmented across multiple files.
* Data quality issues reduce confidence in analytics.
* Reporting depends heavily on manual effort.
* The current workflow does not scale with business growth.
* Business metrics lack consistency across departments.

These challenges justify the implementation of a centralized Azure Data Platform based on the Medallion Architecture.

---

**Next Document →** `03-solution-strategy.md`
