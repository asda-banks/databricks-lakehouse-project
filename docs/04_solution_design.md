# Solution Design

## Purpose

This document describes the business processes, operational source systems, and high-level solution design for the QuickCart Lakehouse Platform. It provides the architectural context that drives the implementation of the Medallion Architecture, Delta Lake, and analytical data models.

---

## Business Context

QuickCart is a fictional multinational e-commerce company that sells products through its online marketplace.

The business relies on several operational systems that independently manage customer information, product catalogs, order processing, payments, inventory, logistics, and product returns.

These systems generate data continuously and are considered the authoritative source for their respective business domains.

---

## Business Process

The simplified business workflow is shown below.

```text
Customer Registration
        |
        v
Browse Product Catalog
        |
        v
Place Order
        |
        v
Payment Processing
        |
        v
Inventory Update
        |
        v
Shipment Creation
        |
        v
Order Delivery
        |
        v
Optional Return
```

Each stage produces operational data that will be ingested into the Lakehouse.

---

## Source Systems

| Source System | Business Domain | Dataset | Refresh Frequency |
|--------------|----------------|---------|------------------|
| CRM | Customer Management | Customers | Daily |
| ERP | Product Management | Products | Daily |
| OMS | Order Management | Orders | Hourly (simulated as batch loads) |
| Payment Gateway | Payments | Payments | Hourly |
| Warehouse Management System | Inventory | Inventory | Daily |
| Logistics | Shipping | Shipments | Hourly |
| Customer Service | Returns | Returns | Daily |

---

## Design Decisions

### Multiple Independent Source Systems

Rather than generating a single dataset, each business domain is represented by its own operational system.

**Reason**

This mirrors how enterprise organisations separate business responsibilities and allows the Lakehouse to demonstrate multi-source data integration.

---

### File-Based Data Exchange

Operational systems export CSV or JSON files into the landing zone.

**Reason**

Although production systems often integrate through APIs or messaging platforms, file-based ingestion is a common enterprise integration pattern and is fully supported within Databricks Free Edition.

---

### Synthetic Operational Data

All source data will be generated as part of this project.

The datasets will simulate realistic business operations rather than randomly generated records.

Customer registrations, orders, payments, inventory movements, shipments, and returns will be logically connected through shared business keys.
