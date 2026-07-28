# Business Requirements Document (BRD)

## Project Name
**QuickCart Lakehouse Platform**

---

## Overview

QuickCart is a fictional multinational e-commerce company that sells products through its online marketplace. The company generates data from multiple operational systems, including customer management, product catalog, order processing, payments, inventory, logistics, and returns.

The objective of this project is to design and build a modern Lakehouse platform using **Databricks Free Edition** that consolidates these disparate data sources into a trusted analytics platform.

---

## Business Problem

QuickCart currently relies on multiple operational systems that produce isolated datasets. As a result:

- Business reports are inconsistent across departments.
- Data quality issues reduce confidence in analytics.
- Manual reconciliation is required to produce reliable reports.
- Executives lack a single source of truth for business KPIs.

---

## Business Objectives

The platform aims to:

- Centralize enterprise data into a single Lakehouse.
- Improve data quality through standardized validation rules.
- Preserve historical data for auditing and analysis.
- Deliver trusted, business-ready datasets for reporting.
- Support incremental data processing for efficient pipeline execution.

---

## Stakeholders

| Stakeholder | Business Need |
|------------|---------------|
| Executive Leadership | Company-wide KPIs and performance reporting |
| Finance | Revenue, payments, and financial reporting |
| Marketing | Customer insights and product performance |
| Operations | Inventory and order fulfillment |
| Logistics | Shipment tracking and delivery metrics |
| Data Engineering | Reliable, maintainable, and observable data pipelines |

---

## In Scope

- Customer, product, order, payment, inventory, shipment, and return data
- Batch data ingestion
- Medallion Architecture (Bronze, Silver, Gold)
- Data quality validation
- Incremental data processing
- Business-ready analytical data models
- SQL-based reporting and dashboards

---

## Out of Scope

- Machine learning workloads
- Real-time streaming pipelines
- Customer-facing applications
- External cloud services outside Databricks Free Edition

---

## Success Criteria

- Single source of truth for business reporting
- Reliable incremental data pipelines
- Automated data quality validation
- Curated Gold-layer datasets for analytics
- Reproducible, well-documented project suitable for portfolio and interview discussions
