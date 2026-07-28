# Functional Requirements

## Purpose

This document defines the functional capabilities of the **QuickCart Lakehouse Platform**.

---

## Data Ingestion

The platform shall:

- Ingest data from multiple source systems.
- Support CSV and JSON input files.
- Preserve raw data in the Bronze layer without modification.
- Capture ingestion metadata (e.g., load timestamp, source file, batch ID).
- Support incremental data ingestion.

---

## Data Storage

The platform shall:

- Store all datasets as Delta tables.
- Organize data using the Medallion Architecture (Bronze, Silver, Gold).
- Manage data assets using Unity Catalog.

---

## Data Processing

The platform shall:

- Clean and standardize source data.
- Remove duplicate records.
- Handle missing and invalid values.
- Enforce business validation rules.
- Support schema evolution.
- Perform incremental MERGE operations.
- Maintain Slowly Changing Dimensions (Type 2) where applicable.

---

## Data Quality

The platform shall:

- Validate mandatory fields.
- Detect duplicate records.
- Validate acceptable data ranges.
- Enforce referential integrity.
- Validate source schemas.
- Store rejected records in quarantine tables.
- Record data quality metrics for each pipeline execution.

---

## Analytics

The platform shall:

- Produce curated Gold-layer tables.
- Provide business-ready KPIs.
- Support Databricks SQL queries.
- Enable dashboard creation for business users.

---

## Monitoring

The platform shall:

- Log pipeline execution details.
- Capture processing metrics.
- Record errors and exceptions.
- Maintain audit tables for monitoring.

---

## Orchestration

The platform shall:

- Execute pipelines in dependency order.
- Support retry and failure handling.
- Enable scheduled execution using Databricks-native orchestration where supported.
