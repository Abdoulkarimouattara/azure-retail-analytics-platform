# 07 — Engineering Decisions

| Document Information |                                 |
| -------------------- | ------------------------------- |
| **Project**          | Azure Retail Analytics Platform |
| **Case Study**       | Nova Retail Group               |
| **Document**         | Engineering Decisions           |
| **Status**           | Final                           |
| **Version**          | 1.0                             |
| **Author**           | Aboudoul Karim OUATTARA         |
| **Last Updated**     | June 2026                       |

---

# Executive Overview

Building a successful data platform requires more than selecting the right technologies.

Every implementation decision has consequences on scalability, maintainability, performance, cost, and long-term evolution.

This document explains the key engineering decisions made throughout the project and the reasoning behind each choice.

---

| Decision                   | Primary Goal      | Trade-off                 |
| -------------------------- | ----------------- | ------------------------- |
| Preserve Raw Data          | Traceability      | Additional storage        |
| Centralize Business Logic  | KPI Consistency   | More ETL transformations  |
| Separate Processing Layers | Maintainability   | More pipeline stages      |
| Store Data as Parquet      | Performance       | Less human-readable files |
| Lightweight Power BI       | Simpler reporting | More upstream processing  |

---

# Decision 1 — Preserve Raw Data

## Context

Incoming transactional data may contain inconsistencies, duplicate records, missing values, or cancelled orders.

Cleaning the data immediately after ingestion would permanently modify the original source.

## Decision

Store all incoming data unchanged in the Bronze layer.

## Benefits

* Preserves historical records.
* Enables complete data lineage.
* Supports future reprocessing.
* Simplifies debugging.
* Provides a reliable audit trail.

## Trade-off

Additional storage is required because both raw and processed datasets are retained.

However, storage costs are relatively low compared to the value of preserving historical data.

---

# Decision 2 — Centralize Business Logic

## Context

Business metrics such as revenue calculations are used by multiple reports.

Implementing these calculations independently in Power BI would create duplicated logic and inconsistent KPIs.

## Decision

Implement business rules during the data transformation process.

Examples include:

* `line_total`
* `is_return`
* `year`
* `month`

## Benefits

* Single implementation of business logic.
* Consistent KPI calculations.
* Easier maintenance.
* Reusable analytical datasets.

## Trade-off

Transformation complexity increases slightly, but reporting becomes significantly simpler and more reliable.

---

# Decision 3 — Separate Processing Layers

## Context

Combining ingestion, cleansing, and reporting into a single workflow creates tightly coupled pipelines.

## Decision

Adopt a layered processing model using Bronze, Silver, and Gold.

## Benefits

* Easier debugging.
* Better modularity.
* Independent evolution of each layer.
* Improved maintainability.
* Clear data lineage.

## Trade-off

Additional processing stages increase pipeline complexity while significantly improving long-term maintainability.

---

# Decision 4 — Store Analytical Data as Parquet

## Context

The platform is optimized for analytical workloads rather than transactional processing.

## Decision

Store Silver and Gold datasets in the Parquet format.

## Benefits

* Faster analytical queries.
* Columnar storage.
* Better compression.
* Lower storage costs.
* Improved Spark performance.

## Trade-off

Parquet files are not intended for manual editing but provide substantial performance improvements for analytics.

---

# Decision 5 — Keep Power BI Lightweight

## Context

Complex business logic inside dashboards often leads to duplicated calculations and difficult maintenance.

## Decision

Move transformations upstream into the data platform.

Power BI consumes only curated Gold datasets.

## Benefits

* Faster dashboard development.
* Consistent business metrics.
* Better report performance.
* Simpler semantic model.
* Easier maintenance.

## Trade-off

More processing occurs within the data platform, reducing complexity in the reporting layer.

---

# Engineering Principles Applied

Throughout the project, the following engineering principles guided every implementation decision.

| Principle              | Application                                           |
| ---------------------- | ----------------------------------------------------- |
| Separation of Concerns | Independent storage, processing, and reporting layers |
| Reusability            | Shared analytical datasets across multiple reports    |
| Traceability           | Immutable Bronze layer                                |
| Maintainability        | Modular transformations                               |
| Scalability            | Cloud-native Azure architecture                       |
| Performance            | Parquet storage and Spark processing                  |
| Consistency            | Centralized business logic                            |
| Simplicity             | Clear responsibilities for every layer                |

---

# Consultant's Perspective

The engineering decisions presented in this document intentionally prioritize long-term maintainability over short-term implementation speed.

While several alternative solutions could achieve similar results, the selected approach reflects common architectural patterns used in enterprise cloud data platforms.

The objective is not only to build a working pipeline, but to build a platform that remains understandable, extensible, and reliable as business requirements evolve.

---

# Key Takeaways

The success of a Data Engineering platform depends not only on the technologies selected, but also on the engineering principles that guide implementation.

Throughout this project, every technical decision was evaluated against four questions:

* Does it improve maintainability?
* Does it improve scalability?
* Does it improve data quality?
* Does it improve business value?

These principles provide the foundation for evaluating the production readiness of the platform in the next document.

---

**Previous Document ←** `06-pipeline-walkthrough.md` | **Next Document →** `08-production-readiness.md`
