# Conceptual Data Model

## Purpose

This document defines the core business entities within the QuickCart platform and the relationships between them. The conceptual model provides a business-centric view of the data without considering physical implementation details such as databases, schemas, or table structures.

---

## Business Context

QuickCart's business revolves around customers purchasing products through an online marketplace.

Each purchase triggers a series of business events including payment processing, inventory updates, shipment creation, and potentially product returns.

These business events form the foundation of the analytical platform.

---

# Core Business Entities

## Customer

Represents an individual or organization that purchases products through the QuickCart platform.

### Business Responsibilities

- Registers an account
- Places orders
- Makes payments
- Requests returns

---

## Product

Represents an item available for purchase.

### Business Responsibilities

- Belongs to a product category
- Has a selling price
- Maintains inventory
- Can be purchased multiple times

---

## Order

Represents a customer's purchase transaction.

### Business Responsibilities

- Contains one or more products
- Is associated with a customer
- Generates payment and shipment events

---

## Payment

Represents the financial transaction associated with an order.

### Business Responsibilities

- Confirms payment for an order
- Records payment status
- Supports multiple payment methods

---

## Inventory

Represents the available stock for each product.

### Business Responsibilities

- Tracks available quantity
- Updates after purchases and restocking
- Supports warehouse operations

---

## Shipment

Represents the delivery process for an order.

### Business Responsibilities

- Tracks shipment lifecycle
- Records delivery status
- Associates logistics information with customer orders

---

## Return

Represents a customer's request to return purchased products.

### Business Responsibilities

- References the original order
- Records return reason
- Supports refund processing

---

# Business Relationships

| Parent Entity | Child Entity | Relationship | Description |
|---------------|-------------|--------------|-------------|
| Customer | Order | One-to-Many | A customer can place multiple orders. |
| Product | Order | Many-to-Many | A product can appear in many orders, and an order can contain multiple products. |
| Order | Payment | One-to-One | Each order has a corresponding payment transaction. |
| Product | Inventory | One-to-One | Each product maintains inventory information. |
| Order | Shipment | One-to-One | Each order results in a shipment. |
| Order | Return | Zero-or-One | An order may or may not be returned. |

---

# Business Process Flow

```text
Customer
    |
    v
Places Order
    |
    v
Processes Payment
    |
    v
Updates Inventory
    |
    v
Creates Shipment
    |
    v
Delivered
    |
    v
(Optional)
Return Request
```

This sequence represents the primary lifecycle of a customer purchase within the QuickCart platform.

---

# Design Decisions

## Business-Driven Modelling

The conceptual model is centered around business processes rather than technical implementation.

### Reason

Understanding business entities before designing storage structures leads to a more maintainable and scalable data platform.

---

## Separation of Business and Technical Design

This document intentionally excludes implementation details such as Delta tables, Medallion layers, schemas, and physical storage.

### Reason

Physical implementation may evolve over time, while business concepts remain relatively stable.

---

# Assumptions

- Every order belongs to exactly one customer.
- Every payment is associated with one order.
- Every shipment is linked to one order.
- Every return references an existing order.
- Inventory is tracked at the product level.

---

# Future Evolution

The conceptual model can be extended to support additional business capabilities, including:

- Suppliers
- Promotions and discounts
- Customer reviews
- Loyalty programs
- Multiple warehouses
- Multi-currency support
- Subscription-based products
