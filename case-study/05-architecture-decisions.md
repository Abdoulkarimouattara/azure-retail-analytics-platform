# 05 — Architecture Decisions

| Document Information |                                 |
| -------------------- | ------------------------------- |
| **Project**          | Azure Retail Analytics Platform |
| **Case Study**       | Nova Retail Group               |
| **Document**         | Architecture Decisions          |
| **Status**           | Final                           |
| **Version**          | 1.0                             |
| **Author**           | Aboudoul Karim OUATTARA         |
| **Last Updated**     | June 2026                       |

---

# Executive Overview

Designing a modern data platform is not simply a matter of selecting cloud services.

Every architectural component should solve a specific business or engineering problem while contributing to a scalable, maintainable, and reliable platform.

This document explains the rationale behind the key architectural decisions made during the design of the Azure Retail Analytics Platform.

---

# Architecture Overview

The solution follows a modern cloud-native architecture based on three fundamental principles:

* Separation of storage and compute.
* Progressive improvement of data quality.
* Delivery of business-ready analytical datasets.

These principles guided every technology selection throughout the project.

---

# Decision 1 — Azure Data Lake Storage Gen2

## Business Need

The organization requires a centralized repository capable of storing raw, cleansed, and curated datasets while supporting future growth.

## Decision

Azure Data Lake Storage Gen2 is used as the central storage layer for the entire platform.

## Why This Choice?

* Establishes a single source of truth.
* Supports virtually unlimited scalability.
* Separates storage from compute resources.
* Integrates natively with Azure analytics services.
* Preserves historical datasets for auditing and reprocessing.

## Trade-off

While introducing an additional storage layer increases architectural complexity, it provides significantly greater flexibility and long-term scalability.

---

# Decision 2 — Medallion Architecture

## Business Need

Raw operational data should not be consumed directly by business users.

## Decision

The platform adopts a Medallion Architecture composed of Bronze, Silver, and Gold layers.

## Why This Choice?

| Layer  | Responsibility                              |
| ------ | ------------------------------------------- |
| Bronze | Preserve raw source data.                   |
| Silver | Cleanse, validate, and enrich data.         |
| Gold   | Deliver business-ready analytical datasets. |

This layered approach:

* Improves traceability.
* Simplifies debugging.
* Separates responsibilities.
* Supports reusable data products.

## Trade-off

Additional processing stages increase implementation effort but significantly improve maintainability and data quality.

---

# Decision 3 — Azure Data Factory

## Business Need

Data ingestion must be reliable, repeatable, and easy to manage.

## Decision

Azure Data Factory orchestrates the ingestion workflow from source files to the Bronze layer.

## Why This Choice?

* Managed orchestration service.
* Native Azure integration.
* Scheduling capabilities.
* Pipeline monitoring.
* Reduced operational overhead.

## Trade-off

Azure Data Factory focuses on orchestration rather than complex transformations, requiring a dedicated processing engine for business logic.

---

# Decision 4 — Azure Databricks & PySpark

## Business Need

Large datasets require scalable processing capable of handling complex transformations efficiently.

## Decision

Business transformations are implemented using Azure Databricks with PySpark.

## Why This Choice?

* Distributed processing engine.
* Excellent scalability.
* Native Spark ecosystem.
* Reusable transformation logic.
* Strong integration with Azure Data Lake.

## Trade-off

Databricks introduces additional operational complexity compared to traditional SQL solutions but provides significantly greater scalability and flexibility.

---

# Decision 5 — Parquet Storage Format

## Business Need

Analytical datasets must support fast query performance while minimizing storage costs.

## Decision

The Silver and Gold layers are stored using the Parquet file format.

## Why This Choice?

* Columnar storage.
* High compression.
* Faster analytical queries.
* Better Spark performance.
* Efficient storage utilization.

## Trade-off

Parquet is optimized for analytics rather than manual editing, making it less convenient for direct inspection than CSV files.

---

# Decision 6 — Power BI

## Business Need

Business users require intuitive access to trusted analytical data.

## Decision

Power BI serves as the presentation layer of the platform.

## Why This Choice?

* Interactive dashboards.
* Executive KPI monitoring.
* Self-service analytics.
* Native Azure integration.
* Rapid business insight delivery.

## Trade-off

Dashboard quality depends entirely on the consistency of upstream data models, making a robust Gold layer essential.

---

# Architecture Principles

The final architecture is built upon the following engineering principles:

| Principle              | Implementation                                                    |
| ---------------------- | ----------------------------------------------------------------- |
| Separation of Concerns | Independent ingestion, storage, processing, and reporting layers. |
| Scalability            | Cloud-native services capable of handling future growth.          |
| Traceability           | Immutable Bronze layer preserving raw data.                       |
| Data Quality           | Progressive cleansing through Silver and Gold layers.             |
| Reusability            | Shared analytical datasets for multiple reporting scenarios.      |
| Maintainability        | Modular components with clearly defined responsibilities.         |

---

# Consultant's Note

The selected Azure services are not presented as the only possible solution.

Alternative technologies could also satisfy the business requirements.

The objective of this architecture is to demonstrate a balanced design that prioritizes simplicity, scalability, maintainability, and business value while remaining aligned with modern Azure Data Engineering best practices.

---

# Key Takeaways

Every technology used in this project was selected to address a specific business or engineering requirement.

The architecture emphasizes:

* Business-driven design.
* Modular cloud-native components.
* Progressive data refinement.
* Scalable analytics.
* Long-term maintainability.

These architectural decisions establish the technical foundation for the implementation described in the next document.

---

**Previous Document ←** `04-business-requirements.md` | **Next Document →** `06-pipeline-walkthrough.md`
